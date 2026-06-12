---
title: "WG311v3 Help!"
date: 2008-08-12
forum: Networking &amp; Wireless
---

### Post by Rossk on 2008-08-12
Hello.

Im have Ubuntu 8.04 installed on my pc. Im trying to get Wireless with a WG311v3 card. The Card works in Win XP home edition perfectly.

I installed ndiswrapper (V 1.52) and used the Win XP version of the WG311v3 driver. ndiswrapper set up the driver perfectly , and found the hardware. When I go and imput "iwconfig" into the Terminal, only "lo" and "eth0" show up and say that there are no wireless settings or something for them. I finished up the instilation, and configure ndiswrapper to start up on boot-up. I restart and log in. Then Ubuntu says that there is a fatal code error or something.

I tried a bunch of commend lines and i got errors like "the windows drivers failed to start the hardware".

So, basically , my system will not install and use my wireless card correctly. Ive heard that other people have gotten this card to work , so I have no clue as to why mine wont.

I also tried the tutorial on this web page :[https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3](https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3) .

It doesnt work either.

Someone please help me!

---

### Post by pytheas22 on 2008-08-12
Please post the output of:
```

lsusb
dmesg | grep -e wlan -e ndis
```

---

### Post by Rossk on 2008-08-13
bump

---

### Post by Rossk on 2008-08-13
heres the output from what you requested:

code:

lsusb 

Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

dmesg | grep -e wlan -e ndis 

[   32.078990] ndiswrapper version 1.52 loaded (smp=yes, preempt=no) 
[   32.882288] usbcore: registered new interface driver ndiswrapper 
[  155.026292] usbcore: deregistering interface driver ndiswrapper 
[  155.052469] ndiswrapper version 1.52 loaded (smp=yes, preempt=no) 
[  155.067919] ndiswrapper: driver wg311v3 (NETGEAR,02/22/2005,3.1.1.7) loaded 
[  155.070163] ndiswrapper: using IRQ 20 
[  155.170389] ndiswrapper (mp_init:216): couldn't initialize device: C0000001 
[  155.170400] ndiswrapper (pnp_start_device:439): Windows driver couldn't initialize the device (C0000001) 
[  155.170412] ndiswrapper (mp_halt:259): device eb84d480 is not initialized - not halting 
[  155.171998] ndiswrapper: device eth%d removed 
[  155.172711] ndiswrapper: probe of 0000:00:06.0 failed with error -22 
[  155.179696] usbcore: registered new interface driver ndiswrapper


and btw, the wireless adapter is pluged in to one of my open pci ports. Its a pci adapter.

---

### Post by Rossk on 2008-08-13
bump

---

### Post by Rossk on 2008-08-13
bump

---

### Post by pytheas22 on 2008-08-13
Thanks for the information.

I'm not sure exactly what's wrong, but there are a few possibilities.

First, it may be IRQ conflicts.  If possible, check your BIOS to see if you can reassign the IRQ address of the PCI bus that you the wireless card plugged into.  Or try plugging the card into a different slot.

It may also help to compile ndiswrapper from source.  To do so, run these commands (you should be plugged into ethernet first):
```

sudo -s
apt-get remove --purge ndiswrapper*
apt-get install build-essential
wget http://sourceforge.net/project/downloading.php?group_id=93482&use_mirror=internap&filename=ndiswrapper-1.53.tar.gz&92439738
tar -xzvf ndis*
cd ndis*
make
make install
```

Then you need to reinstall the Windows driver into ndiswrapper, and reboot.  Hopefully that will fix the problem.

If neither of the above helps, please post the output of:
```

ndiswrapper -l
lspci -nn
cat /proc/interrupts
```

---

### Post by Rossk on 2008-08-13
Ok im sligtly confused lol. I have no internet on the Ubuntu computer. So do i have to download the drivers/ software from another computer and then transfer it?

and i did try to reinstall ndiswrapper from 2 files that i downloaded off of another computer. no luck.

and heres the outputs from that code you asked for:

ndiswrapper -l

wg311v3 : driver installed 
	device (11AB:1FAA) present 

lspci -nn 


00:00.0 Host bridge [0600]: VIA Technologies, Inc. K8M800 Host Bridge [1106:0204] 
00:00.1 Host bridge [0600]: VIA Technologies, Inc. K8M800 Host Bridge [1106:1204] 
00:00.2 Host bridge [0600]: VIA Technologies, Inc. K8M800 Host Bridge [1106:2204] 
00:00.3 Host bridge [0600]: VIA Technologies, Inc. K8M800 Host Bridge [1106:3204] 
00:00.4 Host bridge [0600]: VIA Technologies, Inc. K8M800 Host Bridge [1106:4204] 
00:00.7 Host bridge [0600]: VIA Technologies, Inc. K8M800 Host Bridge [1106:7204] 
00:01.0 PCI bridge [0604]: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South] [1106:b188] 
00:06.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless [11ab:1faa] (rev 03) 
00:0a.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10) 
00:0f.0 IDE interface [0101]: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller [1106:3149] (rev 80) 
00:0f.1 IDE interface [0101]: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE [1106:0571] (rev 06) 
00:10.0 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 81) 
00:10.1 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 81) 
00:10.2 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 81) 
00:10.3 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 81) 
00:10.4 USB Controller [0c03]: VIA Technologies, Inc. USB 2.0 [1106:3104] (rev 86) 
00:11.0 ISA bridge [0601]: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South] [1106:3227] 
00:11.5 Multimedia audio controller [0401]: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller [1106:3059] (rev 60) 
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100] 
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101] 
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102] 
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103] 
01:00.0 VGA compatible controller [0300]: VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter [1106:3108] (rev 01) 


 cat /proc/interrupts :

           CPU0        
  0:        314   IO-APIC-edge      timer 
  1:        712   IO-APIC-edge      i8042 
  4:          2   IO-APIC-edge     
  7:          0   IO-APIC-edge      parport0 
  8:          3   IO-APIC-edge      rtc 
  9:          0   IO-APIC-fasteoi   acpi 
 12:      42410   IO-APIC-edge      i8042 
 14:      24747   IO-APIC-edge      libata 
 15:      35540   IO-APIC-edge      libata 
 16:          0   IO-APIC-fasteoi   eth0 
 17:          0   IO-APIC-fasteoi   sata_via 
 18:     295114   IO-APIC-fasteoi   uhci_hcd:usb1, uhci_hcd:usb2, uhci_hcd:usb3, uhci_hcd:usb4, ehci_hcd:usb5

---

### Post by Rossk on 2008-08-13
bump

---

### Post by pytheas22 on 2008-08-13
If you can plug your computer in with an ethernet cable temporarily, that would be the easiest way to do this, and you could follow the steps from my last post.

If you really have no way of getting online with Ubuntu right now, then follow these steps:

1. download [this file]("http://downloads.sourceforge.net/ndiswrapper/ndiswrapper-1.53.tar.gz?modtime=1211931005&big_mirror=0") and transfer it to Ubuntu; save it on the desktop there.

2. put your Ubuntu installation CD in the drive.  Then go to System>Administration>Software Sources.  Under the "Ubuntu Software" tab, make sure that the box to use your CD as a repository is checked (this box is under the "Installable from CD-ROM/DVD" section).

3. now run these commands to compile ndiswrapper:
```

cd ~/Desktop
sudo -s
apt-get remove --purge ndiswrapper
apt-get update
apt-get install build-essential
tar -xzvf ndiswrapper*
cd ndiswrapper*
make
make install
```

After this, you have to reinstall your Windows driver into ndiswrapper as you did before, using the "ndiswrapper -i" command (there is no graphical application available this time).

Also, please don't keep bumping the thread unless I forget to reply for a long time...I'll reply as soon as possible, but I'm not always at my computer.

---

