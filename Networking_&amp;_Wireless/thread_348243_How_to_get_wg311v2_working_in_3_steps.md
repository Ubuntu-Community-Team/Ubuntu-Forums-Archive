---
title: "How to get wg311v2 working in 3 steps"
date: 2007-01-28
forum: Networking &amp; Wireless
---

### Post by theoneandonlywheeler on 2007-01-28
Hey

I have seen some people (myself included) who have found that using the wg311v2 has been alot of bother with ndiswrapper.

Well firstly I would like to say that I am a bit of a noob at linux, secondly I will not take any credit for this, it was this guy here:
[http://www.doctort.org/adam/nerd-notes/netgear-wg311v2-wireless-lan-and-ubuntu-dapper.html](http://www.doctort.org/adam/nerd-notes/netgear-wg311v2-wireless-lan-and-ubuntu-dapper.html)
thirdly YOU MUST NOT HAVE UNINSTALLED THE ACX NATIVE DRIVER!

1- Verify you haven't uninstalled the native acx driver when trying ndiswrapper

2- Type to open the file:

> gksudo gedit /etc/modprobe.d/options

3- Add this line at the end:

> options acx firmware_ver=1.2.0.30

4- Reload the driver:

> sudo rmmod acx
sudo modprobe acx firmware_ver=1.2.0.30

5- Setup your card using the networking interface

6- Restart the driver

> sudo ifup wlan0

7 - You should have a working internet card with a native driver 
:guitar:

---

