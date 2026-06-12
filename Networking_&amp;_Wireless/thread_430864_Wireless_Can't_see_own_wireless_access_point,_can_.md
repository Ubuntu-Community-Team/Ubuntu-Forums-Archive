---
title: "Wireless: Can't see own wireless access point, *can* see others of same type"
date: 2007-05-02
forum: Networking &amp; Wireless
---

### Post by cro on 2007-05-02
I've been fiddling with a new install of Ubuntu 7.04 for the past couple of (ok, several) days on a brand new Compaq Presario F500EA laptop, and I'm now at a total dead end when it comes to wireless networking.

I can't see my own wireless access point, but I **can** see those being run by my neighbours.

Nothing I do to my own access point makes it appear, regardless of settings, channel, region, security (or lack thereof). I know the access point works as all three of my laptops connect fine under other OSes, and one of the laptops connects fine using the Feisty BETA install (installed using WUBI) using a netgear card (which was a pain to set up, but works).

Using iwlist scanning shows nearby networks - sometimes. Most often it returns nothing. Network Manager shows a list of nearby networks, but not my own. I've tried every variation I can think of, including the WPA_SUPPLICANT guides, all of which work fine, but none of which ever find my wireless access point, only other people's. All I can seem to find is other people's access points.

And yes, I do *not* have my wired network cable attached whilst searching.

Looking at the other access points nearby I thought it might be related to using WPA, but there are other access points using WPA nearby. I switched my own access point to WEP, but it still wasn't detected. I tried changing channels (from 11 to 6), no joy. I even tried changing the region, but still it refused to appear/was not detected.

It's set to advertise it's existence as well, and - as is evidenced by this post - is working fine, since I'm connected to it under Vista at the moment.

So, as an absolute last resort since I am currently at my wits end and am bereft of further ideas except to poke around and get more frustrated, I thought I'd post this request for help.

Some additional background:
Yes, the driver's running (I can see other APs).
The driver's a Broadcom Dell one (the 43xx).
wpa_supplicant is installed and working.
network-manager is installed and working.
iwlist eth1 scanning *sometimes* returns nearby access points. (wireless is eth1 not wlan0)
wpa-supplicant -w -Dwext etc etc in -dd mode will scan, and sometimes find access points, but not mine.

And the most confusing thing: My wireless access point sometimes sees the MAC address of my wireless card - but my wireless card never sees the wireless access point.

Any pointers, tips, suggestions or assistance would be gratefully received as I really want to move this laptop entirely onto Ubuntu, but without network access I have to keep Vista so i can work (at the moment I can only use Ubuntu when I have my very long network cable plugged in, which is sort of pointless :( ).

---

### Post by spd106 on 2007-05-03
If you're not having any luck with the bcm43xx driver then it's probably worth trying ndiswrapper instead.

Could you please post the version of the card you have, lspci will tell you.

---

### Post by cro on 2007-05-03
> **spd106 said:**
> If you're not having any luck with the bcm43xx driver then it's probably worth trying ndiswrapper instead.
Could you please post the version of the card you have, lspci will tell you.

The driver's fine, I can see other network access points without any problem. I just can't see my local one, not even when I'm less than 18 inches away from the aerial. I have tried ndiswrapper, which didn't work at all.

lspci reports the card as "Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 01)"

---

### Post by spd106 on 2007-05-04
All I can think of is a possible error with the router, are there any firmware updates?

I read on the bcm43xx mailing list I few weeks ago that a D-link router wasn't working correctly, but a firmware upgrade sorted it out. That might not be the problem in your case, I'm just saying that it's not unknown.

---

### Post by cro on 2007-05-04
> **spd106 said:**
> All I can think of is a possible error with the router, are there any firmware updates?
I've been considering this. The router is a Netgear DG834G, firmare version 3.01.31. It does seem odd that only this one router is not visible, when others are. However, the router firmware is also the absolute latest version :(

Time to test different versions of Ubuntu and network-manager.

---

### Post by pichulines on 2007-05-04
same to me... try ndiswrapper instead of fwcutter, it worked for 

follow this [guide]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29")

---

### Post by cro on 2007-05-04
> **pichulines said:**
> same to me... try ndiswrapper instead of fwcutter, it worked for 

follow this [guide]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29")

Pichulines, you are a star. I followed the guide (using the 1.43 drivers), and after the reboot stage, wireless came up, I could see the accesspoint and I am now connected wirelessly and posting from within Ubuntu.

---

### Post by jewelry on 2007-05-12
Spam.

---

### Post by regsrv on 2007-05-25
Pichulines truly is a star! [The guide]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29") solved my problem also (although my Ubuntu didn't find ANY wireless networks, neither mine nor my neighbours').

However, when I reboot my computer this time, Ubuntu doesn't detect my wireless network card at all. When I type in the commands

sudo depmod -a
modprobe ndiswrapper

in the terminal, everything works fine again (Network card AND wireless network recognized). My Linux knowledge is about zero.. but I think the commands registered the driver or something. Is there a way to permanently register the driver? It is a bit cumbersome to type in these two commands on every bootup.. how can this be done easier?

Regards

---

### Post by spd106 on 2007-05-25
Keep reading the guide through steps 6, 7 and 8.

---

