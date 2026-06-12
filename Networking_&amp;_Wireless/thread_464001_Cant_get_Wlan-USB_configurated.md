---
title: "Cant get Wlan-USB configurated"
date: 2007-06-04
forum: Networking &amp; Wireless
---

### Post by fitzefitzefatze on 2007-06-04
Since I´m new here first of all: Hi @ all!

I´m also very new to linux, so I hope I´m able to explain my problem well. 

What do I use:
Ubuntu 7.04
USB-Stick: Edimax EW-7318Ug (rt73-chip)
Encryption: WPA (Essid visible)

What did I do:
I installed the stick by following that tutorial:

[http://ubuntuforums.org/showthread.php?p=1642126](http://ubuntuforums.org/showthread.php?p=1642126)

Everything worked fine, but if i try to configure this stick i got several problems:

My /etc/network/interfaces:

```
face rausb0 inet dhcp
wireless-essid My_Router
wireless-channel 6
wireless-mode managed
```

Without those entries the system doesn´t know my stick, but with 

```

iwconfig rausb0 
```

I got the settings with channel 6 but not with my AP.

```
iwpriv rausb0 get_site_survey 
```

gets all APs 

BUT

```
iwlist rausb0 scanning 
```

says: "rausb0 interface doesn´t support scanning".

That´s confusing since I got all APs with iwpriv. 

Every kind of help would be highly apprechiated!

Thanks in advance!

---

### Post by rodica.balasa on 2008-01-18
I managed to make it work using Edimax drivers, only on inconvinence: it is seen as a wired connection by network manager (using gutsy):
[URL="http://www.len.ro/work/tools/old-new-i8000-2"]
http://www.len.ro/work/tools/old-new-i8000-2[/URL]

---

