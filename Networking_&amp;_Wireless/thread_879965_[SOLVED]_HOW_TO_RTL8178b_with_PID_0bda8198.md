---
title: "[SOLVED] HOW TO: RTL8178b with PID 0bda:8198"
date: 2008-08-04
forum: Networking &amp; Wireless
---

### Post by wessie on 2008-08-04
Hi all,

I'm writing this post in case any person is suffering with a problem I struggled with for quite a while.

I have a Realtek onboard wireless card with the RTL8178b chipset. I tried installing NDISWrapper with the win98 driver which seems to be the de facto solution for getting your wireless working.

The difference with my chip and *most* others is that when I issue the lsusb command, my output is

```
Bus 007 Device 002: ID 0bda:8198 Realtek Semiconductor Corp.
```

most others have a PID of 8189 or 8197 etc.

Luckily I managed to find this post on a Russian site:

[http://planeta.rambler.ru/users/crowfish/45208465.html](http://planeta.rambler.ru/users/crowfish/45208465.html)

It shows exactly what needs to be done. If you're lsusb output shows a slightly different reading, it might be worth giving this guys suggestion a go.....it worked for me :-)

---

### Post by darck on 2008-10-08
If lsusb gives:
Bus 007 Device 003: ID 0bda:8198 Realtek Semiconductor Corp.

use driver modified by me (it's basicly modified driver as written in this russian site). All others doesnt work with ID :8198!
Probably module included with kernel 2.6.27 douesnt work with that id too.
[http://rapidshare.com/files/152036377/rtl8187b_linux_driver_modified_for_0bda-8198_darck.zip.html](http://rapidshare.com/files/152036377/rtl8187b_linux_driver_modified_for_0bda-8198_darck.zip.html)

following installation:
./makedrv
sudo nano /etc/rc.local
add to this file: /change/path/to/correct/wlan0up
sudo apt-get install wicd
after restart chenge in wicd settings wireless interface to correct one (usually wlan0 or wlan1, can be checked by iwconfig)

run wicd, press refresh, APs should be detected. Press connect, vuala :)
&#8212;&#8212;&#8212;-
!?!?!!:
-driver compilation ./makedrv requires libraries: linux-headers- (install if gets fatal error)
-this driver probably doesn&#8217;t work with ID other than: 0bda:8198.
OR:
use (in /etc/rc.local) wlan0up in following way:
lsusb gives for example: Bus 007 Device 002: ID 0bda:8198 Realtek Semiconductor Corp., so:
wlan0up force_card=0×8189
-I couldn&#8217;t compile this driver with kernel v. 2.6.27

---

### Post by philandstuff on 2008-10-18
Here are some more solutions on my site:

[http://www.doc.ic.ac.uk/~pgp/personal/logs/r8198-wifi.html](http://www.doc.ic.ac.uk/~pgp/personal/logs/r8198-wifi.html)

The kernel in ubuntu 8.10 (currently development, due for release Real Soon Now) has a rtl8187b driver, but it doesn't work out of the box with 8198 cards. By hacking the kernel module, it's possible to get that running natively, with no need for ndiswrapper.

---

### Post by styrofoam cup on 2008-11-02
its working now

[http://ubuntuforums.org/showthread.php?t=900791](http://ubuntuforums.org/showthread.php?t=900791)

using the compat-wireless drivers and 8.10. check out the link above, about post number 40

---

