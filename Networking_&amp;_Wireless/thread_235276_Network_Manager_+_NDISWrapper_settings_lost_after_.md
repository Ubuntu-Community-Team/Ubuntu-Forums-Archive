---
title: "Network Manager + NDISWrapper settings lost after reboot"
date: 2006-08-12
forum: Networking &amp; Wireless
---

### Post by esauve on 2006-08-12
Using the excellent how-to from compwiz18 (thanks a lot compwiz18!) I was finally able to get my broadcom 4318 to work in WPA mode with Network Manager and NDISWrapper, but for some reasons I have to go through the settings (ESSID, passkey) everytime I reboot my notebook. I'm not talking about entering the keyring after a successful connection on the AP here (I'll deal with that once the settings stick after reboots). TIA

---

### Post by Mighty_Ferguson on 2006-08-18
Bumping this because I'm having the exact same problem. Network-manager won't remember my settings either. I'm using ndiswrapper as well. I also have the keyring password issue, but it sounds like the problem we're having with the wireless settings not being remembered is seperate.  This is a huge hassle for me, and probably the one that's keeping me from using Ubuntu as my main OS.
-Mighty

---

### Post by drascus on 2007-01-06
I am also having the same problem I have tried several things to remedy including saving the settings to modprobe.d once I had everything up and running. I noticed one peculiar thing in the ndiswrapper wrapper the alias was listed as wlan0 but in the network everything lists the same device as eth1. I tried by modifying the files so they would all say wlan0. that kind of just made nothing on boot. but thats what was suggested in one of the ndiswrapper forums. if anyone does figure it out please do a detailed response as no one has figured out the answer to the boot problem anywhere else yet. 
thanks.
~Mike~

---

### Post by ckom on 2007-01-24
I'm having a similar issue.  i'm using Edgy Eft Server.  I finally got Ndiswrapper "working" on my netgear wpn111 usb dongle. when i boot it still says NDISwrapper not fully implemented (yet), but that's another issue.

The problem is.  When i reboot, the wireless dongle does not load properly and wlan0 does not exist. So when i do a poweroff and start the computer again I do not get any major errors (just the Ndiswrapper not fully implemented thing) but all of my wlan0 settings are missing. and i have to reconfigure them.

okay... i solved part of the issue

in the terminal

```
sudo pico /etc/network/interfaces
```

then in your wlan0

```
auto wlan0
iface wlan0 inet dhcp
     wireless-essid ESSID
     wireless-key YOURKEY
```

remember if your key is a passphrase you must prefix it with an s: for example

```
s:wirelesskey
```

hope this helps

---

### Post by okidian on 2008-07-22
Having the same problem with Hardy.

Edit:

I achieved to make mine work by adding the line *ndiswrapper* into */etc/modules* file.
you can edit the file with ```
gksudo gedit /etc/modules
```

You probably should need to take a look at this document first.
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#Configuring%20Wireless%20Network%20Settings%20using%20nm-applet%20(GNOME%20front%20end%20for%20Network%20Manager](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#Configuring%20Wireless%20Network%20Settings%20using%20nm-applet%20(GNOME%20front%20end%20for%20Network%20Manager))

---

