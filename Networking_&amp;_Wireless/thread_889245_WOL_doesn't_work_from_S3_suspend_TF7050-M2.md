---
title: "WOL doesn't work from S3 suspend TF7050-M2"
date: 2008-08-13
forum: Networking &amp; Wireless
---

### Post by purdueee on 2008-08-13
I'm having issues getting WOL to work from S3.  S3 works ok, I can resume from the power button, but can't wake via WOL while suspended.

I've tried a number of suggestions found around the internet with no luck.

I have the module r8169 in the MODULES section of /etc/defaults/acpi-support so that it is not unloaded.

I have the jumpers set on the MOBO so that the NIC gets power (obvious from normal WOL after shutdown working).

I have ethtool set to enable wake on "g" both on power up and after resume.

I have enabled everything in /proc/acpi/wakeup without any success.

Any other ideas?

The motherboard is a biostar TF7050-M2 with integrated network card.  Bios is configured to allow WOL.

uname -a reports:
 uname -a
2.6.24-19-generic #1 SMP Fri Jul 11 21:01:46 UTC 2008 x86_64 GNU/Linux

lspci reports (ethernet only):
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)

/proc/acpi/wakeup:
Device  S-state   Status   Sysfs node
SLPB      S5    *enabled
HUB0      S5     enabled   pci:0000:00:08.0
XVR0      S5     enabled   pci:0000:00:0b.0
XVR1      S5     enabled   pci:0000:00:0c.0
XVR2      S5     enabled   pci:0000:00:0d.0
XVR3      S5     enabled   pci:0000:00:0e.0
XVR4      S5     enabled   pci:0000:00:0f.0
XVR5      S5     enabled   pci:0000:00:10.0
XVR6      S5     enabled   pci:0000:00:11.0
UAR1      S5     enabled   pnp:00:08
USB0      S3     enabled   pci:0000:00:02.0
USB1      S3     enabled   pci:0000:00:04.0
USBB      S3     enabled   pci:0000:00:04.1
USB2      S3     enabled   pci:0000:00:02.1
AZAD      S5     enabled   pci:0000:00:07.0
MMAC      S5     enabled   


Any ideas?

---

