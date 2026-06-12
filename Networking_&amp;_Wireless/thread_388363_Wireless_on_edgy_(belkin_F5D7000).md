---
title: "Wireless on edgy (belkin F5D7000)"
date: 2007-03-19
forum: Networking &amp; Wireless
---

### Post by simonalexander2005 on 2007-03-19
Hi

my setup is as follows:

_Hardware_

AMD 3200+ 64 processor
Belkin  F5D7000 wireless card (exact version unknown. windows device manager device instance ID says PCI\VEN_1814&DEV_0201&SUBSYS_700A1799&REV_01\4&13699180&0&3848 ).

_Software_

Edgy eft (6.10) amd 64 edition
windows XP home 32 bit edn

_Network_

WPA-PSK TKIP encryption, hex key. channel 11, SSID = Alexanders (this is broadcast), 802.11g router, encryption on.

---------------------

how do I get this configuration to work in linux? thank you for any help you can give!

Simon :)

---

### Post by MontanaMax on 2007-03-19
I'm not going to be able to give you expert advice, but I would suggest turning off the encryption and relying on MAC address filtering only while you get basic connectivity going over the wireless. Once everything is working fine with no encryption, then add that next layer of complexity - or just use MAC address filtering over an unencrypted connected and use SSH tunnels for data security.

Good luck!

---

### Post by simonalexander2005 on 2007-03-19
so how does that work then? I mean - I get rid of the WPA - what next?

---

### Post by cckid on 2007-03-19
Hi Simon,
I had quite a hard time connecting to my WPA router, so I would like to share what I did with you.
Please let me know if this works for you as well!
So, after installing all of the network drivers, I was able to see other wireless networks but could not connect to my own due to:
1 - I do not broadcast my SSID
2 - WPA is enabled and open

So, after hours of fiddling, I was able to connect by typing this in my terminal:
```
sudo iwconfig eth1 essid XXX
sudo iwconfig eth1 key open XXX
sudo iwconfig eth1 channel X
sudo dhclient eth1
```

Notice the "open" in line 2.  Tis was key for me.
Good luck!

---

### Post by doddi on 2007-03-20
I am new to Linux (2 days) and this is the first problem I came accross. I have an F5D7001 card and found the link below extremely useful. Just follow the steps and you should not have any difficulties.

[link]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29")

---

### Post by spd106 on 2007-03-20
I am using an F5D7000 version 1 (BCM4306 rev 3) card right now with WPA-PSK CCMP, so it can be done.

It is important that you find out which chipset it has, some have Ralink, but most are Broadcom. You will find this information in the Device Manager or through running 'lspci' at a terminal.

If you have a Broadcom card then the page suggested by doddi above is very useful.

Another note I might add is that when it comes to WPA, I have found Network Manager to be rather troublesome, so I use wpa_supplicant via the /etc/network/interfaces file. See the forum sticky about WPA for more details.

---

### Post by simonalexander2005 on 2007-03-20
the driver supplier is ralink, so does that mean the chipset is too?

---

### Post by spd106 on 2007-03-21
> **simonalexander2005 said:**
> the driver supplier is ralink, so does that mean the chipset is too?

Yes, you should have a look at this page [https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500)

---

### Post by simonalexander2005 on 2007-03-21
Thank you all ever so much. That last link was the key. I am writing this from linux!!!

Why does that have to be so complicated? windows is just click and go!

ah well

---

