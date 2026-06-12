---
title: "Problem with wlan"
date: 2006-09-20
forum: Networking &amp; Wireless
---

### Post by dmsn on 2006-09-20
Hey.
I installed ubuntu today and it works fine but now this...
I want my wlan card to work, i have a HP NX7400 laptop.
And i googled little and i saw i need ipw2200.
But i cant install it :(

dmsn@arc:~/ipw2200-1.0.3$ make
make -C /lib/modules/2.6.15-27-386/build SUBDIRS=/home/dmsn/ipw2200-1.0.3 MODVERDIR=/home/dmsn/ipw2200-1.0.3 modules
make: *** /lib/modules/2.6.15-27-386/build: No such file or directory.  Stop.
make: *** [modules] Error 2
dmsn@arc:~/ipw2200-1.0.3$


You know what to do?


Thanks

---

### Post by mrlarone on 2006-09-22
read this thread. i don't know how to lnk to it so search for the title:

HOWTO: ipw2200 + wpa

perfect walkthru of what you need to do. 

i have to say though that this didn't end my quest to enable wifi, but it did get the driver installed. let me know what happens with you.

---

### Post by haxx on 2006-09-23
Curious what you have for a WiFi card

plz post results of "lspci" (without "") in terminal

---

### Post by mrlarone on 2006-09-23
i've actually managed to get it fully working now.

the problem is my laptop has a unsupported switch on the front to toggle the card, you can use the following cmds to do this from terminal:

$sudo iwconfig eth1 power 1       #this turns it on

$sudo iwconfig eth1 power 0       #this turns it off

two things to note 1)eth1 is the name of my wifi card (should be wlan1 but enough head banging for me) 2) i've istalled the 1.2.0 drivers and firmware from sforge

$lspci #results:

0000:00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
0000:00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
0000:00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
0000:00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
0000:00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
0000:00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
0000:00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
0000:00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
0000:00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
0000:00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
0000:00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
0000:00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
0000:00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
0000:06:05.0 Network controller: Intel Corporation PRO/Wireless 2200BG (rev 05)
0000:06:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:06:09.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)

---

