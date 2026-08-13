# esphome2sunspec

This project connects to the ESPHome API to make the values available to Victron Cerbo GX over ModbusTCP as a generic Sunspec PV inverter.

This was originally created for a 1-phase Solis inverter. Credits for this go to Menollo: https://github.com/Menollo/esphome2sunspec 

Currently I'm in the works of adapting the code of this esphome2sunspec project to work with a 3-phase Goodwe setup.
I will also reference the ESPhome code on github when done. Since I did not create that code and it not yet on github I'm refering to Tweaker for now: https://gathering.tweakers.net/forum/list_message/85891356#85891356

# ---- Everything below is under development ---#

## Installatie

Zet het project in /srv/esphome2sunspec:

```
cd /srv/
git clone https://github.com/Menollo/esphome2sunspec.git
```

maak een virtual environment:
```
cd /srv/esphome2sunspec/
python -m venv venv
./venv/bin/pip install -r requirements.txt
```

Maak een file .env (in /srv/esphome2sunspec/) met de voor jouw relevante settings:
(Waarbij POWER_CAPABILITY het vermogen van je omvormer is. (1000 is 1kW))

```
ESP_HOST=192.168.0.100
ESP_PORT=6053
ESP_API_PASSWORD=
ESP_API_ENCRYPTION=

MANUFACTURER=Sunspec
MODEL=ESPHome
POWER_CAPABILITY=1000
```

Kopieer de systemd files naar /etc/systemd/system
```
cp /srv/esphome2sunspec/systemd.service /etc/systemd/system/esphome2sunspec.service
cp /srv/esphome2sunspec/systemd.socket /etc/systemd/system/esphome2sunspec.socket
```

start en enable:
```
systemctl enable --now esphome2sunspec.socket
```
