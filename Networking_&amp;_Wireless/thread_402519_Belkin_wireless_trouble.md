---
title: "Belkin wireless trouble"
date: 2007-04-05
forum: Networking &amp; Wireless
---

### Post by Blacktalon on 2007-04-05
Hello everyone,

I had just installed Xubuntu onto my brothers laptop, and he uses a Belkin Wireless G USB Network adapter.  We are on a encrypted network, and I edited the interfaces files according to my own laptop, which works fine.  But the difference is that on my laptop it has an internal wireless card, where my brothers uses an USB wireless Network Adapter.  From what I understand so far is that I need to change the wext(generic) to the correct driver type, but I do not know which one that is, can anyone help me out please.


Thanks,
~BT

---

### Post by Floppyjoe on 2007-04-05
These are the different drivers to use with Wpa Supplicant:
> drivers:
  hostap = Host AP driver (Intersil Prism2/2.5/3)
  madwifi = MADWIFI 802.11 support (Atheros, etc.)
  atmel = ATMEL AT76C5XXx (USB, PCMCIA)
  wext = Linux wireless extensions (generic)
  ndiswrapper = Linux ndiswrapper
  ipw = Intel ipw2100/2200 driver
  wired = wpa_supplicant wired Ethernet driver
  test = wpa_supplicant test driver

You need to determine which driver your card is using for wpa_supplicant and use that and the right interface in the command:
```
 sudo wpa_supplicant -Dwext -iwlan0 -c/etc/wpa_supplicant.conf
```
Enter :
```
lsusb
```
to determine the card type.

---

### Post by Blacktalon on 2007-04-05
Ok, I did a lsusb and got:
Bus 001 Device 006: ID 050d:705a Belkin Components 

And I found out what driver it is:
F5D7050 ( rt2500 ..I think this is it)

---

### Post by spd106 on 2007-04-06
There are a few details on this wiki page for the rt2500 [https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500)

There are also pages for rt73 etc.

---

