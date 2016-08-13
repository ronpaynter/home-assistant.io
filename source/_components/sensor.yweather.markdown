---
layout: page
title: "Yahoo Weather"
description: "Instructions how to integrate Yahoo Weather within Home Assistant."
date: 2016-07-06 9:06
sidebar: true
comments: false
sharing: true
footer: true
logo: yahooweather.png
ha_category: Weather
ha_release: 0.24
---


The `yweather` platform uses [Yahoo Weather](https://www.yahoo.com/news/weather/) as an source for current meteorological data. The `forecast` will show you the condition for 5 days, 0 is the current day. You can use only `weather`, `temp_min`, and `temp_max` with forecast.

<p class='note warning'>
Use of the Yahoo Weather API should not exceed reasonable request volume. Access is limited to 2,000 signed calls per day.
</p>

The `woeid` (Where On Earth ID) for your location, as shown in the example below. You can find your woeid by copying the numeric digits at the end of the URL for your location at [Yahoo Weather](https://www.yahoo.com/news/weather/). If you don't add a woeid it generate it from Home Assistant's latitude and longitude.

To add Yahoo Weather to your installation, add the following to your `configuration.yaml` file:

```yaml
# Example configuration.yaml entry
sensor:
  platform: yweather
  woeid: YOUR_WOEID
  forecast: 0
  monitored_conditions:
   - weather
   - weather_current
   - temp_min
   - temp_max
   - wind_speed
   - pressure
   - visibility
   - humidity
   - temperature

# Example configuration.yaml entry with forecast
sensor:
  platform: yweather
  woeid: YOUR_WOEID
  forecast: 3
  monitored_conditions:
   - weather
   - temp_min
   - temp_max
```

Configuration variables:

- **woeid** (*Optional*): See above.
- **forecast** (*Optional*): Day of forecast. The default is the current day to display conditions.
- **monitored_conditions** array (*Required*): Conditions to display in the frontend.
  - **weather**: A human-readable text summary with picture from yahoo.
  - **weather_current**: A human-readable text summary with picture from yahoo from current conditon.
  - **temperature**: The current temperature.
  - **temp_min**: The minimal temperature of this day.
  - **temp_max**: The maximum temperature of this day.
  - **wind_speed**: The wind speed.
  - **humidity**: The relative humidity.
  - **pressure**: The sea-level air pressure in millibars.
  - **visibility**: The average visibility.


Details about the API are available in the [Yahoo! Developer Network](https://developer.yahoo.com/weather/).

