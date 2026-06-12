---
title: "Belkin F5D7000 (v1000) not working in Xubuntu"
date: 2006-12-02
forum: Networking &amp; Wireless
---

### Post by the music man on 2006-12-02
Hi, I installed Xubuntu 6.10 on my old Pentium 200 system and I have the Belkin F5D7000 v1000 wireless PCI card with Broadcom chipset in it. When I installed Xubuntu, the system first didn't boot at all. I had to remove the card, boot the system, blacklist the BCM46xx driver and then place the card back. (Maybe I could have done that through recovery mode but I didn't know that yet). I have installed ndiswrapper-utils and the ndisgtk graphical frontend. Now, I have copied bcmwl5.inf and bcmwl5.sys from the driver CD to a folder on the system. I installed the bcmwl5.inf file into ndiswrapper through Applications > System > Windows Wireless Drivers, and it says: "Hardware present: Yes". But when I try to set the connection through Applications > System > Network, the device is not listed there. :-|  When I enter iwconfig, it says "lo no wireless extensions.". :(  Did I something wrong? Or maybe do I have to try this without the graphical thing? But I don't know how to do that? :confused:

---

### Post by FrodoB on 2006-12-02
sudo depmod -a

 sudo modprobe ndiswrapper

 sudo ndiswrapper -m

Note that you may get an error message that says:

adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper ...
couldn't add module alias:  at /usr/sbin/ndiswrapper line 717.

You can ignore that. Just cat /etc/modprobe.d/ndiswrapper to 
see that it is there and reboot.


You should be able to see the device using iwconfig then.

---

### Post by the music man on 2006-12-03
> **FrodoB said:**
> sudo depmod -a

 sudo modprobe ndiswrapper

 sudo ndiswrapper -m

Note that you may get an error message that says:

adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper ...
couldn't add module alias:  at /usr/sbin/ndiswrapper line 717.

You can ignore that. Just cat /etc/modprobe.d/ndiswrapper to 
see that it is there and reboot.


You should be able to see the device using iwconfig then.
Hi, thanks for your quick help. When I enter the last command, it says "modprobe config already contains alias directive", and when I cat the file there is "alias wlan0 ndiswrapper", but my card still doesn't show up in iwconfig. What should I do now?

---

### Post by the music man on 2006-12-03
I discovered that the card is gone after reboot. When I enter the commands and then iwconfig without rebooting, my card shows up as "wlan0" there. Should I add the 3 commands to a startup file? Or do I have to do something else?

---

### Post by FrodoB on 2006-12-03
Perhaps just add ndiswrapper to /etc/modules and reboot and see if that gets it.

---

### Post by the music man on 2006-12-03
I solved it. After I did that commands again, I configured my network through Applications>System>Network and enabled the interface. Now it stays working. :D

---

### Post by FrodoB on 2006-12-03
Excellent news. Congratulations.

---

### Post by the music man on 2006-12-11
I now have the same problem, but with my old laptop with the F5D7010 PCMCIA card. When I do:
sudo modprobe ndiswrapper
it prints:
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.17-10-generic/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument

And there's no card in iwconfig. What is this? :confused:

---

### Post by the music man on 2006-12-11
Installed ndiswrapper 1.8 and now it works on the laptop too. :)

---

