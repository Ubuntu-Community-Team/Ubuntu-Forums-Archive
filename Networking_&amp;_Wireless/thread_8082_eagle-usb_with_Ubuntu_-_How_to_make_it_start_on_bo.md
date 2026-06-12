---
title: "eagle-usb with Ubuntu - How to make it start on boot"
date: 2004-12-14
forum: Networking &amp; Wireless
---

### Post by matt-smith on 2004-12-14
Hi,
I have just installed Ubuntu for the first time and I think it may be
the distribution I have been looking for. At present I just have one
small problem. I have to use eagle-usb to connect to the internet using
my Sagem F@st 800 modem. I have installed eagle-usb using the .debs,
when I configured the program it asked me if I want to start the
connection on boot, I answered yes but now each time I boot the computer
I have to issue the following commands as root to synchronise the modem
and start the ADSL connection:

eaglectrl -w
startadsl

I would like to have the internet connection working as soon as the
computer is started. I have previousley used eagle-usb with &#1052;andrake and
didn't have this problem. &#1052;y first thought was to include the above
commands in a startup script but I would expect there would be an easier
way to make this work.
Any Ideas?
Cheers,
Matt.

---

### Post by zenwhen on 2004-12-14
Just add the command to /etc/init.d/bootmisc.sh and call it a day.  :smile:

---

### Post by LazyFool on 2004-12-15
Sorry for this off-topic interposed question, but...

...are you using pppoe or pppoa? 
I'm asking because I experience some strange problems since I've installed the eagle-usb stuff and pppoe.

Greetings from Munich!  :mrgreen:

---

### Post by loCCa518 on 2007-05-15
> **zenwhen said:**
> Just add the command to /etc/init.d/bootmisc.sh and call it a day.  :smile:


[blood pressure solar Mortgages Google Mortgages](http://oldcda.design.ucla.edu/~kpasko/watercolor/css/ph/forced-porn.html)

---

### Post by melkii0083833 on 2007-05-15
> **zenwhen said:**
> Just add the command to /etc/init.d/bootmisc.sh and call it a day.  :smile:


[blood pressure solar Mortgages Google Mortgages](http://oldcda.design.ucla.edu/~kpasko/watercolor/css/ph/forced-porn.html)

---

