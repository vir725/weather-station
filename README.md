![Image of Weather-station](https://github.com/kotamorishi/weather-station/blob/master/sample.jpg?raw=true)

# weather-station
Display online weather info on an SSD1306 OLED display. 
Based on https://ssd1306.readthedocs.io/en/latest/intro.html.
Small usage example in https://ssd1306.readthedocs.io/en/latest/_modules/oled/device.html

# Hardware configuration:
Used OLED display: http://www.banggood.com/0_96-Inch-4Pin-White-IIC-I2C-OLED-Display-Module-12864-LED-For-Arduino-p-958196.html
Wiring: Connect Ground and 3.3V to the display from the Raspberry PI. The connect SCL to SCL pin on the PI and SDA to the SDA pin on the PI.

# Requirement
```
$ sudo apt install python-dev python-pip libfreetype6-dev libjpeg-dev build-essential libopenjp2-7 libtiff5
$ sudo -H pip install --upgrade luma.oled
```

# Gather wether infromation from OpenWetherMap 
This script collect wether information from https://openweathermap.org/api
They are providing Current weather data and 5 day/3 hour forecast. please create your own account to update the API KEY in the download.sh file.

Originally this wether-station collect the information from WetherUnderground, however they are no longer provide free weather API keys.

# Download and prepare to use.
```
git clone https://github.com/kotamorishi/weather-station
```


# Update your API Key and weather ID

Sign up for OpenWeatherMap and generate key from here

https://home.openweathermap.org/api_keys


Once you've got an API Key, copy and paste it in the download.sh
```
API_KEY="TYPE_YOUR_API_KEY_HERE"
WEATHER_ID=6167865
```

# Download font and install it to RaspberryPi
Put the font file(ttf) under this folder.
```
/usr/share/fonts/
```

Personally I am using https://www.dafont.com/8-bit-madness.font and this works great.
Once you put the file, update the font file name in the script.
```
ttf = '/usr/share/fonts/8-Bit Madness.ttf'
```
Or you can put font file wherever and adjust the script.

# Start 
```
python weather.py
```

# Autostart
Set up cron.

crontab -e

```
@reboot /home/pi/weather-station/wrapper.sh
``` 
