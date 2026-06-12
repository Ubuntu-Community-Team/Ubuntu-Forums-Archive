---
title: "Gnome Weather Widget"
date: 2011-01-18
forum: New to Ubuntu
---

### Post by Syndacate on 2011-01-18
Hey,

I'm using 10.10 and I was just wondering with regards to the default weather widget, where it polls its temperature/weather from?

Reason I ask is sometimes it's way off - right now, it's spot on, earlier today (about 4a), it was reading 30*F when it was about 0*F..so where does it get its info from?  (And yes, my location is set right).

Not a very important thing, I was j/w - I was thinking it may have had something to do with a negative value, as I think it was in the negatives last night...but it doesn't appear to be an overflow as it's way too low.

---

### Post by Frogs Hair on 2011-01-18
When I was using the default clock/ weather widget the closest data I could get was from Chicago , 180 miles away . The Weather Report applet on the add to panel menu gets me within 20 miles.

---

### Post by dBuster on 2011-01-18
If you are referring to the screenlets weather widget, ClearWeatherScreenlet, the information comes from weather.com

You need to properly configure the properties to where it polls your local zip code.  When it asks for location put in your zip code and it works like a charm.  I has never been off in its readings for me and this has been for two plus years now.

---

### Post by Syndacate on 2011-01-28
> **Frogs Hair said:**
> When I was using the default clock/ weather widget the closest data I could get was from Chicago , 180 miles away . The Weather Report applet on the add to panel menu gets me within 20 miles.

Well it's entered by zip, so I'm not sure if it "accepted" that or not.

> **dBuster said:**
> If you are referring to the screenlets weather widget, ClearWeatherScreenlet, the information comes from weather.com

You need to properly configure the properties to where it polls your local zip code.  When it asks for location put in your zip code and it works like a charm.  I has never been off in its readings for me and this has been for two plus years now.

I'm not sure what I'm referring to, I don't know what a screenlet is.  It's the standard clock/weather info that comes in the bar with Ubuntu 10.10.

I do have my zip in there, it was just way off.  I'll have to remember to check it again next time it went negative, that's when it seemed to be out of whack.

EDIT:
Except those couple of times when it was negative, it was spot on accurate.

---

### Post by dBuster on 2011-01-29
> **Syndacate said:**
> I'm not sure what I'm referring to, I don't know what a screenlet is.  It's the standard clock/weather info that comes in the bar with Ubuntu 10.10.


This is a photo of my weather screenlet along with the weather on the panel.  This time they are a degree off but the one just changed temperature a few minutes ago and the other one probably has not updated yet.  They update on intervals..

---

### Post by Frogs Hair on 2011-01-29
I have since changed from Weather Report  on the add to panel menu to the Awn weather applet on my dock which also uses Weather.com .

---

### Post by Syndacate on 2011-01-29
Ah, no, it's not a screenlet, then.

More like this:
[https://www.starryhope.com/i/articles/weather.png](https://www.starryhope.com/i/articles/weather.png)

The one actually built into the distro.

I'm not whining about a degree or two, I understand it can only guesstimate for some places, I'm talking like 30* difference a couple of times, but the vast majority of the time it's right on target.

Just one of those things that annoys you, y'know?

I'll have to wait until it's negative again, that's when it happened, I believe.

---

### Post by Frogs Hair on 2011-01-29
> **Syndacate said:**
> Ah, no, it's not a screenlet, then.

More like this:
[https://www.starryhope.com/i/articles/weather.png](https://www.starryhope.com/i/articles/weather.png)

The one actually built into the distro.

I'm not whining about a degree or two, I understand it can only guesstimate for some places, I'm talking like 30* difference a couple of times, but the vast majority of the time it's right on target.

Just one of those things that annoys you, y'know?

I'll have to wait until it's negative again, that's when it happened, I believe.

The one in your link is the one that would only poll information from Chicago , that is why I first switched to Weather Report from the add to panel menu . Then I added the dock applet .

---

### Post by Cheesehead on 2011-01-29
For locations in the United States, the Gnome clock/weather applet pulls data reported by the National Weather Service (and outside the US from similar official weather-reporting organizations). The same US data is available at [http://www.weather.gov](http://www.weather.gov), and from several commandline packages like 'metar'.

The reporting system is very simple, and libgweather really has no way of knowing how old the observations are, so if a station is offline for a few hours the applet will continue to show the last reported readings. Most temporary failures are due to hiccups in the data reporting - the data-reporting systems run 24/7, so occasional short outages are to be expected. Very few failures are due to libgweather or the applets.

---

### Post by Syndacate on 2011-01-30
> **Frogs Hair said:**
> The one in your link is the one that would only poll information from Chicago , that is why I first switched to Weather Report from the add to panel menu . Then I added the dock applet .

That wasn't from my computer, mine's set up with my zip code.  Typically it's correct within a few degrees, but sometimes it was redic off.  Or are you saying it ALWAYS only polls from Chicago?  I'll try adding weather report, although I'd assume it's the same engine as the one "in" the clock - I can see them adding two or more different front ends to the same engine, but 2 or more engines?

> **Cheesehead said:**
> For locations in the United States, the Gnome clock/weather applet pulls data reported by the National Weather Service (and outside the US from similar official weather-reporting organizations). The same US data is available at [http://www.weather.gov](http://www.weather.gov), and from several commandline packages like 'metar'.

The reporting system is very simple, and libgweather really has no way of knowing how old the observations are, so if a station is offline for a few hours the applet will continue to show the last reported readings. Most temporary failures are due to hiccups in the data reporting - the data-reporting systems run 24/7, so occasional short outages are to be expected. Very few failures are due to libgweather or the applets.

Ah, okay, that makes sense, that is probably what happened then, thank you!

---

### Post by Garthhh on 2011-02-02
I don't see any locations close to where I live 95338

---

### Post by iluminameluna on 2011-05-29
> **Syndacate said:**
> I'm not sure what I'm referring to, I don't know what a screenlet is.  It's the standard clock/weather info that comes in the bar with Ubuntu 10.10.

When I upgraded, I chose to keep my desktop configuration from Lucid (10.04LTS) but would like to have a weather widget as I do on my netbook (appeared on it after an update). I just installed Docky but there doesn't seem to be a way to add a weather widget.

I used Synaptic Pkg Mgr to look for weather widgets, applets, desklets .. & got a bunch of files I didn't understand how to use or WHERE to use ..

Also, I now have lost approximately 1/5 of my screen (the bottom 1/5th is black).

Can anyone give me some guidance?

---

