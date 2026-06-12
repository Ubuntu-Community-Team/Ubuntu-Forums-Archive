---
title: "connecting to a network-- not working"
date: 2007-10-14
forum: Networking &amp; Wireless
---

### Post by mike_302 on 2007-10-14
I have a Broadcom wireless card on my laptop. It is recognized by linux, but I can't seem to get the Network manager to connect to the network. The wireless router I'm trying to connect to is a WRT54g v.6 which is connected to two other computers (both XP), all on the same "workgroup". The network's IP address is the common 192.168.1.1 address.   Anyone have any idea waht I'm doing wrong? I go to properties of the Wireless connection in the network manager and I enter the Key properly, the essid as the SSID that hte router has entered on its Wireless page, and set it to dhcp. Waht else am I missing?.. The checkbox is checked in the connections tab in the network manager.

Thanks in advance for your help!

---

### Post by JawsThemeSwimming428 on 2007-10-14
I've found disabling the Network Manager that comes installed in Fiesty is the key. I have had numerous wireless issues with Ubuntu and most of the time when I disable the Network Manager and then manually configure the card and connection it works after a reboot. Worth a shot.

---

### Post by mike_302 on 2007-10-14
Well, I got the WIRED connection to work anyways... Obviously thats not going to be enough seeing as how it is a laptop but... It tells us SOMETHING right? I have all the same settings for my wireless as i do for the wired.

I installed the "Wireless LAN assistant" app, but its telling me i don't have permission to use it... need to use sudo.

See, I'm the only one on this laptop, so I'm obviously admin. why is it that I need to do this Sudo crap ? I dont even know how to use it, and I dont even know a single command on the command line.

---

### Post by Tye on 2007-10-14
Try using WICD

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

---

