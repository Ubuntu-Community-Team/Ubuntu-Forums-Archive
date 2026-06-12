---
title: "Problem to get wireless usb robotics 805422 to work"
date: 2006-08-01
forum: Networking &amp; Wireless
---

### Post by steunzool on 2006-08-01
hey,

I have a wireless usb card.  usb robotics 805422.  
I have installed the drivers with ndiswrapper with:
ndiswrapper -i rsc4usb.inf

when I enter ndiswrapper -l I get:

Installed ndis drivers:
rsc4usb         driver present, hardware present

I have entered the command ndiswrapper -m

but wlan0 does not show up in the list of network devices.

In the beginning eth1 showed up but I disabled that by adding

blacklist islsm_usb
blacklist islsm_device
blacklist islsm

in a file in modprobe.d like I saw in somewhere in a forum

but still wlan0 doesn't appear

I don't know what to do now, can anybody help me?

thanks in advance

---

### Post by phansiizwe on 2006-08-01
Hoi Steunzool,

try this (after ndiswrapper -l):

```

sudo depmod -a
sudo modprobe ndiswrapper
iwlist wlan0 scan

```

First checks for corrctness of dependencies (if I'm right).
Second installs the ndiswrapper module.
Third list the wireless networks in your vicinity (only works if wlan0 is working, though)

---

### Post by steunzool on 2006-08-01
With the last command I get:
wlan0     Interface doesn't support scanning.

---

### Post by phansiizwe on 2006-08-01
Does wlan0 show up when you run

```
ifconfig
```

and does it have an IP address (inet addr)?!


Edit: some smiley appeared where I didn't want it...

---

### Post by poets1977 on 2006-12-23
Hi, 
try to uninstall your actual Ndiswrapper ( also ndiswgtk) and reinstall only ndiswrapper-common and ndiswrapper-utils-1.8 , then load the rsc4usb.inf driver.
blacklist : islsm_usb, islsm_device e islsm.
Shut down (not reboot) your machine and the adpter  will start...i hope.
Bye.

ps:I'm running Edgy.

---

### Post by djRobbieF on 2006-12-23
Yes that will do it.  Edgy comes with an old (and not working) ndiswrapper.  Install 1.8 through apt-get and you'll be golden.

---

### Post by 00Luke on 2007-02-12
I've got this same wireless USB, but I'm running Xubuntu - I'm completely new to the whole linux / ubuntu / xubuntu OS, so any help would be greatly appreciated. How do I get it working in Xubuntu?

Cheers! :)

---

