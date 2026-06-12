---
title: "US Robotics Wireless MAXg PCI Adapter"
date: 2007-05-08
forum: Networking &amp; Wireless
---

### Post by raulu on 2007-05-08
Hi all,

I use the US Robotics Wireless MAXg PCI Adapter to connect to my wireless network at home.
I am completely new with Linux, but would like to hav a go with it. Idownloaded the latest Ubuntu-distribution and start up the LiveCD.  First I want to check if I'm able to connect to the wireless network. 
But no way!

Here is what i get when i run **lspci**:


```
00:09:0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 801.11b/g Wireless LAN Controller (rev 02)
```

It seems the system detects the card correctly.
Here is what i get when i run **iwconfig**:

```
lo   no wireless extensions
eth0 IEEE 802.11b/g ESSID:"" Nickname:"Broadcom 4318"
     Mode: Managed Access Point: Invalid
     RTS thr: off Fragment thr: off 
     Link Quality:0/100 Signal level=-256dBm Noise level=-256dBm
     Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag: 0
     Tx excessive retiries:0 Invalid misc:0 Missed beacon:0
```

This looks less satisfying. When i click on the network-button in the upper right-corner and try to connect to my network, using the networkname and my WEP-key, I can't get a connection.
Can anyone tell me what i'm missing or what i'm doing wrong.

Any help is greatly appreciated.
Regards, Raoul.

---

### Post by chili555 on 2007-05-08
The most likely explanation is that either the ESSID or the WEP key is wrong; for example, Linksys instead of linksys, or using a passphrase 'ilovecoldbeer' instead of the hex key it generated '097c7f299e...etc.'

You can check the ESSID by doing:```
sudo iwlist eth0 scan
```Scan may take a few tries.

To double-check the WEP key may take a trip to the admin pages of the router.

Post back and let us know how you get along.

---

### Post by raulu on 2007-05-15
No success so far.

I've read all kinds of articles considering the Broadcom 4318 chipset on wireless adapters.
It seems I'm not one of those lucky guys, who doesn't own this kind of chipset, but anyway.
Many of those articles are covering Ubuntu 6.10 and not Feisty.
Has anyone been successful configuring this adapter?

Not: I have not installed Feisty yet. I am running Ubuntu with the Live-CD (I think that is the correct term)

Regards, Raoul.

---

### Post by tomiu on 2007-05-16
> **raulu said:**
> No success so far.


Has anyone been successful configuring this adapter?



Regards, Raoul.

i'm searching for that answer for a couple of months(in different forums), and i never found anyone that has configured this adapter to work with ubuntu :(  . 

Regards, tomiu

---

