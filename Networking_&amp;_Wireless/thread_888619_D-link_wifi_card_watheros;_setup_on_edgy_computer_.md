---
title: "D-link wifi card w/atheros; setup on edgy computer w/out internet access"
date: 2008-08-13
forum: Networking &amp; Wireless
---

### Post by teddmeister2 on 2008-08-13
I need to install the ath9k driver on an edgy eft computer (kernel version 2.6.17-12) that currently doesn't have internet access.  I can use a pen drive or burnt cd to transfer over whatever packages I might need, but I don't know where to find a package with that driver for edgy eft.  I know there are packages floating around for  2.6.24, but I assume that probably won't work on 2.6.17.  I'd prefer not to have to try to make the upgrade to a more recent version of ubuntu on her computer.
here is the output of lspci (just to make sure I'm right about the driver--my wireless card is a d-link xtreme-N, DWA-552--and to help you help me in whatever ways that you can):
```
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
01:04.0 Modem: Broadcom Corporation BCM4212 v.90 56k modem (rev 02)
01:05.0 Network controller: Atheros Communications, Inc. Unknown device 0023 (rev 01)
01:09.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
```

I appreciate any help anyone could give, (and if you could help me enable wpa-2 encryption on it as well, I will be ever greatful)

---

### Post by kevmitch on 2008-08-13
could you run 

```
update-pciids
```

and try

```
lspci
```

again?

---

### Post by kevmitch on 2008-08-13
It is highly unlikely that you will ever get ath9k running on 2.6.17. The closest you may get is 2.6.18, and even that's dicey. If lspci shows a card that is only supported by ath9k, your best bet if you don't want to upgrade Ubuntu is to upgrade just the kernel:
[http://www.thinkwiki.org/wiki/How_to_install_the_development_version_of_atk9k](http://www.thinkwiki.org/wiki/How_to_install_the_development_version_of_atk9k)

---

### Post by teddmeister2 on 2008-08-13
Here ya go.  Thanks for helping. :)

```
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
01:04.0 Modem: Broadcom Corporation BCM4212 v.90 56k modem (rev 02)
01:05.0 Network controller: Atheros Communications Inc. AR5416 802.11abgn Wireless PCI Adapter (rev 01)
01:09.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
```

Is that chipset only supported by the ath9k driver?
Does anyone know the earliesr version of ubuntu to have ath9k in the repos?
How much easier does doing a distribution upgrade stand to make this process?

---

### Post by kevmitch on 2008-08-13
Ath9k isn't really in the Ubuntu repos. It is just been posted up by someone who was nice enough to put together a package for it. If you have a mac, you will have to add an other repo. If you don't have a mac you'll have to download the package from the forum page ([http://ubuntuforums.org/showthread.php?t=874097](http://ubuntuforums.org/showthread.php?t=874097)) where it was posted.

In any case, it looks like AR5416 is also supported by madwifi. I'm not sure if its supported by the version in the Ubuntu repos. I'm pretty certain it won't be supported by the edgy eft. Ndiswrapper might work if you've got the XP driver handy or know where to get it.

I just took a look at the repositories and it appears that edgy eft isn't supported any more, so it's actually going to be rather difficult to implement any of these solutions as they all require installing packages.

---

### Post by teddmeister2 on 2008-08-14
Thanks kevmitch.  I decided to just upgrade her to hardy and install it after that.  I'll let you know how it goes.

---

### Post by kevmitch on 2008-08-15
Sure, I'm still watching this thread if you need any help.

---

### Post by karachuonyo on 2008-08-15
I have an Atheros based card AR5413 and this worked OOTB with the restricted drivers. I'm connecting using network manager.My laptop has Kubuntu 8.04.

---

