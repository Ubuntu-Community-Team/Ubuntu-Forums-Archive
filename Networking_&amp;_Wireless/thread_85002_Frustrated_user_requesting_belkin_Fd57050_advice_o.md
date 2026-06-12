---
title: "Frustrated user requesting belkin Fd57050 advice or suggestions"
date: 2005-11-01
forum: Networking &amp; Wireless
---

### Post by cajunaggie on 2005-11-01
I have a Belkin FD7050 wireless USB G adapter. As far as I can tell this is based on the RT2500 chipset. Now, the wiki page tells me the card is supported directly out of the box. When I go to System - Admin - Networking I see a little piece that says "modem" but nothing about my adapter. I clicked it, just in case,  clicked properties and got a big box of stuff I didn't understand. After reading some tutorials on how to install RT2500 chipsets, I am thourough ... thuroly ... thureauly ... I'm friggin confused.

[LIST=1]
[*]If the System>Admin>Network box doesn't show anything about my adapter does that mean it hasen't been installed or detected?
[*]If I need to install it, where do I find the drivers for the FD57050 adapter? Several tutorials use them, but none says where to find them.
[*]If it is installed, am I in the right spot for configuring it?
[/LIST]

I'm gonna keep looking for solutions. I've found plenty of answers, I just don't  understand any of them. ](*,)

---

### Post by bailout on 2005-11-09
just to bump this, I have the same problem with the same device (Belkin 7050 wireless usb pen). Doesn't show up in networking at all.

Any ideas

---

### Post by bailout on 2005-11-10
bump no 2

---

### Post by bailout on 2005-11-11
bumpity bump

---

### Post by nijinsky on 2005-12-07
[QUOTE=bailout]bumpity bump[/QUOTE]

Bumper'd

Me to

---

### Post by carlosqueso on 2005-12-07
I'm not sure I can help, but post the output of:```
lsusb
``` and maybe me or someone else can help.

---

### Post by nijinsky on 2005-12-07
[QUOTE=carlosqueso]I'm not sure I can help, but post the output of:```
lsusb
``` and maybe me or someone else can help.[/QUOTE]

Bus 004 Device 003: ID 050D:7050 Belkin Components
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000


PS I'm on Day one of linux and just installed it.
I am familiar with the command line. Use RISC OS ARM machines years ago.


PPS. Thanks for the quick reply. Very Much Appreciated

All the best
Bob

---

### Post by grinchy on 2005-12-08
Hey i'm having awful problems with this device too.
I have install ndiswrapper and ndiswrapper-utils,
installed the driver with ndiswrapper -i rt73.inf,
but when i do modprobe ndiswrapper it just freezes.
iwconfig reveals no wlan0
also there is no mention of the device in lspci

---

### Post by bailout on 2005-12-08
I have the same adapter and got it working with ndis by following this howto

[http://www.ubuntuforums.org/showthread.php?t=91732&highlight=belkin+usb](http://www.ubuntuforums.org/showthread.php?t=91732&highlight=belkin+usb)

It doesn't seem to work as well as under windows but I am not sure whether that is more the guis, wifi-radar, kwifi, are pretty useless. I also have problems with the hotplug detection during bootup hanging if the adapter is plugged in. 

there is a linux driver available but it looks as if you have to be connected to the internet to use apt before you can install it. Now I have some connectivity I might try the linux driver sometime. For more details see my thread here

[http://www.ubuntuforums.org/showthread.php?t=95309&highlight=belkin+usb](http://www.ubuntuforums.org/showthread.php?t=95309&highlight=belkin+usb)

---

