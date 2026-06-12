---
title: "problem with wireless on a toshiba"
date: 2006-10-01
forum: Networking &amp; Wireless
---

### Post by DCDraco on 2006-10-01
Hey, I need any kind of help the wireless is not working have no idea what the problem might be. Any help that could lead to getting connected would be great. Please help ](*,)

---

### Post by ThaRabbit on 2006-10-02
Could you tell us a little bit more about your laptop / which version of Ubuntu you are using at the moment ? A model indication would help.

Also, could you either check your device manager if the wireless card is detected at all / post the system's reply to these commands:

```
iwconfig wlan0
dmesg
```

A little information:
If your toshiba uses an Atheros chip then fully dunctional linux drivers are available here:
[http://madwifi.org/](http://madwifi.org/)

If another chipset is used then you'll probably be needing ndiswrapper, a tool which loads windows drivers. I am using ndiswrapper at the moment actually :) ndiswrapper modules / packages are available via the apt recources provided by the ubuntu community, howto's are available on this forum / in the FAQ.
[http://ndiswrapper.sourceforge.net/](http://ndiswrapper.sourceforge.net/)

---

