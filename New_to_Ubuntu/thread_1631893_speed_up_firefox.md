---
title: "speed up firefox?"
date: 2010-11-27
forum: New to Ubuntu
---

### Post by DarinB on 2010-11-27
Hi 
I did these tweaks and my firefox pops! any body know if this will kill anything else? Yes I am a tinkerer and love experimenting...
I got it from a techsource website


1. Type about:config into the Firefox URL/address bar and hit ENTER. You will be warned that you might void your warranty if you change some advanced settings, but just go on and trust me :-)

2. Inside the Firefox configuration page, scroll down and look for the following entries:

network.http.pipelining
network.http.proxy.pipelining

Set their values to “true” by double-clicking each one of them.

3. Next up, find this entry:

network.http.pipelining.maxrequests

Double-click and set the value to 8.

4. Right-click anywhere inside the config page and select New --> Integer. Name it nglayout.initialpaint.delay and set the value to “0&#8243;.

5. Right-click anywhere inside the config page and select New --> Integer. Name it content.notify.interval and set the value to “500000&#8243;.

6. Right-click anywhere inside the config page and select New --> Boolean. Name it content.notify.ontimer and set the value to “true&#8243;.

7. Right-click anywhere inside the config page and select New --> Integer. Name it content.switch.threshold and set the value to “250000&#8243;.

8. Right-click anywhere inside the config page and select New --> Boolean. Name it content.interrupt.parsing and set the value to “false&#8243;.

That's about it. You should be able to notice the speed improvement immediately after applying the above tweaks.

Disabling Firefox addons that you don't use often, blocking flash content, and using a lightweight theme will also help speed up Firefox.

---

### Post by I2k4 on 2010-11-27
I'm still running Ubuntu off USB drives on two machines while deciding whether to dual boot.  I've used several of the above tweaks to good effect for some time, but the single biggest improvement in FF from about:config has been to run it in RAM by disabling disk cache:

browser.cache.disk.enable  = False

I also increased the RAM cache to 50MB (on the basis that 1MB = 1024 bits) which may require creating a New/Integer entry - this even works on my first gen netbook:

browser.cache.memory.capacity = 51200

FF with the right tweaks competes with Chrome, with better privacy and better add ons.

---

### Post by lobralleo on 2010-11-27
I have been using the same tweaks myself without noticing any significant issue on several platforms.
However, if you happen to load a lot of tabs together (about 10 or more), you might experience a temporary freeze of Firefox: just let it go for two or three seconds and it will coma back to life.

Some more tweaks here:

[http://www.ubuntugeek.com/speed-up-firefox-web-browser.html](http://www.ubuntugeek.com/speed-up-firefox-web-browser.html)

---

### Post by bwhite82 on 2010-11-27
I can vaguely recall a FF version that was built entirely for speed, can't for the life of me think of the name.

EDIT: [SwiftFox]("http://getswiftfox.com/")

---

### Post by wojox on 2010-11-27
[http://firefox-tutorials.blogspot.com/](http://firefox-tutorials.blogspot.com/)

---

### Post by DarinB on 2011-02-19
New problems after about 2 months of tweaks. my firefox has slowed to a crawl to load up. And a big on this week my ctrl + for zoom usually stays in memory but now every time i open firefox it is impossibly tiny and have to re zoom each time. What happened? can I just restore defaults and go from there?

---

### Post by tuxtout on 2012-03-03
You can create a new launcher and use the command

gnome-terminal -x sudo nice -n -20 sudo -u YOU firefox 

(username at YOU)   

Amazingly fast but less secure.

---

