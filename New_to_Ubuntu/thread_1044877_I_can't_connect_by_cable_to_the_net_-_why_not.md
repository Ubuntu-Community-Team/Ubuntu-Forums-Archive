---
title: "I can't connect by cable to the net - why not?"
date: 2009-01-19
forum: New to Ubuntu
---

### Post by tahitiwibble on 2009-01-19
I have never used a cable to my ADSL modem/router until now. How can I disable my wi-fi and go cable? I've tried to do it in Network Manager" which seems to behave strangely.

---

### Post by Miljet on 2009-01-19
Why do you want to disable the wireless network? Just plug in the cable, click on the network icon, check the wired connection and have fun.

---

### Post by tahitiwibble on 2009-01-19
> **Miljet said:**
> Why do you want to disable the wireless network? Just plug in the cable, click on the network icon, check the wired connection and have fun.

Miljet, I am fed up of the combination of my very problematic 8.04 wireless and a rather pathetic Belkin modem. After 3 weeks of unsuccessfully trying to download 8.10, you would have had enough of this setup also! I did exactly the same as you suggested and it doesn't work.

---

### Post by paydaydaddy on 2009-01-19
Just checking the basics here. Have you tried restarting both the modem and the computer wiht the wired connection in place?

---

### Post by tahitiwibble on 2009-01-19
paydaydaddy, I just did both again and still no joy.

PS My daughters portable with wireless disabled works OK with this same modem.

---

### Post by Miljet on 2009-01-20
It sounds like your ethernet card is not being recognized. I'm no expert in this matter, but if you will open a terminal (Applications -> Accessories -> Terminal) and post the results of
```
 lspci 
```
someone will be able to help.

BTW, I had a similar problem with an older computer a while back. Instead of fighting with the onboard lan connection, I bought a cheap ethernet card and installed it in an empty PCI slot. It worked with no problems.

---

### Post by tahitiwibble on 2009-01-20
Miljet, thanks for the suggestion.

Just in case ;
```

dad@dad-desktop:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.5 PIC: VIA Technologies, Inc. P4M890 I/O APIC Interrupt Controller
00:00.6 Host bridge: VIA Technologies, Inc. P4M890 Security Device
00:00.7 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:02.0 PCI bridge: VIA Technologies, Inc. P4M890 PCI to PCI Bridge Controller
00:03.0 PCI bridge: VIA Technologies, Inc. P4M890 PCI to PCI Bridge Controller
00:0f.0 IDE interface: VIA Technologies, Inc. Unknown device 5337 (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
00:13.0 Host bridge: VIA Technologies, Inc. VT8237A Host Bridge
00:13.1 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCI Bridge
01:00.0 VGA compatible controller: VIA Technologies, Inc. UniChrome Pro IGP [VIA P4M890 Chipset] (rev 01)
80:01.0 Audio device: VIA Technologies, Inc. VIA High Definition Audio Controller (rev 10)
dad@dad-desktop:~$
```

---

