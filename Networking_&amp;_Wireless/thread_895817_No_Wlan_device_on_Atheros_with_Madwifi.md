---
title: "No Wlan device on Atheros with Madwifi"
date: 2008-08-20
forum: Networking &amp; Wireless
---

### Post by Naatan on 2008-08-20
Hi, I have an Atheros wifi card in my HP Pavilion dv6000 series laptop, however Ubuntu does not seem to detect the wireless card properly and thus does not add a wlan connection.

In my dmesg I found the following error:

```
[   35.275539] wifi%d: unable to attach hardware: 'Hardware revision not supported' (HAL status 13)
```

I have my kernel's restricted modules package installed but that doesn't do anything for me..

I've removed madwifi from the installed restricted modules and build it from source myself but without luck.

This is the output of lspci for my wifi card

```
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
```

I have managed to get ndiswrapper working at one time but this stopped working just as quickly without any real reason.

---

### Post by Chris Kupka on 2008-08-20
Hardy sometimes misreads the ar5007eg as ar242x.  On Gutsy it used to read the card as a 5006 or something.  Perhaps try compiling a different version of madwifi from source?

---

