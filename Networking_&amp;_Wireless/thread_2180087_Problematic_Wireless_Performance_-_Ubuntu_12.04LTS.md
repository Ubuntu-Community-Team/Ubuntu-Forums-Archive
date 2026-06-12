---
title: "Problematic Wireless Performance - Ubuntu 12.04LTS, Toshiba Satellite S855"
date: 2013-10-11
forum: Networking &amp; Wireless
---

### Post by mcarley on 2013-10-11
Hello.  I am new to Ubuntu and have been experiencing some "flaky" behavior wireless connection.  I have experienced anywhere from 20 mbps to less than 1 mbps, all from the same location in respect to my wireless router.  I have tried most, if not all, the steps located here [http://itsfoss.com/speed-up-slow-wifi-connection-ubuntu/](http://itsfoss.com/speed-up-slow-wifi-connection-ubuntu/) and other similar sites, but still have the problems.  In addition to this, I have experienced some flaky behavior on YouTube and Vimeo - some videos play, while others do not.  Any suggestions?  Thank you.

---

### Post by varunendra on 2013-10-13
Hello mcarley, and Welcome to the forums !

To let us see your wireless card, its driver and related configuration, please open a terminal (Ctrl-Alt-T) and post back the outputs of -
```
lsb_release -d
uname -mr
lspci -nnk | grep -iA2 net
iwconfig
nm-tool
```

While posting the outputs, please use the '**Code**' box. It preserves its formatting and makes your post cleaner, compact and more readable. Follow the "Using Code Tags" link in my signature to see how.

---

