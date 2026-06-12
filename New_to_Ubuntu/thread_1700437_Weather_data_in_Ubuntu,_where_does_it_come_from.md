---
title: "Weather data in Ubuntu, where does it come from?"
date: 2011-03-05
forum: New to Ubuntu
---

### Post by Ben Page on 2011-03-05
Hey Ubuntuers!

While using Ubuntu's time/date/weather applet I noticed it's more precise than other applets, gadgets, widgets etc. that I use in other OSes. I'm wondering were does the weather data come from? Is it possible to access this data via browser? Or to add it to OS X and Windows 7 via some kind of app, plugin?

---

### Post by Ben Page on 2011-03-05
> **pasha_kazmi said:**
> just looking for a good, cheap sound card (pci) for my system that will work well in linux (specifically,

ROTFL!

Go spam!

---

### Post by tuahaa on 2011-03-05
It comes from specialized weather satellites which then transmit the data to earth.

---

### Post by asmoore82 on 2011-03-05
I may be terribly out of date,

but I believe the old, old Gnome Weather Applet pulled data directly from
the national weather service: [http://www.weather.gov/](http://www.weather.gov/)

Anecdotally, way back when I used to use this applet full time, I would notice
from time to time that the forecast given on the local TV news would match
the text in the applet word for word. I presume this is because they pull
the same data feed from the national weather server and can either run
with it as is or embellish/improvise around it.

---

### Post by Ben Page on 2011-03-05
> **tuahaa said:**
> It comes from specialized weather satellites which then transmit the data to earth.

Priceless, you should make a T-Shirt with this quote ;)

---

### Post by Ben Page on 2011-03-05
> **asmoore82 said:**
> I may be terribly out of date,

but I believe the old, old Gnome Weather Applet pulled data directly from
the national weather service: [http://www.weather.gov/](http://www.weather.gov/)

Anecdotally, way back when I used to use this applet full time, I would notice
from time to time that the forecast given on the local TV news would match
the text in the applet word for word. I presume this is because they pull
the same data feed from the national weather server and can either run
with it as is or embellish/improvise around it.

This might be the case, but I'm not in North America region. I don't see data for any other region on this service. I'm in Europe, in the 3rd world part of it. Weather.com and Weatherbug do provide the data for my region, but they are often wrong, there are local stations that provide data, but they are either slow to update (I get the temps only for 7h, 12h and 19 - 7pm h) or also wrong. The Ubuntu applet is more up to date and precise than the official meteorological station in my region :(.
Sadly, I don't use Ubuntu at work, so it would be nice to get this data there on Mac or Win.

---

### Post by asmoore82 on 2011-03-06
Oh, that is an interesting twist ... I have no idea.

Though I do like [www.wunderground.com](www.wunderground.com)

---

### Post by asmoore82 on 2011-03-06
Wow, I did some investigation with the Wireshark network analyzer.
Even for Serbia, the applet is definitely contacting weather.noaa.gov.

I found this on their site: [http://weather.noaa.gov/weather/YU_cc.html](http://weather.noaa.gov/weather/YU_cc.html)

:KS

---

### Post by Ben Page on 2011-03-08
> **asmoore82 said:**
> Wow, I did some investigation with the Wireshark network analyzer.
Even for Serbia, the applet is definitely contacting weather.noaa.gov.

I found this on their site: [http://weather.noaa.gov/weather/YU_cc.html](http://weather.noaa.gov/weather/YU_cc.html)

:KS


Thnx asmoore82!

---

### Post by aeiah on 2011-03-08
i think a lot of the weather info for outside of the US seems to only be for airports (when you use weather.com or us .gov websites etc). if you dont live too close to one, you may get some pretty innacurate results. 

i have a small bbc weather script i use for conky. probably about as useless for mainland europe as the american ones though. just change the .xml string for where you are

```


#! /usr/bin/python
# -*- coding: utf-8 -*-
# grab a 3 day forcast xml file from bbc and process it for conky

import os, re, time

colour1 = '#434343'
colour2 = '#9C4A2A'

ourxml = 'http://newsrss.bbc.co.uk/weather/forecast/25/Next3DaysRSS.xml'
current = '~/scripts/generated_files/current_weather'



def weather(day, pos):

        dayName = re.findall(r'\w*day\w*', day)
        temp = day[-3:-1].replace(' ','')
        outcome = '${color '+colour1+'}'+day.split(' ')[0]+' ${color '+colour2+'}'+day.split(' ')[-1].replace('\n','')+'°C\n'+day.split(' ',1)[-1].rsplit(' ',1)[0]
        return outcome



cmd = "wget "+ourxml+" -q -O -| sed -n '/<item>/,/<\/item>/p' | grep -m 3 'title' | sed -e 's/<title>//g' -e 's/<\/title>//g' -e 's/&.*//' -e 's/, Max Temp://g' -e 's/://g'"


info = os.popen(cmd)
split = info.readlines()
info.close()

today = weather(split[0],1)+'\n\n'
tomorrow = weather(split[1],2)+'\n\n'
third = weather(split[2],3)

current = os.path.expanduser(current)
f = open(current, "w")

total = (today+tomorrow+third).upper()

f.write(total)

print total

```

---

### Post by donkyhotay on 2011-03-08
> **asmoore82 said:**
> I may be terribly out of date,

but I believe the old, old Gnome Weather Applet pulled data directly from
the national weather service: [http://www.weather.gov/](http://www.weather.gov/)

Anecdotally, way back when I used to use this applet full time, I would notice
from time to time that the forecast given on the local TV news would match
the text in the applet word for word. I presume this is because they pull
the same data feed from the national weather server and can either run
with it as is or embellish/improvise around it.

Yes it is from the national weather service. I have a ham radio that picks up the national weather service broadcasts and the forecast information listed in the ubuntu weather applet is word for word what the national weather service is broadcasting.

---

