---
title: "Problems getting SMC2662W to work in Hardy Heron 8.04"
date: 2008-08-24
forum: Networking &amp; Wireless
---

### Post by creelbm on 2008-08-24
Greetings.  I'm a fairly low skilled Linux user.  I have set up my machine as dual boot Win2k and Hardy Heron, but run in Ubuntu most of the time.  I can connect to my DSL modem via the ethernet card fine, which is how I'm posting here.  However, I cannot get my SMC2662W USB plug in wireless connector to connect to my wireless network.  I got it from a friend, so I don't have the drivers CD.

An odd item is that when I first booted up the system after installing Ubuntu, I was briefly able to configure the wireless card (WEP encryption and so forth), and was able to "see" othwe wireless networks around, including my own, which was extremely weak at a 15' line of site distance.  However, I wasn't able to connect to the network.  I was briefly able to see the Wireless Networks option on the network icon in the upper right of my top toolbar.  However, a month later, I am unable to see that Wireless Network option, and my system doesn't seem to recognize that I have a card.  This is with and without the ethernet cable plugged into the computer.

I have tried installing ndiswrapper and downloading various Windows drivers that I can see out there for my card, but they are considered invalid when I try to import the files into ndiswrapper.

My system clearly recognizes my ethernet card, but doesn't seem to think the SMC USB wireless controller exists.

Any thoughts on how to get this working, before I go and buy something new?

Here is the results from various diagnostic commands I've seen suggested in the forums:

 lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 3c905C-TX/TX-M [Tornado]
       vendor: 3Com Corporation
       physical id: c
       bus info: pci@0000:02:0c.0
       logical name: eth0
       version: 78
       serial: 00:b0:d0:17:50:0d
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=3c59x ip=192.168.0.3 latency=64 maxlatency=10 mingnt=10 module=3c59x multicast=yes

lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 82850 850 (Tehama) Chipset Host Bridge (MCH) [8086:2530] (rev 02)
00:01.0 PCI bridge [0604]: Intel Corporation 82850 850 (Tehama) Chipset AGP Bridge [8086:2532] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev 02)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801BA ISA Bridge (LPC) [8086:2440] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801BA IDE U100 Controller [8086:244b] (rev 02)
00:1f.2 USB Controller [0c03]: Intel Corporation 82801BA/BAM USB Controller #1 [8086:2442] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801BA/BAM SMBus Controller [8086:2443] (rev 02)
00:1f.4 USB Controller [0c03]: Intel Corporation 82801BA/BAM USB Controller #1 [8086:2444] (rev 02)
01:00.0 VGA compatible controller [0300]: nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro] [10de:002d] (rev 15)
02:0a.0 Multimedia audio controller [0401]: Creative Labs SB Live! EMU10k1 [1102:0002] (rev 07)
02:0a.1 Input device controller [0980]: Creative Labs SB Live! Game Port [1102:7002] (rev 07)
02:0b.0 Communication controller [0780]: Conexant HCF 56k Data/Fax/Voice/Spkp Modem [14f1:1036] (rev 08)
02:0c.0 Ethernet controller [0200]: 3Com Corporation 3c905C-TX/TX-M [Tornado] [10b7:9200] (rev 78)

 uname -m
i686

 dmesg | grep -e iwl -e ipw     gives nothing

---

### Post by creelbm on 2008-08-24
Here's another diagnostic posting:
lsusb
Bus 002 Device 002: ID 0d5c:a001 Belkin 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 046d:c00e Logitech, Inc. M-BJ69 Optical Wheel Mouse
Bus 001 Device 001: ID 0000:0000  


Does my system think my SMC card is the Belkin line?

Just to make sure, I tested the wireless in Windows2k, which works.  I also tried the Windows dual boot ipconfig /release trick, which I expected would have no effect, and did not.

---

### Post by creelbm on 2008-08-25
Anyone's thoughts on this problem?

---

### Post by creelbm on 2008-08-27
bump

---

### Post by creelbm on 2008-09-02
bump

---

### Post by atarisan on 2008-10-16
hah...... welcome to the club of orphanage card.....
I'm too faced the same problem and are still mind-bobbling to solve this. 

fyi, really got frustrated and want to move back to the DARK M$ side. 
without WiFi, I'm just useless.

---

### Post by atarisan on 2008-11-17
hello, some update, on how I got this solve.

I'm using Hardy Heron, I noticed that SMS2662W will not start with ndiswrapper install with wifi radar. 
What I did, uninstall ndiswrapper and wifiradar in synaptic, restart and:guitar: ....

work seamlessly, but only one small issue, is that Wireless Roaming does not seems to work, but wat the heck, just manual configure it. :lolflag:

well good luck to you too.

---

