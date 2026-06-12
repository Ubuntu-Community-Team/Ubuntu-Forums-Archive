---
title: "Wireless Adapter freezes Ubuntu"
date: 2007-06-06
forum: Networking &amp; Wireless
---

### Post by Cmain on 2007-06-06
First off I have an _Edimax EW-7318Ug USB Wireless Adapter_ which has a _Ralink RT73 (aka RT2571)_ chipset.    

I then installed the 1.0.4 driver for Linux from the Ralink website following the steps in this guide(changing the version number accordingly): [http://ubuntuforums.org/showthread.php?p=1642126](http://ubuntuforums.org/showthread.php?p=1642126)

I wanted to use the card to set up an Ad-Hoc network to share my dial-up connection(ttys0) with a laptop running Windows XP. I followed the guide here after installing the driver to configure ICS: [http://ubuntuforums.org/showthread.php?t=91370](http://ubuntuforums.org/showthread.php?t=91370)

I then did an iwconfig which showed my wireless adapter as rausb0.
Next I tried the following command: 
```
iwconfig rausb0 essid "Ubuntu" mode Ad-Hoc channel auto key open
```

iwconfig then showed everything fine except ESSID was still set to off/any and the network didn't show up on my XP box. I then tried a few variations of my previous command with/out quotes, but still ESSID: off/any.

I then tried the following command:
```
iwconfig rausb0 essid on mode Ad-Hoc channel auto key open
```
A few things showed in terminal and I waited but eventually ctrl-c'd it because it seemed to be monitoring something rather than changing anything. I then tried to do iwconfig again but the command just hung. I tried other commands and they did nothing just blinking cursor. 

I then tried to restart my pc with my USB wireless adapter in and it made it past the Ubuntu progress bar screen but no further. I then tried restarting with my wireless adapter unplugged and it booted successfully. I then tried to plug my wireless adapter in but it greatly slowed Ubuntu down and once again no commands would work.  Unplugging the adapter totally froze Ubuntu.  I'm currently booted without the adapter plugged in and it is working fine.  Any idea as to why this is happening? Help would be greatly appreciated.

---

### Post by rodica.balasa on 2008-01-18
I managed to make it work using Edimax drivers, only on inconvinence: it is seen as a wired connection by network manager (using gutsy):

[http://www.len.ro/work/tools/old-new-i8000-2]("http://www.len.ro/work/tools/old-new-i8000-2")

---

