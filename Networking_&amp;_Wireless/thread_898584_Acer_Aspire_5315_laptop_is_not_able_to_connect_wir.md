---
title: "Acer Aspire 5315 laptop is not able to connect wirelessly, only wired"
date: 2008-08-23
forum: Networking &amp; Wireless
---

### Post by LinuxGuy1234 on 2008-08-23
My laptop (Acer Aspire 5315) can't connect wirelessly. The driver in the kernel is known as "tg3" or "Broadcom Tigon3 support". I've tried these solutions:

1. MadWifi - modprobes fine, but wireless doesn't work
2. acer_acpi - won't work

But I need wireless urgently and being wired is annoying! Help me please!

I'm using Gusty on a Acer Aspire 5315.

---

### Post by hernandez87 on 2008-08-27
This worked for me [http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html]("http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html")
I have an Aspire 5315-2813

---

### Post by LinuxGuy1234 on 2008-11-01
I'm using a Acer Aspire 5315-2153. That link is incorrect.

---

### Post by dantakeoff on 2008-11-20
acer aspire 5315... maybe try ndiswrapper, get it through add/remove, then use it to browse to your windows xp wireless driver, install it with ndiswrapper, and reboot...if you dont have your original xp driver, find it on the net. mine used the atheros driver, and now works hundreds...

---

### Post by LinuxGuy1234 on 2008-11-25
> **dantakeoff said:**
> acer aspire 5315... maybe try ndiswrapper, get it through add/remove, then use it to browse to your windows xp wireless driver, install it with ndiswrapper, and reboot...if you dont have your original xp driver, find it on the net. mine used the atheros driver, and now works hundreds...

It's a Vista driver not supported...

---

### Post by Ayuthia on 2008-11-25
Can you post the results of lspci -nn from the Terminal?  The tg3 driver is for your wired card.

---

### Post by Plumtreed on 2008-11-25
My Aspire 5315 is working well, perhaps you can give more details, such as what Ubuntu version?

---

### Post by LinuxGuy1234 on 2008-11-25
> **Ayuthia said:**
> Can you post the results of lspci -nn from the Terminal?  The tg3 driver is for your wired card.

Wasn't booted into Ubuntu; had another distro; relevant lines:
```
05:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5906 Fast Ethernet PCI Express [14e4:1713] (rev 02)
06:00.0 Ethernet controller [0200]: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter [168c:001c] (rev 01)
```
I use Gutsy and Acer Aspire 5315-2153.

---

### Post by Plumtreed on 2008-11-26
I use Hardy 8.04 but have upgraded NetworkManager to 0.7. This configuration works exceptionally well for me and allows me to connect easily from wired to wireless. I am travelling at the moment and can connect via mobile broadband when WIFI is not freely available.

It can only be described as 'out of the box' it is all so simple.

Perhaps you can upgrade to NetworkManager 0.7 in Gutsy or even go to Hardy and upgrade. Version 8.10, Intrepid, is available and appears to be especially good with networking. Have you considered upgrading?

When I used Gutsy, I used to connect via GnomePPP but this involved manual configuration.

---

### Post by LinuxGuy1234 on 2008-11-26
> **Plumtreed said:**
> I use Hardy 8.04 but have upgraded NetworkManager to 0.7. This configuration works exceptionally well for me and allows me to connect easily from wired to wireless. I am travelling at the moment and can connect via mobile broadband when WIFI is not freely available.

It can only be described as 'out of the box' it is all so simple.

Perhaps you can upgrade to NetworkManager 0.7 in Gutsy or even go to Hardy and upgrade. Version 8.10, Intrepid, is available and appears to be especially good with networking. Have you considered upgrading?

When I used Gutsy, I used to connect via GnomePPP but this involved manual configuration.

Thanks for suggesting 8.10. But ACER actually got a Linux to download called "Linpus", I'm going to try it and if everything falls in hell, I'm trying 8.10.

---

### Post by Plumtreed on 2008-11-26
Suit yourself, but it sounds like the hard way. Are you short of disc space or under rammed? Get 8.04 or 8.10, it is not that hard a thing to do.

On my 5315 I have an 80GB drive and 1GB of Ram and everything works well and is super fast. The only thing that slows us down is the ISP and their connections. 

Everything just works!!!!

---

### Post by LinuxGuy1234 on 2008-11-27
> **Plumtreed said:**
> Suit yourself, but it sounds like the hard way. Are you short of disc space or under rammed? Get 8.04 or 8.10, it is not that hard a thing to do.

On my 5315 I have an 80GB drive and 1GB of Ram and everything works well and is super fast. The only thing that slows us down is the ISP and their connections. 

Everything just works!!!!

I'm not short of disk space (60G last check) and not under rammed (2G RAM).

I'll suit myself.

---

### Post by LinuxGuy1234 on 2008-12-06
I've found the problem! The dmesg shown a lot of _UNDEFINED_ symbols. All we need is a solution! I'm going to write up a wireless module for my wireless chip!

---

