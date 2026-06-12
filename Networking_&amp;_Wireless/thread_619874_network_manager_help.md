---
title: "network manager help"
date: 2007-11-21
forum: Networking &amp; Wireless
---

### Post by mrsudo on 2007-11-21
i have had numerous problems with my wireless usb adapter.  ive been fiddling around with it for a few weeks.  i just succeeded in installing my windows driver through ndiswrapper.  the light on the dongle is on.  i naturally try and use network manager to connect and one or two times ive seen it find my wireless signal but not able to connect.  ive set all my encryption info in as well.  the one thing that bothers me above everything else is that after opening network manager for a minute or two many programs (mainly admin applications)  freeze and wont even start.  is this a problem with network manager?  should i try and use a different manager?

---

### Post by kevdog on 2007-11-21
Probably the best alternative GUI for NWM is WICD -- do not install from synaptic however, rather visit the website and install the latest beta (it is more stable than the stable version -- yes I know it doesnt make sense!!).

Or you could just try connecting directly from the command line (link in my signature).  This is more for troubleshooting rather than an everyday thing.

---

### Post by mrsudo on 2007-11-21
thanks im gonna give that a try.  ill post back with some results.  im dual booting xp where i can actually use my wifi.  once i get this up and running i wont have much use for it.

---

### Post by mrsudo on 2007-11-22
i tried and installed wicd.  i connected to my network . . . . i think.  my light is blinking which means it has connected but i cant use it at all.  and . . . .  wicd stops responding after even clicking on anything once or twice.

---

### Post by kevdog on 2007-11-22
Can you post

lshw -C network


Time to do some debugging!!

---

### Post by mrsudo on 2007-11-22
lshw -C network
you should run this as super user
Network Interfaces

its so hard to use ubuntu at all now.  no programs are running including text editor.  I totally removed NWM. im not sure what the problem could be in the slightest.

---

### Post by mrsudo on 2008-01-27
it turns out the sis163u.inf file is the right one.  
[URL="http://www.sis.com/download/download_step1.php?id=155939"]http://www.sis.com/download/download_step1.php?id=155939
[/URL]

wired my pc and updated.  the installed the newest ndiswrapper and kernel headers.  
then i uninstalled network-manager and installed wicd.  

then edited my /etc/network/interfaces file to look like this:
```
iface lo inet loopback
auto lo

auto wlan0
iface wlan0 inet dhcp
wireless-essid My_Network
wireless-key 1397975370

auto eth0
iface eth0 inet dhcp

```

rebooted and voila.  i am also using a wep encryption.  if you use wpa than you must change accordingly[URL="https://help.ubuntu.com/community/WifiDocs/WPAHowTo"]
https://help.ubuntu.com/community/WifiDocs/WPAHowTo[/URL]

---

