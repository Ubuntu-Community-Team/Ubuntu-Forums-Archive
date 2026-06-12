---
title: "WIFI /w Intrepid: PCMCIA Card doesn't show up!"
date: 2008-11-09
forum: Networking &amp; Wireless
---

### Post by pelagic on 2008-11-09
I got a problem with my PCMCI WIFI card. Actually I got 2 problems:

1) And this happend already with 8.04: booting with my WIFI card in the pcmcia slot did not work. booting always got stuck. I found a work around and only inserted the card *after* booting. Not real fun but working.

2) With 8.10 still the same with booting. But now the card doesnt seem to work even if I put it in the slot after booting.

Anyone has an idea how to solve this?

Environment:
Laptop Dell Inspiron 8000 (way old)
500 MB RAM
Kernel 2.6.27-7
WIFI: Zyxel ZyAIR B-100

Output from lspci:
```

00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82815 815 Chipset AGP Bridge (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 02)
00:1f.0 ISA bridge: Intel Corporation 82801BAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801BAM IDE U100 Controller (rev 02)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 Go] (rev b2)
02:03.0 Multimedia audio controller: ESS Technology ES1983S Maestro-3i PCI Audio Accelerator (rev 10)
02:06.0 PCI bridge: Actiontec Electronics Inc Mini-PCI bridge (rev 11)
02:0f.0 CardBus bridge: Texas Instruments PCI4451 PC card Cardbus Controller
02:0f.1 CardBus bridge: Texas Instruments PCI4451 PC card Cardbus Controller
02:0f.2 FireWire (IEEE 1394): Texas Instruments PCI4451 IEEE-1394 Controller
08:04.0 Ethernet controller: Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 (rev 08)
08:08.0 Communication controller: Agere Systems WinModem 56k (rev 01)

```

output from lshw: attached

Any help is appreaciated!
/pelagic

---

### Post by papichulo on 2010-07-05
im having the same problem too but i've already got it to work., i have the same pcmcia wifi card "zykel zyair b-100".

here's what i have done.

```
sudo iwconfig eth(?) essid -- "YOUR WIFI ESSID NAME without quotes"
```

you can check first w/c "eth" is connecting to the wifi., just type:

```
iwconfig
```

btw, im using xubuntu 10.04. :)

---

