---
title: "Will VERIZON WIRLESS card work with FF 7.04?"
date: 2007-05-14
forum: Networking &amp; Wireless
---

### Post by intricate on 2007-05-14
Can I use my VERIZON PCMCIA wireless network card on my laptop with Ubuntu FF 7.04?  Do I need other software to enable 7.04 to "see" my VERIZON wireless card?

Thanks to your help I am something.

---

### Post by GS2 on 2007-05-14
Post the model number(s) of the wireless card (especially any revision number), it will help to find out what chipset the card uses.

Also put the card in your laptop, start Feisty up, open a terminal and type 
```
lspci 
```- post that output in this thread along with ouput of 
```
lspci -n
```

---

### Post by intricate on 2007-05-17
the model # on my Verizon Broadband access card is PC 5740.

Does that help? Its being used in a 4 year old DELL laptop.

---

### Post by GS2 on 2007-05-21
A little, I would prefer you to post the results of lscpi and lspci -n :)

---

### Post by sikdogg on 2007-05-24
I was going to post the same question as well...

The PC card i have is the V620

Here's the result of LSPCI and LSPCI -n:

wabad@wabadubulaptop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82830 830 Chipset Host Bridge (rev 04)
00:01.0 PCI bridge: Intel Corporation 82830 830 Chipset AGP Bridge (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #1) (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 LY
02:00.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
02:01.0 CardBus bridge: Texas Instruments PCI1420
02:01.1 CardBus bridge: Texas Instruments PCI1420
07:00.0 USB Controller: NEC Corporation USB (rev 43)
07:00.1 USB Controller: NEC Corporation USB (rev 43)
wabad@wabadubulaptop:~$ 
wabad@wabadubulaptop:~$ lspci -n
00:00.0 0600: 8086:3575 (rev 04)
00:01.0 0604: 8086:3576 (rev 04)
00:1d.0 0c03: 8086:2482 (rev 02)
00:1e.0 0604: 8086:2448 (rev 42)
00:1f.0 0601: 8086:248c (rev 02)
00:1f.1 0101: 8086:248a (rev 02)
00:1f.5 0401: 8086:2485 (rev 02)
00:1f.6 0703: 8086:2486 (rev 02)
01:00.0 0300: 1002:4c59
02:00.0 0200: 10b7:9200 (rev 78)
02:01.0 0607: 104c:ac51
02:01.1 0607: 104c:ac51
07:00.0 0c03: 1033:0035 (rev 43)
07:00.1 0c03: 1033:0035 (rev 43)
wabad@wabadubulaptop:~$

I appreciate any help you can give... thnx :)

---

