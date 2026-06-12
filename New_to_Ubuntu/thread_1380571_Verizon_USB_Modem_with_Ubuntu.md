---
title: "Verizon USB Modem with Ubuntu"
date: 2010-01-13
forum: New to Ubuntu
---

### Post by pathfindermwd on 2010-01-13
I am putting this in beginner talk since I am an ubuntu beginner.  

I am trying to figure out how to use a Verizon 760 USB modem in Ubuntu.  I found this answer in a ubuntu forum but it's old and using 9.04.  I am wondering if this applies to 9.10.:

t4thflavor
29th June 2007

In the terminal type

sudo wvdialconf

it will test for a modem, if there are no modems in your box besides your blackberry it should tell you that it found a modem and is using it.

if there are multiple modems you can edit the /etc/wvdial.conf to point to the correct modem(which was identified in the wvdialconf step). I believe it should be /dev/ttyACM0 (that is what my razr shows up as)
Then use whatever dial program you want like gnome-ppp or kppp or whatever. in the settings page you should have a place to put the modem device.

---

