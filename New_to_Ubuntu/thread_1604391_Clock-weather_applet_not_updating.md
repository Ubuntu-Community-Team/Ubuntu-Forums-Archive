---
title: "Clock-weather applet not updating"
date: 2010-10-24
forum: New to Ubuntu
---

### Post by jimmy8910 on 2010-10-24
Hi,

I'm having problems getting appropriate weather updates on the default clock-weather applet.

The problem I have is that the applet updates the exact weather conditions for "Bangalore International Airport" which happens to be about 23kms away from the main city. It does not update for the "Bangalore Airport" which would be an appropriate location to choose. I tried using separate weather applet and it shows that the last update time for "Bangalore Airport" region was on Oct 04. How can i solve this?

---

### Post by rustutzman on 2010-10-24
I don't know for sure what applet you're talking about but have you tried right clicking on it and going into preferences?

---

### Post by jimmy8910 on 2010-10-24
> **rustutzman said:**
> I don't know for sure what applet you're talking about but have you tried right clicking on it and going into preferences?

The one which comes by default in Ubuntu 10.04, "Weather Report".
Its the same as the one available in the clock, but in this i can see the last updated time and also set time intervals for updating the weather in the preferences.

---

### Post by jimmy8910 on 2010-10-24
It updates properly for all other cities other than "Bangalore Airport", it's still showing the last update time to be Oct04 10:30

---

### Post by a8j8i8t8 on 2010-12-13
Hi,
This Ubuntu applet is not updating the weather information for me either.
I added "Pune, India" city by specifying correct co-ordinates.
But still it's not showing correct weather information.
If you see following image, google weather service is showing correct weather information but Ubuntu doesn't.
Ubuntu shows 28 Degrees Celsius whereas Google shows 21 Degrees Celsius which is correct.

[IMG]http://ubuntuone.com/p/TQX/[/IMG]

---

### Post by amjjawad on 2010-12-13
You need to choose one of the close "main" cities to your location. They can't list each and every location in the world, thus, you need to choose a location that's close to you. Try to change the location, even if it's a bit far and see what will happen.

Good luck!

P.S.
For me, my city is already listed so I have no issues and yes, I'm running 10.04 as well.

Oh, I just noticed this thread is an old one!!!!!

---

### Post by gmargo on 2010-12-13
It's not the fault of the weather applet.  The "Bangalore Airport", which has [METAR]("http://en.wikipedia.org/wiki/Metar") code VOBG, has not updated its weather report since January, nearly a year ago.

Here's the link that the applet uses to get the weather report; you can see the date stamp is "2010/01/04 05:00":
[http://weather.noaa.gov/mgetmetar.php?cccc=VOBG](http://weather.noaa.gov/mgetmetar.php?cccc=VOBG)

And here's the link for the "Bangalore International Aiport", with METAR code VOBL; you can see it has a current date:
[http://weather.noaa.gov/mgetmetar.php?cccc=VOBL](http://weather.noaa.gov/mgetmetar.php?cccc=VOBL)

---

