---
title: "Wireless issue"
date: 2009-06-03
forum: New to Ubuntu
---

### Post by AutumnPhoenix on 2009-06-03
Hi,

yesterday I posted that during my upgrade I lost my wireless driver during xubuntu upgrade to 9.04

Curently, I stuck in my old ubuntu disk and am running live and can acess the internet.

Can I somehow 
a) find the appropriate driver
b) copy the appropriate driver
c) get the driver onto my version of xubuntu

all without loosing my data?

---

### Post by stephanvaningen on 2009-06-03
For this you first need to know which chipset you use, type:
```
lspci
```
drop the output on this thread...

---

### Post by AutumnPhoenix on 2009-06-03
Sorry I should of thought of that before

here it is

> 00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03) 
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03) 
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03) 
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03) 
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03) 
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03) 
00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 03) 
00:1c.3 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 (rev 03) 
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03) 
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03) 
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03) 
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03) 
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03) 
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3) 
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03) 
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03) 
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03) 
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751M Gigabit Ethernet PCI Express (rev 11) 
14:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3) 
14:00.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 0 
14:00.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 17) 
14:00.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0 
14:02.0 Ethernet controller: Atheros Communications Inc. AR5212 802.11abg NIC (rev 01) 

---

### Post by AutumnPhoenix on 2009-06-03
bump

---

### Post by AutumnPhoenix on 2009-06-03
bump again

I just need to find a way to load my driver

---

### Post by stephanvaningen on 2009-06-03
According [this]("http://ubuntuguide.org/wiki/Ubuntu:Jaunty#Wireless_Cards") site, Jaunty should recognize your wireless card. As I can read from your PCI info, it's an Atheros AR5212.

anyway, if you really can not activate the card using the option 'Proprietary drivers' (your laptop needs a wired internet connection during this process), then you can still try this option (which also requires a wired internet connection):
```
sudo apt-get install madwifi-tools 
```

---

### Post by stephanvaningen on 2009-06-03
> **AutumnPhoenix said:**
> bump again

I just need to find a way to load my driver

sorry for the delay, I'm working ;-)

---

### Post by AutumnPhoenix on 2009-06-03
no problem, I just want to make sure that this thread dosn't get lost

---

### Post by AutumnPhoenix on 2009-06-03
Ok, I ran madwifi and it states that I have the latest version.  I rebooted and tried again but my wireless still is not responding in any way.

BLAH!

Again, it works if I run my old 7.04 CD.  So its not physically broken.

Could it be that there is some sort of block or forbidden acess if the driver is correct?

---

