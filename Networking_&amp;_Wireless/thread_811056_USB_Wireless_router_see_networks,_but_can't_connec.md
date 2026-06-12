---
title: "USB Wireless router see networks, but can't connect"
date: 2008-05-28
forum: Networking &amp; Wireless
---

### Post by Iteria on 2008-05-28
I'm using a Belkin f5d6050 to try to connect to our home network. It sees the network, but it doesn't connect. I looked at the vendor site and it seems that the model had had issue connecting to networks with security, but that had been fixed in a driver update. I nabbed a driver from the vendor in hopes of using ndiswrapper to solve my problems, but extracting the files from the .exe file using cabextract and unshield yielded no .inf files I could use. 

Now, I'm at a lost. Everything else on the box works perfectly, I don't want to have to install windows on it just because I can't find a stupid driver.

Doe anyone have any clever ideas?

---

### Post by Iteria on 2008-05-29
Bump

---

### Post by prshah on 2008-05-30
> **Iteria said:**
> 
Doe anyone have any clever ideas?

Theres a very good guide at [http://www.astahost.com/info.php/configuring-belkin-f5d6050-802-11b-usb-wifi-device-mandriva-2007-using-ndiswrapper_t14333.html](http://www.astahost.com/info.php/configuring-belkin-f5d6050-802-11b-usb-wifi-device-mandriva-2007-using-ndiswrapper_t14333.html) that you can follow. 

Note that instead of an INF file, you get a IN_ file, which can be used the same way as the INF file.

If you still can't access the inf and related driver files, PM me your email address and I'll send it across to you. It's about 672Kb so maybe we can even xfer it by instant messenger (I use Yahoo on pidgin).

---

### Post by Iteria on 2008-05-30
I wasn't given a .inf, but I did follow the directions and now my router is recognized, but it doesn't find any networks, which is a step backward from what I had before. here's what I entered into the command line and the response given back to me from the computer:


user@user-desktop:~$ cd /home/user/Desktop/WINXP
user@user-desktop:~/Desktop/WINXP$ sudo ndiswrapper -i bkusb.in_
[sudo] password for user: 
install argument must be .inf file
user@user-desktop:~/Desktop/WINXP$ sudo ndiswrapper -m
adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper ...

************************************************************************
*
* The update-modules command is deprecated and should not be used!
*
************************************************************************

user@user-desktop:~/Desktop/WINXP$ sudo modprobe ndiswrapper
user@user-desktop:~/Desktop/WINXP$ sudo ifdown wlan0
ifdown: interface wlan0 not configured
user@user-desktop:~/Desktop/WINXP$ sudo ifup wlan0
Ignoring unknown interface wlan0=wlan0.
user@user-desktop:~/Desktop/WINXP$ ifup wlan0


I noted at the end that it said that wlan0 isn't configured, but don't remember having to configure anything before on my other linux-based boxes. Though, those had built in wireless cards and that might make a difference,.

---

### Post by prshah on 2008-05-31
> **Iteria said:**
> 
user@user-desktop:~/Desktop/WINXP$ sudo ndiswrapper -i bkusb.in_
install argument must be .inf file


Rename the .in_ file to .inf, then proceed as you have done, starting with "ndiswrapper -i..." command.

All your commands are correct, but since the very first one has failed (must be inf), nothing else will work. After renaming, everything should be fine.

---

### Post by Iteria on 2008-06-01
I renamed everything and I used ndisgtk to install the driver instead of normal commands because I thought it was probably less error prone and I has used it before.

However, Ubuntu thinks that my usb router is a wired internet device instead of a wireless internet device. Any ideas why that would happen?

---

