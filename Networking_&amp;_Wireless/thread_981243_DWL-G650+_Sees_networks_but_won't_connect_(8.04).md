---
title: "DWL-G650+ Sees networks but won't connect (8.04)"
date: 2008-11-13
forum: Networking &amp; Wireless
---

### Post by grayter on 2008-11-13
Hi all,

I'm trying to get a DWL-G650+ PCMCIA wifi card working with my Dell Latitude D630 without luck.  In Ubuntu 8.04 I can see the networks that are around me, and there signal strength but if I try to connect to any of them, it sits doing nothing for a while before giving up.  I've tried with and without encryption which didn't make any difference.

I've also tried the Live CD of 8.10 to see if I had any better luck, but that didn't even pick up the wifi networks that are around me :( Is this just a problem with the LiveCD?

Can anyone point out what I'm doing wrong or need to change?  Here is some of the info which might be useful:

lspci:
```
04:00.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Interface

```

dmesg:
```
[   27.729187] acx: Loaded combined PCI/USB driver, firmware_ver=default
[   27.729191] acx: compiled to use 32bit I/O access. I/O timing issues might occur, such as non-working firmware upload. Report them
[   27.729276] acx: found ACX111-based wireless network card at 0000:04:00.0, irq:18, phymem1:0x8C020000, phymem2:0x8C000000, mem1:0xf8a14000, mem1_size:8192, mem2:0xf8bc0000, mem2_size:131072
[   27.730300] acx: loading firmware for acx1111 chipset with radio ID 16
[   28.028262] acx: === chipset TNETW1130, radio type 0x16 (Radia), form factor 0x01 ((mini-)PCI / CardBus), EEPROM version 0x05: uploaded firmware 'Rev 1.2.1.34' ===
[   28.028529] acx v0.3.36: net device wlan0, driver compiled against wireless extensions 22 and Linux 2.6.24-21-generic
[   28.028569] usbcore: registered new interface driver acx_usb

```

Errors sometimes seen in dmesg:
```
wlan0: tx error 0x20, buf 06!
```

I'd be really grateful if someone can figure out what's wrong as I need the wifi to work when I head out to a conference soon.

Thanks!

---

### Post by grayter on 2008-11-14
Bump...

---

### Post by Zhukov on 2008-11-14
Have you tried upgrading to 8.10?

Best regards!

---

### Post by grayter on 2008-11-14
OK so I've tried upgrading to 8.10 and exactly the same thing happens.  I can see the wireless networks but I can't connect to any of them (even unencrypted ones!).  I gave a suggestion I got at work out (install wicd) and whilst I definitely prefer the GUI, it has the same problem :(

Any more ideas?

---

### Post by Zhukov on 2008-11-16
If you can access and unencripted network try connecting through the terminal:

sudo iwconfig <interface> essid <SSID>
sudo dhclient <interface>

And see what happens.

And on dmesg as well, post it here.

Best regards!

---

