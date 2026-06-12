---
title: "No wireless connection"
date: 2011-04-25
forum: New to Ubuntu
---

### Post by Mean Mr Mustard on 2011-04-25
Re: Ubuntu wireless connection 
Many thanks to those that took the time to reply to me...and apologies to all if I have stepped on any toes  by posting in the wrong place previously. Anyway here is the info I hope will explain the problem after using code 1spci in Terminal... I am no expert here so please bear with me. Many thanks :confused:

```
B UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc RV410 [Radeon X700 Pro (PCIE)]
01:00.1 Display controller: ATI Technologies Inc RV410 [Radeon X700 Pro (PCIE)] (Secondary)
03:01.0 Multimedia controller: Philips Semiconductors SAA7134/SAA7135HL Video Broadcast Decoder (rev 01)
03:03.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev 80)
03:04.0 Communication controller: Agere Systems V.92 56K WinModem (rev 03)
03:06.0 Ethernet controller: VIA Technologies, Inc. VT6105/VT6106S [Rhine-III] (rev 8b)
```

---

### Post by ImperialXT on 2011-04-25
Might help if you told us exactly what your problem was in *this* thread.

---

### Post by Mean Mr Mustard on 2011-04-25
Well ImperialXT thank you for the comment...the  problem IS I cannot access the internet via my desktop usuing Ubuntu 1010 which I have loaded on PC to run along side Windows XP. I have no ethernet connection to router as it is located downstairs just the onboard wireles card in desktop which works fine in XP but nothing doing in ubuntu. I pumped code 1spci into Terminal  and got the result previously published...So any help  on this would be very much appreciated.

---

### Post by 6677 on 2011-04-26
My laptop I had to get a new set of drivers for the wireless card. I'm a complete ubuntu noob so I dont feel I can go into detail about how to get those

---

### Post by Mean Mr Mustard on 2011-04-26
> **6677 said:**
> My laptop I had to get a new set of drivers for the wireless card. I'm a complete ubuntu noob so I dont feel I can go into detail about how to get those
 
Many thanks for the input 6677, I will explore that possibility...who knows? :D

---

### Post by josephmills on 2011-04-26
could we all please see a ```
lspci -nn
``` this next one takes a while to load also please take out any ip address ```
sudo lshw -C network
``` thanks

---

### Post by Mean Mr Mustard on 2011-08-28
Hi one and all, have decided to give this Linux thing another bash and have now downloaded version 11.04 and running dual sysytem alongside windows XP. STILL no wireless card recognition and hence no internet connection via desktop so am using my laptop via windows 7 to get here. have extracted following from Terminal window within ubuntu 11.04 and hope someone can decipher it for me and ideally explain whats going on and why my Desk Top PC will not recognise wireless card in Ubuntu mode but if I switch to XP bingo! I am back on the internet via PCI wireless card!!!

Here is the extract from Terminal window...many thanks.
 
```
mike@ubuntu:~$ sudo lshw -C network
[sudo] password for mike:
*-network
description: Ethernet interface
product: VT6105/VT6106S [Rhine-III]
vendor: VIA Technologies, Inc.
physical id: 6
bus info: pci@0000:03:06.0
logical name: eth0
version: 8b
serial: 00:11:09:f2:4c:75
size: 10Mbit/s
capacity: 100Mbit/s
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd
autonegotiation
configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.5.0
duplex=half latency=32 link=no maxlatency=8 mingnt=3 multicast=yes port=MII speed=10Mbit/s
resources: irq:18 ioport:d300(size=256) memory:d8003000-d80030ff
*-network DISABLED
description: Wireless interface
physical id: 1
bus info: usb@1:6.1
logical name: wlan0
serial: 00:11:09:df:ad:16
capabilities: ethernet physical wireless
configuration: broadcast=yes driver=rt2500usb driverversion=2.6.38-8-generic firmware=N/A
link=no multicast=yes wireless=IEEE 802.11bg
mike@ubuntu:~$ sudo lspci
00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev
04)
00:01.0 PCI bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL PCI Express Root Port (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High
Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express
Port 1 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI
#1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI
#2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI
#3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI
#4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2
EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE
Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller
(rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc RV410 [Radeon X700 Pro (PCIE)]
01:00.1 Display controller: ATI Technologies Inc RV410 [Radeon X700 Pro (PCIE)] (Secondary)
03:01.0 Multimedia controller: Philips Semiconductors SAA7134/SAA7135HL Video Broadcast
Decoder (rev 01)
03:03.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI
Controller (rev 80)
03:04.0 Communication controller: Agere Systems V.92 56K WinModem (rev 03)
03:06.0 Ethernet controller: VIA Technologies, Inc. VT6105/VT6106S [Rhine-III] (rev 8b)
mike@ubuntu:~$ sudo lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c502 Logitech, Inc. Cordless Mouse & iTouch Keys
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 008: ID 0db0:4023 Micro Star International
Bus 001 Device 007: ID 0bc7:0006 X10 Wireless Technology, Inc. Wireless Transceiver (ACPIcompliant)
Bus 001 Device 006: ID 0db0:6855 Micro Star International Bluetooth Device
Bus 001 Device 005: ID 148f:2570 Ralink Technology, Corp. RT2570 Wireless Adapter
Bus 001 Device 004: ID 05e3:0605 Genesys Logic, Inc. USB 2.0 Hub [ednet]
Bus 001 Device 003: ID 04b8:0122 Seiko Epson Corp. Perfection 3590 scanner
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/LEFT]
mike@ubuntu:~$

```
Many thanks to anyone who can spare me their time here, I would be most grateful.

---

### Post by blade4 on 2011-08-28
Try this link : 
[URL="http://www.viaarena.com/displaydrivers.aspx?PageID=1&OSID=60&CatID=3760&SubCatID=127"]
http://www.viaarena.com/displaydrivers.aspx?PageID=1&OSID=60&CatID=3760&SubCatID=127[/URL]

The site says this driver is supported for 10.04 . Dunno if this will  work on 11.04 . I'll try to find out more about this . Till then , keep  this as a backup solution .

---

### Post by Mean Mr Mustard on 2011-08-28
Many thanks Blade4 for your help here its much appreciated. Please bear in mind that I am on a wing and a prayer here as I am very new to this stuff, but willing to try just not able to run at your speed I guess. May seem daft question but what do do with the driver once I have got it????

---

### Post by blade4 on 2011-08-28
Just extract the file . The installation instructions are inside in a file called linux.txt .  :) 

As for my trying to find out some more stuff , unfortunately this was all I could find . If you don't have anything terribly important on your ubuntu installation , give the driver a try . 
 
Hope this solves your probs :)

---

### Post by chili555 on 2011-08-28
You don't need to extract and compile the via-rhine driver for your wireless. It is an ethernet driver and you already have it:> *-network
description: [COLOR="Red"]Ethernet interface[/COLOR]
product: VT6105/VT6106S [Rhine-III]
vendor: VIA Technologies, Inc.
physical id: 6
bus info: pci@0000:03:06.0
logical name: eth0
version: 8b
 ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd
autonegotiation
configuration: autonegotiation=on broadcast=yes [COLOR="Red"]driver=via-rhine[/COLOR] driverversion=1.5.0Is your wireless PCI (internal) or USB?> *-network DISABLED
description: Wireless interface
physical id: 1
bus info: usb@1:6.1
logical name: wlan0
serial: 00:11:09:df:ad:16
capabilities: ethernet physical wireless
configuration: broadcast=yes driver=rt2500usb driverversion=2.6.38-8-generic firmware=N/A
link=no multicast=yes wireless=IEEE 802.11bgOR?> Bus 001 Device 005: ID 148f:2570 Ralink Technology, Corp. RT2570 Wireless AdapterThe wireless shows Disabled; is it disabled in the BIOS? Please check.

I wonder if it's actually one of the rare motherboard mounted wireless devices that's connected to an internal USB bus.

---

### Post by Mean Mr Mustard on 2011-08-29
Mr Chili555 sir I am so thrilled that you have taken time to help me, thank you so much.
 
My wireless card is INTERNAL and is functioning fine when I switch to XP but when I try Ubuntu the wirelss connection is just not there its greyed out???????????
Also have checked my Device Manager and Network adapter is listed as RT2500USB Wireless LAN Card

---

### Post by Zetheroo on 2011-08-29
Hi all ... believe it or not I too have this RT2570 Wireless Adapter which, afaik, is somewhere integrated on the motherboard. 

I am trying to use 11.04 on the system but the network manager says:

"wireless is disabled by hardware switch"

Thing is I don't think there is any "hardware switch" - at least when running Windows I have never had to much around with that.

It seems to me that the device is seen and so the driver must be present and working ... it just thinks it's locked or switched off ....

---

### Post by chili555 on 2011-08-29
@MMMustard--

What does this tell us?```
rfkill list all
sudo rfkill unblock all
rfkill list all
```Thanks.

---

### Post by Mean Mr Mustard on 2011-08-29
Hi Chili555...please bear with me as I am struggling with this. Results as below:-
 
```
mike@ubuntu:~$ rfkill list all
0: hci0: Bluetooth
            Soft blocked: no
            Hard blocked: no
1: phy0: Wireless LAN
            Soft blocked: no
            Hard blocked: yes
mike@ubuntu:~$ sudo rfkill unblock all
[sudo] password for mike:
Sorry, try again.
[sudo] password for mike:
mike@ubuntu:~$ sudo rfkill unblock all
mike@ubuntu:~$ rfkill list all
0: hci0: Bluetooth
            Soft blocked: no
            Hard blocked: no
1: phy0: Wireless LAN
            Soft blocked: no
            Hard blocked: yes
mike@ubuntu:~$
```

---

### Post by chili555 on 2011-08-29
> please bear with me as I am struggling with this.No problems at all; sometimes I struggle, too! 

Of course, we wonder why the wireless is shown as 'hard blocked' when this is evidently a desktop machine with no wireless switch. Have you checked in the BIOS? Is there an option to enable/disable on-board wireless? Is there an option to enable dependent on the operating system; that is, let the OS decide? What make and model is the desktop machine? What does this tell us?```
dmesg | grep -i usb
```

---

### Post by Mean Mr Mustard on 2011-08-29
Have looked at BIOS (first time!) but cannot find any reference to wireless LAN card?
 
```
Headings in BIOS (version 4.0G (01/27/05) are as follows:-
 
STANDARD CMOS FEATURES
ADVANCED BIOS
ADVANCED CHIPSET FEATURES
INTERGRATED PERIPHERALS
POWER MANAGEMENT SETUP
PnP/PCI CONFIGURATIONS
 
ALL of the above I have "entered" and searched, but no speciphic reference to card?
 
MEDION PC
Operating System
MS Windows XP Home 32-bit SP3
CPU
Intel Pentium 4 640 (3.2GHz)
Prescott 90nm Technology
RAM
1.00 GB Dual-Channel DDR @ 199MHz (3-3-3-8)
Motherboard
MICRO-STAR INTERNATIONAL CO., LTD MS-7091 (Socket 478) 62 °C
Graphics
SyncMaster (1920x1080@60Hz)
128MB MEDION RADEON X740XL (MSI)
Hard Drives
156GB Western Digital WDC WD1600JD-00HBB0 (SATA) 39 °C
156GB Western Digital WDC WD1600JD-00HBB0 (SATA) 42 °C
Generic USB Hub
RT2500 USB Wireless LAN Card
MSI Bluetooth Device
X10 USB Wireless Transceiver (ACPI-compliant)
Optical Drives
PIONEER DVD RW DVR-109
HL-DT-ST DVD-ROM GDR8163B
Audio
C-Media High Definition Audio Device
 
mike@ubuntu:~$ dmeg | grep -i usb 
No command 'dmeg' found, did you mean: 
Command 'dreg' from package 'emboss' (universe) 
Command 'dmesg' from package 'util-linux' (main) 
dmeg: command not found 
mike@ubuntu:~$ 
```
 
Steep learning curve for me Chili555 but enjoying it all the same.

---

### Post by Mean Mr Mustard on 2011-08-29
My appologies Chili555, but I misread your instructions...see below for correct info,
 
 
```
[EMAIL="mike@ubuntu:~$"]mike@ubuntu:~$[/EMAIL] dmesg | grep -i usb
[    0.341597] usbcore: registered new interface driver usbfs
[    0.341627] usbcore: registered new interface driver hub
[    0.341679] usbcore: registered new device driver usb
[    0.729988] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.730120] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.750023] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.750218] hub 1-0:1.0: USB hub found
[    0.750335] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.750354] uhci_hcd: USB Universal Host Controller Interface driver
[    0.750486] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.750719] hub 2-0:1.0: USB hub found
[    0.750875] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.751102] hub 3-0:1.0: USB hub found
[    0.751267] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.760258] hub 4-0:1.0: USB hub found
[    0.760415] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.760651] hub 5-0:1.0: USB hub found
[    1.130116] usb 1-2: new high speed USB device using ehci_hcd and address 3
[    1.440046] usb 1-6: new high speed USB device using ehci_hcd and address 4
[    1.592645] hub 1-6:1.0: USB hub found
[    1.870056] usb 2-1: new low speed USB device using uhci_hcd and address 2
[    2.130331] usb 1-6.1: new high speed USB device using ehci_hcd and address 5
[    2.450339] usb 1-6.2: new full speed USB device using ehci_hcd and address 6
[    2.640346] usb 1-6.3: new low speed USB device using ehci_hcd and address 7
[    2.830351] usb 1-6.4: new high speed USB device using ehci_hcd and address 8
[   14.766126] usbcore: registered new interface driver uas
[   14.860379] input: X10 Wireless Technology Inc USB Receiver as /devices/pci0000:00/0000:00:1d.7/usb1/1-6/1-6.3/input/input3
[   14.861727] usb 1-6.3: Weird data, len=1 ff 00 00 00 00 00 ...
[   14.870186] usbcore: registered new interface driver ati_remote
[   14.870193] ati_remote: 2.2.1:ATI/X10 RF USB Remote Control
[   15.205434] Initializing USB Mass Storage driver...
[   15.206761] Bluetooth: Generic Bluetooth USB driver ver 0.6
[   15.213148] usbcore: registered new interface driver btusb
[   15.215910] scsi4 : usb-storage 1-6.4:1.0
[   15.223527] usbcore: registered new interface driver usb-storage
[   15.223534] USB Mass Storage support registered.
[   15.316715] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/input/input4
[   15.319663] generic-usb 0003:046D:C502.0001: input,hidraw0: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:1d.0-1/input0
[   15.353574] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.1/input/input5
[   15.353892] generic-usb 0003:046D:C502.0002: input,hidraw1: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:1d.0-1/input1
[   15.353955] usbcore: registered new interface driver usbhid
[   15.353960] usbhid: USB HID core driver
[   15.807843] Registered led device: rt2500usb-phy0::radio
[   15.807968] Registered led device: rt2500usb-phy0::quality
[   15.808463] usbcore: registered new interface driver rt2500usb
[EMAIL="mike@ubuntu:~$"]mike@ubuntu:~$[/EMAIL]
```

---

### Post by chili555 on 2011-08-29
I'm studying. I don't have a solution yet.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/553782](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/553782)

---

### Post by chili555 on 2011-08-29
What options are in the BIOS in INTERGRATED PERIPHERALS? Also, please post:```
ls /proc/acpi
```Thanks.

---

### Post by Mean Mr Mustard on 2011-08-29
USB CONTROLLER ENABLED
ON BOARD USB USB 2.0
USB KEYBOARD SUPPORT ENABLED
AZALIA / AC97 SELECTION AUTO
ON BOARD LAN BOOT ROM DISABLED
IO DEVICES CONFIGURATION Press Enter
IDE DEVICES CONFIG Press Enter
SATA DEVICES CONFIG Press Enter
 
 
Entermike@ubuntu:~$ ls /proc/acpi
ac_adapter battery button event wakeup
mike@ubuntu:~$ 
 
 
Many thanks for your time on this it is greatly appreciated.

---

### Post by chili555 on 2011-08-30
Is there a WIRELESS section in the BIOS under ADVANCED? What are the options?

---

### Post by Mean Mr Mustard on 2011-08-30
No Wirelsss option shown?
 
ADVANCED BIOS FEATURES as follows:-
 
Execute Disable Bit (ENABLED)
Hyper-Threading Function (ENABLED)
Quick Boot (ENABLED)
Security Option (Set Up)
Boot to OS/2 (YES)
Boot Sequence (Press Enter)

---

### Post by Mean Mr Mustard on 2011-08-31
> **chili555 said:**
> Is there a WIRELESS section in the BIOS under ADVANCED? What are the options?
 
Hi Chili555...have you had any further thoughts on my problem or is it back to Windows for me?
 
Many thanks for  all your efforts all the same.

---

### Post by chili555 on 2011-09-01
Please see my PM.

I expect that the computer was built with the expectation that it would only ever have Windows and the RT2500 wireless driver and utility installed. I expect the utility has some magic way to enable and disable wireless. I downloaded it and tried to extract it and tried to install it on my own system with Wine; all to no avail.

I wonder if there is a jumper on the motherboard that controls the wireless USB jumper JUSB2? [http://217.110.237.70/Manuals/Medion%208383XL%20mit%20MS-7091.pdf](http://217.110.237.70/Manuals/Medion%208383XL%20mit%20MS-7091.pdf)

Will the wireless work if you change the connector from JUSB2 to the adjacent JUSB1?

I have been unable to find anywhere in the driver or its dependencies that can be used to correct a hard block. 

I wish I had a better answer.

Before I returned to Windows, I'd certainly look into any of the many $15-20 USB wireless devices, such as this: [https://help.ubuntu.com/community/WifiDocs/Device/Asus%20USB-N13_Natty%2011.04](https://help.ubuntu.com/community/WifiDocs/Device/Asus%20USB-N13_Natty%2011.04)

---

### Post by Mean Mr Mustard on 2011-09-01
Many thanks for ALL of your efforts its greatly appreciated. I will investigate alternative wireless devices after I have explored the inside of my PC....now wheres my face mask and gloves!

---

### Post by androssofer on 2011-09-01
> **Mean Mr Mustard said:**
> Many thanks for ALL of your efforts its greatly appreciated. I will investigate alternative wireless devices after I have explored the inside of my PC....now wheres my face mask and gloves!

i'd recommend: 

[http://www.amazon.co.uk/Belkin-802-11g-Wireless-Network-Adapter/dp/B001J2XSMA/ref=cm_cr_pr_product_top](http://www.amazon.co.uk/Belkin-802-11g-Wireless-Network-Adapter/dp/B001J2XSMA/ref=cm_cr_pr_product_top)

or if ur in the US:

[http://www.amazon.com/F5D7050-Wireless-802-11g-Network-Adapter/dp/B0002HA7FY/ref=sr_1_1?ie=UTF8&qid=1314894370&sr=8-1](http://www.amazon.com/F5D7050-Wireless-802-11g-Network-Adapter/dp/B0002HA7FY/ref=sr_1_1?ie=UTF8&qid=1314894370&sr=8-1)

as its nice n cheap and works out the box..

---

### Post by Redmage913 on 2011-09-01
+1. I've used the F5D7050 for a couple years now, and I've had no problems with it in Ubuntu.

---

### Post by Mean Mr Mustard on 2011-09-01
Many thanks for the tip its much appreciated.

---

### Post by Mean Mr Mustard on 2011-09-08
Have fitted new AR5007G PCI card which works fine in XP but nothing doing in 11.04. Need help to get right driver installed please.
 
Many thanks

---

### Post by Mean Mr Mustard on 2011-10-10
ANYONE OUT THERE CARE TO HELP ME PLEASE?
 
```
mike@ubuntu:~$ sudo lshw -C network
[sudo] password for mike: 
  *-network:0 DISABLED    
       description: Wireless interface
       product: AR5007G Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 2
       bus info: pci@0000:03:02.0
       logical name: wlan1
       version: 01
       serial: 54:e6:fc:c9:0a:f3
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k driverversion=2.6.38-11-generic firmware=N/A latency=168 link=no maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11bg
       resources: irq:18 memory:d8000000-d800ffff
  *-network:1
       description: Ethernet interface
       product: VT6105/VT6106S [Rhine-III]
       vendor: VIA Technologies, Inc.
       physical id: 6
       bus info: pci@0000:03:06.0
       logical name: eth0
       version: 8b
       serial: 00:11:09:f2:4c:75
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.5.0 duplex=half latency=32 link=no maxlatency=8 mingnt=3 multicast=yes port=MII speed=10Mbit/s
       resources: irq:18 ioport:d300(size=256) memory:d8013000-d80130ff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       bus info: usb@1:6.1
       logical name: wlan0
       serial: 00:11:09:df:ad:16
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt2500usb driverversion=2.6.38-11-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bg
mike@ubuntu:~$
```

---

### Post by chili555 on 2011-10-10
I am still quite mystified as to why both the wireless devices are disabled. Please post:```
rfkill list all
dmesg | grep -e ath -e 03:02
```Thanks.

---

### Post by Mean Mr Mustard on 2011-10-10
> **chili555 said:**
> I am still quite mystified as to why both the wireless devices are disabled. Please post:```
rfkill list all
dmesg | grep -e ath -e 03:02
```Thanks.
 
 Hope this helps.
 
```
ubuntu@ubuntu:~$ rfkill list all 
0: hci0: Bluetooth 
Soft blocked: no 
Hard blocked: no 
1: phy1: Wireless LAN 
Soft blocked: no 
Hard blocked: yes 
2: phy0: Wireless LAN 
Soft blocked: no 
Hard blocked: no 
ubuntu@ubuntu:~$ dmesg | grep -e ath -e 03:02 
[ 4.308388] device-mapper: multipath: version 1.2.0 loaded 
[ 4.308394] device-mapper: multipath round-robin: version 1.0.0 loaded 
[ 64.261572] ath5k 0000:02:02.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18 
[ 64.261644] ath5k 0000:02:02.0: registered as 'phy0' 
[ 64.761016] ath: EEPROM regdomain: 0x809c 
[ 64.761022] ath: EEPROM indicates we should expect a country code 
[ 64.761026] ath: doing EEPROM country->regdmn map search 
[ 64.761030] ath: country maps to regdmn code: 0x52 
[ 64.761034] ath: Country alpha2 being used: CN 
[ 64.761037] ath: Regpair used: 0x52 
[ 64.772540] ath5k phy0: Atheros AR2417 chip found (MAC: 0xf0, PHY: 0x70) 
ubuntu@ubuntu:~$
```

---

### Post by chili555 on 2011-10-10
> ubuntu@ubuntu:~$ rfkill list all
0: hci0: Bluetooth
Soft blocked: no
Hard blocked: no
1: phy1: Wireless LAN
Soft blocked: no
[COLOR="Red"]Hard blocked: yes[/COLOR]
2: phy0: Wireless LAN
Soft blocked: no
Hard blocked: no Ordinarily, a desktop machine will have no wireless switch. I am even more mystified! There is nothing in dmesg that I've seen so far associated with your Atheros card that is an error. Obviously, if we saw an error, we could try to fix it.

I am further mystified that the Atheros shows first on bus #0000:03:02.0 in lshw but then at #0000:02:02.0 in dmesg. 

Let's look a bit deeper. Please reboot so we start with a clean slate and then do:```
dmesg > MMMustard.txt
sudo cat /var/log/syslog | tail -n50 >> MMMustard.txt
lspci -nn >> MMMustard.txt
zip MMMustard.zip MMMustard.txt
```You will find the file MMMustard.zip in your user directory. Please attach it to your reply using the paperclip tool at the top of the reply box.

---

### Post by Lisiano on 2011-10-10
@chilli555
```
[ 64.261644] ath5k 0000:02:02.0: registered as 'phy0' 
```Notice that the AR5007G is registered as phy0.
```
2: phy0: Wireless LAN
Soft blocked: no
Hard blocked: no
```
The AR5007G is not blocked, both software nor hardware.

@Mustard
Do you see any Wireless Access Points in the Network Manager icon (Looks like a WiFi signal/2 arrows going up and down).
Please show us the output of 
```
nm-tool
```

---

### Post by chili555 on 2011-10-11
> The AR5007G is not blocked, both software nor hardware.Indeed. But then why is it:> *-network:0 *[COLOR="Red"]DISABLED[/COLOR]*
description: Wireless interface
product: AR5007G Wireless Network Adapter
vendor: Atheros Communications Inc.
physical id: 2
bus info: pci@0000:03:02.0
logical name: wlan1
version: 01
serial: 54:e6:fc:c9:0a:f3:confused:

---

### Post by Lisiano on 2011-10-11
That, I have no idea. If nm-tool will report nearby APs then the card is actually Active soooo.. I don't know.

---

### Post by Mean Mr Mustard on 2011-10-11
Dont think chilli555 that first says much, though I think I'm missing something here? Also dont understand where the MMMustard zip file is or where paper clip is-???????? - sorry.
 
```
ubuntu@ubuntu:~$ dmesg > MMMustard.txt 
ubuntu@ubuntu:~$ sudo cat /var/log/syslog | tail -n50 >> MMMustard.txt 
ubuntu@ubuntu:~$ lspci -nn >> MMMustard.txt 
 
 
ubuntu@ubuntu:~$ nm-tool 


NetworkManager Tool 


State: disconnected 


- Device: wlan1 ---------------------------------------------------------------- 
Type: 802.11 WiFi 
Driver: rt2500usb 
State: unavailable 
Default: no 
HW Address: 00:11:09:DF:AD:16 


Capabilities: 


Wireless Properties 
WEP Encryption: yes 
WPA Encryption: yes 
WPA2 Encryption: yes 


Wireless Access Points 




- Device: wlan0 ---------------------------------------------------------------- 
Type: 802.11 WiFi 
Driver: ath5k 
State: unavailable 
Default: no 
HW Address: 54:E6:FC:C9:0A:F3 


Capabilities: 


Wireless Properties 
WEP Encryption: yes 
WPA Encryption: yes 
WPA2 Encryption: yes 


Wireless Access Points 




- Device: eth0 ----------------------------------------------------------------- 
Type: Wired 
Driver: via-rhine 
State: unavailable 
Default: no 
HW Address: 00:11:09:F2:4C:75 


Capabilities: 
Carrier Detect: yes 
Speed: 10 Mb/s 


Wired Properties 
Carrier: off 




ubuntu@ubuntu:~$
```

---

### Post by Mean Mr Mustard on 2011-10-11
[Quote]- Lisianno - Do you see any Wireless Access Points in the Network Manager icon (Looks like a WiFi signal/2 arrows going up and down).

Please remember I am VERY new to this...There is no wifi signal just fan like symbol, when I click on that both wireless network cards are greyed out. All that is highlighted is VPN Connections, Enable Networking (which is ticked). If you guys are mistified by all of this then I am doomed!

---

### Post by Lisiano on 2011-10-11
That is the icon I was talking about, the names are greyed out since they aren't options and just show what adapter is connected to where.
Random idea, is the "Enable Wireless" ticked in that menu?
What is written directly under the adapter names?

---

### Post by Javelin Dan on 2011-10-11
Mean Mr. Mustard - You could spend months tearing your hair out over this (if you have any left) and still not solve the problem. Ask me how I know! I am someone who has burned literally dozens of different Linux distros and tried connecting to my wireless net via several different wireless usb dongles. I have seen wide ranging performance not only between different distros, but even between different versions of the same distro. My Ralink (2850) 802.11 is spotty at best, while my SMC 802.11 rocks! I dont know if it's ever failed me on any flavor of Linux! It sells on Amazon for about $15 (US). An old Net Gear that I had that worked well on XP wouldn't work on any LInux period, although I'm told some models do (never tried the ndiswrapper thing though). You can spend weeks trying to configure what you've got, or just offer it up to the Linux gods and buy something that works. Let me know if you're interested and I'll dig up the model # of the one I have. Good luck!

---

### Post by Mean Mr Mustard on 2011-10-11
> **Lisiano said:**
> That is the icon I was talking about, the names are greyed out since they aren't options and just show what adapter is connected to where.
Random idea, is the "Enable Wireless" ticked in that menu?
What is written directly under the adapter names?
The Enable Wireless is greyed out.

---

### Post by Mean Mr Mustard on 2011-10-11
Thanks for that...BUT I have an internal Rt2500usb card which refuses to fire up in 11.04, but works great in XP. So I then installed a further PCI wireless card AR5007G...which also works great in XP but nothing doing (SO FAR) in 11.04. My problem is I'm not ready to throw the towel in yet! This PC is 7yrs old and maybe its time to buy a new one! I just wanted to have a go with Linux and not have to return to MS. Would wiping the PC claen of XP and solely running Linux solve the issue?

---

### Post by Mean Mr Mustard on 2011-10-11
Would wiping the PC claen of XP and solely running Linux solve the issue?

---

### Post by Javelin Dan on 2011-10-11
No, Mean Mr. Mustard, reloading will not help. And I'm afraid you are missing my point. People much smarter than you and me together have tried to configure wireless connections and never got it done. From my experience all the Ralinks are spotty performers in Linux and therefore problematic. I was like you once - I already had this equipment and by God! I was going to make it work! But simply buying a new dongle that plugged and played right out of the box has made my life sooo much easier. Bulldogs are kinda cool, but they tend to die young...

---

### Post by Mean Mr Mustard on 2011-10-11
My other problem being that my broadband router is downstairs! My PC Den is UPSTAIRS!! I suppose I could invest in some of those "route plugs"" that uses house wiring to transfer signal and use ethernet connection instead...BUT that just goes around the problem!!

---

### Post by jon zendatta on 2011-10-11
On a side note, Netgear wireless cards don't work on Ubuntu with WPA security, but do with WEP.

---

### Post by anewguy on 2011-10-11
Most of the time we are able to get any adapter working, it's just a matter of how - native/restricted drivers or using ndiswrapper.  However, there seems to be a little more going on here for the OP than just the wireless.

That being said, *IF* the OP is interested, you can get the factory refurbished version of the USB adapter I use currently for $4.99 (+shipping if you don't live near one of their stores).  Mine has worked "out of the box":

[http://www.microcenter.com/single_product_results.phtml?product_id=0373209]("http://www.microcenter.com/single_product_results.phtml?product_id=0373209")

It's nothing special, no fancy stuff.  Mine just works - no problems, etc..  I use mine to connect to our WPA2 protected network.

If you still want to try to get on-board working, it's a little puzzling - not because it's wireless, but because other portions of the networking don't look right as chilli555 has pointed out.

However, I do have a suspicion:  your latest output posting shows 2 wireless adapters installed.  If one is on the motherboard, see if you can disable it via the BIOS on your system.  If both are cards you plugged into the motherboard, remove 1 of them.  Having 2 wireless adapters is highly compounding things for what you want to do right now.

As far as the RT2500 series - it can be made to work just fine.  Same with the Atheros.  Just pick which you to have working and remove/disable the other.  

Then post back and we'll be able to help you much easier.

Dave ;)

---

### Post by Mean Mr Mustard on 2011-10-11
Dave...Many thanks for your input on this but if you look back over the history of my problem you will see thatI have I been right thorugh BIOS and have been unable to solve prolem as to WHY card refuses to work outside of XP/ I have inturn dsiabled both cards but AGAIN inturn EACH of the cards will not work via ubuntu. 
 
The RT2500usb INTERNAL card is not mentioned ANYWHERE in the BIOS. 
 
BOTH cards are operating at same time now BUT nothing doing in ubuntu!!!!!! ONLY XP.
 
I could go back inside PC and REMOVE AR5007G card that I recently installed but that puts be back to square one where I started????????

---

### Post by Mean Mr Mustard on 2011-10-11
jon zendatta...that is very interesting and worth exploring further, thank you.

---

### Post by dave2001 on 2011-10-11
Here's another vote to buy a cheap usb wireless. I too, like some of the other people who have posted in this thread, have spent some long hours attempting to make a piece of hardware work with linux because "it worked fine with windows!". The more I've learned about linux and windows, I've come to understand this isn't the best reasoning. Microsoft actively tries to make things difficult for linux programmers, and that means that some hardware companies who are on the Gates Wagon also do the same thing. Some hardware just doesn't play nice with linux. Also some other hardware isn't supported because it's not on a priority list for the distro dev team. All old hardware eventually falls into the second category. 

So, for one of these reasons (or whatever reason) your hardware doesn't work with linux. Could you possibly fix it? Yes. Could you possibly also waste a huge amount of time and never fix it? Yes. 
Your choice.. how much of your time is worth the 10-15 bucks it would cost for a new wireless usb key?

---

### Post by Mean Mr Mustard on 2011-10-11
> **dave2001 said:**
> Here's another vote to buy a cheap usb wireless. I too, like some of the other people who have posted in this thread, have spent some long hours attempting to make a piece of hardware work with linux because "it worked fine with windows!". The more I've learned about linux and windows, I've come to understand this isn't the best reasoning. Microsoft actively tries to make things difficult for linux programmers, and that means that some hardware companies who are on the Gates Wagon also do the same thing. Some hardware just doesn't play nice with linux. Also some other hardware isn't supported because it's not on a priority list for the distro dev team. All old hardware eventually falls into the second category. 

So, for one of these reasons (or whatever reason) your hardware doesn't work with linux. Could you possibly fix it? Yes. Could you possibly also waste a huge amount of time and never fix it? Yes. 
Your choice.. how much of your time is worth the 10-15 bucks it would cost for a new wireless usb key?
Please  undertsand that I am new to all of this. What guarantee is there that an external usb dongle will solve the problem? Do I end up with a pile of usb sticks/PCI cards before I quit on this?

---

### Post by anewguy on 2011-10-11
> **Mean Mr Mustard said:**
> Dave...Many thanks for your input on this but if you look back over the history of my problem you will see thatI have I been right thorugh BIOS and have been unable to solve prolem as to WHY card refuses to work outside of XP/ I have inturn dsiabled both cards but AGAIN inturn EACH of the cards will not work via ubuntu. 
 
The RT2500usb INTERNAL card is not mentioned ANYWHERE in the BIOS. 
 
BOTH cards are operating at same time now BUT nothing doing in ubuntu!!!!!! ONLY XP.
 
I could go back inside PC and REMOVE AR5007G card that I recently installed but that puts be back to square one where I started????????

If you have no "access" to the rt2500, the yes I would remove the AR5007G.  But even more importantly:

- I would back up any data, etc., you need from Ubuntu
- remove the AR5007G card
- reboot using a LiveCD and completely reinstall Ubuntu.  If you are going to use the same release then I specify manual partitioning and be sure it is formating the Ubuntu partitions (except of course swap).

When you have done that, then post back.  I personally think there has been to many unknowns done to try to get both of these adapters working that it would be better to start with a clean slate:  fresh Ubuntu install and only 1 wireless adapter installed.  Then we can concentrate on getting that 1 adapter to work.  After that, we can try to add your 2nd adapter, but I really don't think that is going to work in Ubuntu.  So, in order to judge better, I also need to ask what you are doing or attempting to do that you need 2 adapters in Linux.

I know this seems like a lot of work, but too many times we just have too many unknowns in cases like this and it's best to start with a clean slate.  Just as examples - not saying you did any or all of these - if you installed drivers for 1 card and in the process it updated things like the blacklist.conf file or other things, perhaps tried ndiswrapper, tried the drivers for the 2nd card, etc., it just compounds things we need to "undo".

With a clean slate and only 1 adapter we should (can't guarantee 100%, but usually) be able to get wireless running.  Just don't install anything - no wirless drivers, etc. - after the clean install.

Dave ;)

---

### Post by Mean Mr Mustard on 2011-10-11
Dave...The ONLY card I am confident of removing is the one I very recently fitted myself.The original onboard RT2500usb card is the one that I will leave alone then. Its just that I feel as if I am going around in circles with this? As for ubuntu, what do you mean by a LiveCD please?
 
As for why two Cards..no special reason other than an attempt to have one that would work in ubuntu and I am  not expert enough to remove original RT2500usb card without probably creating even more problems!
 
I will be back!

---

### Post by chili555 on 2011-10-11
> Also dont understand where the MMMustard zip file is or where paper clip is-???????? - sorry.The MMMustard.zip file is in your Home Folder. Open it and click the column header to arrange the files by name. Scroll down to the Ms and there is it. 

Reply to this post and attach the file using the paperclip tool at the top of the reply box. Please see attached.

---

### Post by chili555 on 2011-10-11
> If you have no "access" to the rt2500, the yes I would remove the AR5007G. But even more importantly:@anewguy--

You might review our efforts to get the internal card going starting about post #11.

---

### Post by Mean Mr Mustard on 2011-10-11
> **chili555 said:**
> The MMMustard.zip file is in your Home Folder. Open it and click the column header to arrange the files by name. Scroll down to the Ms and there is it. 

Reply to this post and attach the file using the paperclip tool at the top of the reply box. Please see attached.
Where do I find the Home Folder - sorry!

---

### Post by chili555 on 2011-10-11
In Classic Ubuntu look in Places > Home Folder. In Unity, open Files and Folders.

---

### Post by Mean Mr Mustard on 2011-10-11
> **chili555 said:**
> In Classic Ubuntu look in Places > Home Folder. In Unity, open Files and Folders.
I'm using ubuntu 11.04 and have located Holding Folder but what is Unity and where is it? -sorry.

---

### Post by gsocker on 2011-10-11
Slightly far shot, but this happened on another Ubuntu install and broke networking...

If /var/lib/NetworkManager/NetworkManager.state exists, could you post it? I know of one case where the network setting in this file somehow got marked disabled, and editing the file was the only way to fix the problem. This would explain why the device appears to be seen, but networkmanager keeps saying it's disabled.

---

### Post by Mean Mr Mustard on 2011-10-11
> **gsocker said:**
> Slightly far shot, but this happened on another Ubuntu install and broke networking...

If /var/lib/NetworkManager/NetworkManager.state exists, could you post it? I know of one case where the network setting in this file somehow got marked disabled, and editing the file was the only way to fix the problem. This would explain why the device appears to be seen, but networkmanager keeps saying it's disabled.
Whilst I am so grateful for any help with this you guys need to understand that I am VERY new to this.
Sorry but I dont understand this "If /var/lib/NetworkManager/NetworkManager.state exists"

---

### Post by gsocker on 2011-10-11
If this doesn't work, please let me know. I am not familiar with the Unity interface.
Find "Run Command". Type "gedit". Press enter.

When gedit starts, do file/open.
Press Ctrl-L. In the box that appears delete everything, then paste 
```
/var/lib/NetworkManager/NetworkManager.state
```

Click Open.
Copy and paste contents here.

---

### Post by Javelin Dan on 2011-10-11
Mean Mr. Mustard...Here's another possibility. Most of the newer versions of Ubuntu, Puppy Linux, etc. are being released to embrace ever newer hardware - doesn't mean the latest and greatest is best for your machine. All these hardware/software interfaces are very  equipment-operating system-version specific. What works well on one machine might not even work at all on another. Puppy Linux actually released a version called "Wary" because it's wary of newer equipment. This is the only distro that will run well on my ancient Dell Inspiron 8000 laptop {circa 1998}. Depending on how old your computer is (I've forgotten by now), you may actually want to back up a version or two and run the live CD just to see if it makes nice with your junk. I STILL think you're going to have to address your wireless card and get one that works with everything - my SMCWUSB-G NA flat out does. I later also replaced my old cranky D-Link wireless router with what else?..an SMC unit that just blew the D-Link out of the water! I can walk well into my neighbor's yard with my laptop and still have a 40%-50% signal. I know it sounds like I have stock in the company, but I don't. Take it from a total newb who has no skill with the command line and lives in the desktop environment - don't invest too much time on one single combination. Try something else and give yourself a life!

---

### Post by anewguy on 2011-10-11
Possible idea.  I think the OP should also do a search on the net using:

ubuntu rt2500usb

as the search string.  You may be surprised at some of the results.  Normally the default rt2500 driver has to be blacklisted, a new driver downloaded and made in order for it to try to work.

It also appears that many people have just gone with ndiswrapper to get it to work.  If you want to go that route post back and I can get you through that quite easily.

Keep in mind the clean install - it's hard to know what you've done along the way and what to try to undo.  A clean slate is usually the best way to start.  And either disable that on-board wireless or remove the other - yes it will mean opening your box.

If you want to post back again the exact maker/model/specs I can try looking for tech support to see if/how to disable that on-board adapter.

I would prefer, however, if we just get it working.

If 2 adapters is a requisite for you, we still need to start with only 1 installed and a clean slate, get it working first, then try adding the 2nd card.  Having both installed while you're trying to get this working is a very bad idea.

Dave ;)

---

### Post by anewguy on 2011-10-11
> **Mean Mr Mustard said:**
> Dave...The ONLY card I am confident of removing is the one I very recently fitted myself.The original onboard RT2500usb card is the one that I will leave alone then. Its just that I feel as if I am going around in circles with this? As for ubuntu, what do you mean by a LiveCD please?
 
As for why two Cards..no special reason other than an attempt to have one that would work in ubuntu and I am  not expert enough to remove original RT2500usb card without probably creating even more problems!
 
I will be back!

Yep - use the LiveCD to reinstall Ubuntu.  Let's just remove the other card and work only with the rt2500usb for now.  And please keep in mind reinstalling Ubuntu - remembering to format the partitions - so we have a clean slate to work with.  When you have done that don't add anything, don't mess with any drivers, etc., and just post back.

BTW - I forgot to ask - did you install this as dual-boot, or as an "in-Windows" wubi installation?  This can make quite a difference as well, and it is highly recommended to put Ubuntu in it's own partition(s) and use dual boot.  Wubi is really just for test drive of Ubuntu.

Dave ;)

---

### Post by Mean Mr Mustard on 2011-10-12
> **gsocker said:**
> If this doesn't work, please let me know. I am not familiar with the Unity interface.
Find "Run Command". Type "gedit". Press enter.

When gedit starts, do file/open.
Press Ctrl-L. In the box that appears delete everything, then paste 
```
/var/lib/NetworkManager/NetworkManager.state
```

Click Open.
Copy and paste contents here.
Where do I find "Run Command" - sorry.

---

### Post by Mean Mr Mustard on 2011-10-12
> **anewguy said:**
> Yep - use the LiveCD to reinstall Ubuntu.  Let's just remove the other card and work only with the rt2500usb for now.  And please keep in mind reinstalling Ubuntu - remembering to format the partitions - so we have a clean slate to work with.  When you have done that don't add anything, don't mess with any drivers, etc., and just post back.

BTW - I forgot to ask - did you install this as dual-boot, or as an "in-Windows" wubi installation?  This can make quite a difference as well, and it is highly recommended to put Ubuntu in it's own partition(s) and use dual boot.  Wubi is really just for test drive of Ubuntu.

Dave ;)
Please explain what you mean by "LiveCD" - thank you.
 
Also I did use "wubi"  to install  11.04 along side XP to create dual boot system. When I fire up PC now I have the option to select XP or ubuntu.

---

### Post by anewguy on 2011-10-12
That changes everything!  wubi really isn't meant for running normally - just to take ubuntu for a test drive.  The "LiveCD" is the image you downloaded of ubuntu and then burned to a CD - the installation medium.  If you used USB instead of CD, use that USB stick.

However, since it's a wubi install currently, we will probably have to address the partitioning as well.

If I might suggest, even though it doesn't provide the instant fix to your wireless, you may want to read some of the information about being new to ubuntu in the stickies at the top of the forum.  You should also be familiar with partitioning, what a normal partition is versus extended, the limitations, etc..

I know that's not the answer you want to hear - you just want your wireless working.  Unfortunately it is probably going to require a step or 2 backwards before we can try to go forward.

Dave ;)

---

### Post by anewguy on 2011-10-12
I did find an old post about getting the rt2500usb working in a wubi install using ndiswrapper.  So.....please take the following steps:

[LIST]
[*]If you installed the "normal" ubuntu from the download - e.g. you didn't install the 64 bit version, the you need to get the Windows XP drivers for the device.  These would be the .inf and .sys files that your Windows XP installation is using.  Copy the .inf and .sys files to your ubuntu desktop
[*]Boot up ubuntu
[*]After ubuntu is running, place the LiveCD in your CD drive.  DO NOT REBOOT.
[*]Using the navigator "Places", explore the LiveCD and find the /pool/main/n folder.  You will see 2 subfolders there - ndisgtk and ndiswrapper.
[*]Go to the ndiswrapper folder first.
[*]Double-click on the ndiswrapper-common and let it install.
[*]Double-click on the ndiswrapper-utilities and let it install.
[*]Go back 1 folder to /pool/main/n
[*]Go to the ndisgtk folder
[*]Double click on the ndisgtk file and let it install.
[*]Open a terminal window - applications/accessories/terminal
[*]Type:  sudo rmmod rt2500pci <press enter>
[*]Type: sudo rmmod rt2500usb
[*]Type: sudo gedit /etc/modprobe.d/blacklist.conf 
[*]Go to the end of the file and add 3 lines: rt2500  rt2500pci  rt2500usb
[*]Save the file and exit the editor
[*]Go to System/Administration/Windows Drivers - this will start up ndisgtk, the graphical front-end to ndiswrapper.
[*]Select new, then point it to the Windows driver .inf file - if you followed my suggestion above it would be ~/Desktop/xxxxx.inf (where xxxxx is the driver file name)
[*]Close out from ndisgtk
[*]Now reboot.
[/LIST]
Now check under the network manager icon (the thing that looks like radio waves going up) and be sure "Enable Wireless" is checked and enabled - if not, enable it.

Left-click on the network manager and see if any wireless networks show now.

You can do this in wubi without a reinstall of ubuntu.

Dave ;)

---

### Post by Mean Mr Mustard on 2011-10-12
> **anewguy said:**
> I did find an old post about getting the rt2500usb working in a wubi install using ndiswrapper. So.....please take the following steps:

[LIST]
[*]If you installed the "normal" ubuntu from the download - e.g. you didn't install the 64 bit version, the you need to get the Windows XP drivers for the device. These would be the .inf and .sys files that your Windows XP installation is using. Copy the .inf and .sys files to your ubuntu desktop
[*]Boot up ubuntu
[*]After ubuntu is running, place the LiveCD in your CD drive. DO NOT REBOOT.
[*]Using the navigator "Places", explore the LiveCD and find the /pool/main/n folder. You will see 2 subfolders there - ndisgtk and ndiswrapper.
[*]Go to the ndiswrapper folder first.
[*]Double-click on the ndiswrapper-common and let it install.
[*]Double-click on the ndiswrapper-utilities and let it install.
[*]Go back 1 folder to /pool/main/n
[*]Go to the ndisgtk folder
[*]Double click on the ndisgtk file and let it install.
[*]Open a terminal window - applications/accessories/terminal
[*]Type: sudo rmmod rt2500pci <press enter>
[*]Type: sudo rmmod rt2500usb
[*]Type: sudo gedit /etc/modprobe.d/blacklist.conf
[*]Go to the end of the file and add 3 lines: rt2500 rt2500pci rt2500usb
[*]Save the file and exit the editor
[*]Go to System/Administration/Windows Drivers - this will start up ndisgtk, the graphical front-end to ndiswrapper.
[*]Select new, then point it to the Windows driver .inf file - if you followed my suggestion above it would be ~/Desktop/xxxxx.inf (where xxxxx is the driver file name)
[*]Close out from ndisgtk
[*]Now reboot.
[/LIST]if you installed the "normal" ubuntu from the download - e.
 
Now check under the network manager icon (the thing that looks like radio waves going up) and be sure "Enable Wireless" is checked and enabled - if not, enable it.
 
Left-click on the network manager and see if any wireless networks show now.
 
You can do this in wubi without a reinstall of ubuntu.
 
Dave ;)
 
 
Well I just can't believe it...My internal card is now working!!!!! FANTASTIC. Thank you so much.
 
The icon at the top right for wireless is now radiating away, I just cant believe it?
 
Amazing!
 
But the Authentication required by wireless network keeps popping up AND I cant seem to get onto internet?
 
I new it couldn't last...Just fired up PC into ubuntu and NO wireless connection!! 
 
All wireless cards and Enable Wirelss greyed out!
 
 HELP.

---

### Post by Javelin Dan on 2011-10-12
It is asking you for the password you recorded when you first installed Ubuntu. It's a security thing. You will be asked for this every time you try to do any administrational task, or any time you boot up and try to connect wirelessly. You can disable this function, but it's recomended you don't so someone would have a harder time hacking into your network. For wireless security, it's also recomended to configure your wireless router for WPA encription if possible and not already done.
 
I've been where you are (very recently in fact), and it's no fun. You feel clueless because you're having a lot of strange stuff thrown at you all at once and unfortunately, too many people on these forums insist on assuming a certain skill level you don't yet have (you will) and insist on talking over your head. Please go to [www.ubuntupocketguide.com]("http://www.ubuntupocketguide.com"). Download the PDF file and use it to familiarize yourself with a few of these "Linux mysteries". Also go to Amazon and search for a book called "Beginning Ubuntu Linux" by Thomas,Channelle, & Sicam. They have gently used copies for as little as $8.00 (US). I've found it extrememly valuable in breaking through the fog. Good luck!

---

### Post by anewguy on 2011-10-12
> **Mean Mr Mustard said:**
> Well I just can't believe it...My internal card is now working!!!!! FANTASTIC. Thank you so much.
 
The icon at the top right for wireless is now radiating away, I just cant believe it?
 
Amazing!
 
But the Authentication required by wireless network keeps popping up AND I cant seem to get onto internet?
 
I new it couldn't last...Just fired up PC into ubuntu and NO wireless connection!! 
 
All wireless cards and Enable Wirelss greyed out!
 
 HELP.

I *think* I forgot 1 piece of the puzzle that would allow this to work.  We need to tell the system to load ndiswrapper each time it starts up.  I thought ndisgtk normally took care of this.  To test this theory:

- open a terminal window (applications/accessories/terminal)

- type:  sudo modprobe ndiswrapper <press enter>

- close the terminal window

- wait a few minutes and see if your wireless "wakes up"

If this works:

- open a terminal window (applications/accessories/terminal)

- type:  sudo gedit /etc/modules <press enter>

- go to the end of the file and add a line that says:

ndiswrapper

- save the file
- exit the editor
- close the terminal window
- REBOOT

See if the wireless comes back up after the boot.

Please post back any and all questions/comments/etc..  BTW - nobody here should worry about feeling "stupid" - this is the beginners forum.  Heck I still ask a lot of questions here myself.  As far as people not understanding a post because someone thinks you have more knowledge than you do - NEVER BE AFRAID TO ASK A QUESTION.  Most of us have been where you are - after all, we were all "new" at some point in time.  If you don't understand an answer or what someone is wanting you to do, just post back asking for clearer step-by-step instructions.  They might not be immediate, but they will show up.

As far as the password thing is concerned:  does it say it is asking for a keyring password, or is it showing a screen asking for the network password?  I assume you mean the network password.  There are a couple of possibilities here:

- the network is a "hidden" network - it's not broadcasting it's SSID (the name that would show in the list of available networks).  In such cases, you must open network manager and click on the link to manually specify the connection. 

- you specified manually in network manager what to connect to, etc..  If any attempt is made this way and is found to be in error, you need to open network manager and use "Edit Connections" and remove the network, then manually describe it again with the correct information.  I've seen too many times where the old description wasn't removed before a new attempt, and it results in the connection attempt being rejected - normally with the box back asking for the network password/passphrase again.

- the encryption type isn't matching (do you know if the router you connect to requires WEP, WPA or WPA2 encryption?)

- perhaps, but doubtful, the Windows driver being used doesn't support the encryption type specified on the router

- the password/passphrase you are entering doesn't match that on the router you are trying to connect to

- MAC filtering enabled on the router and the wireless adapters' MAC address is not in the router table.  Since you have connected with Windows before, I will assume it's the same network you are trying to connect to, so this probably shouldn't apply.



Dave ;)

---

### Post by anewguy on 2011-10-12
> **Javelin Dan said:**
> It is asking you for the password you recorded when you first installed Ubuntu. It's a security thing. You will be asked for this every time you try to do any administrational task, or any time you boot up and try to connect wirelessly. You can disable this function, but it's recomended you don't so someone would have a harder time hacking into your network. For wireless security, it's also recomended to configure your wireless router for WPA encription if possible and not already done.
 
I've been where you are (very recently in fact), and it's no fun. You feel clueless because you're having a lot of strange stuff thrown at you all at once and unfortunately, too many people on these forums insist on assuming a certain skill level you don't yet have (you will) and insist on talking over your head. Please go to [www.ubuntupocketguide.com]("http://www.ubuntupocketguide.com"). Download the PDF file and use it to familiarize yourself with a few of these "Linux mysteries". Also go to Amazon and search for a book called "Beginning Ubuntu Linux" by Thomas,Channelle, & Sicam. They have gently used copies for as little as $8.00 (US). I've found it extrememly valuable in breaking through the fog. Good luck!

Please keep the following in mind:

- nobody had asked the OP if the password being asked for was the keyring password (what you are thinking of) or the network password/passphrase (from the access point - in this case the router).  So please don't just post that they should use their logon password, which is what it sounds like you mean - you would need to clarify that in your post. The network password/passphrase would never have been setup anytime by installing ubuntu.  It's a router setup thing, not an ubuntu installation thing.  It's just not that simple.  In prior releases you could even set your keyring password to what ever you wanted, so even your suggestion wouldn't work then.  Remember, ask for detail before assuming.

- if you or anyone else has problems understanding a post and what is talked about in it, just post back asking for a simple explanation and simple instructions.  Sometimes it is easy to assume someone knows more than they do - it's only natural after replying on the forum for a long time.  Most posters won't mind a request for simplification, even if it means simple step-by-step instructions.  It may take a while, but someone will post something in a way you can follow.


Dave ;)

---

### Post by Mean Mr Mustard on 2011-10-12
> **Javelin Dan said:**
> It is asking you for the password you recorded when you first installed Ubuntu. It's a security thing. You will be asked for this every time you try to do any administrational task, or any time you boot up and try to connect wirelessly. You can disable this function, but it's recomended you don't so someone would have a harder time hacking into your network. For wireless security, it's also recomended to configure your wireless router for WPA encription if possible and not already done.
 
I've been where you are (very recently in fact), and it's no fun. You feel clueless because you're having a lot of strange stuff thrown at you all at once and unfortunately, too many people on these forums insist on assuming a certain skill level you don't yet have (you will) and insist on talking over your head. Please go to [www.ubuntupocketguide.com]("http://www.ubuntupocketguide.com"). Download the PDF file and use it to familiarize yourself with a few of these "Linux mysteries". Also go to Amazon and search for a book called "Beginning Ubuntu Linux" by Thomas,Channelle, & Sicam. They have gently used copies for as little as $8.00 (US). I've found it extrememly valuable in breaking through the fog. Good luck!
Thanks for the reply but I know its asking me for the key my router requires to allow access to internet. The problem being that after I have entered "the key" and pressed the button it disappears as you would expect only to return about 10 secs later which is annoying! All of this is by the way at the moment because I am having a problem getting my wireless connection to spring back to life.

---

### Post by Mean Mr Mustard on 2011-10-12
> **anewguy said:**
> I *think* I forgot 1 piece of the puzzle that would allow this to work. We need to tell the system to load ndiswrapper each time it starts up. I thought ndisgtk normally took care of this. To test this theory:
 
- open a terminal window (applications/accessories/terminal)
 
- type: sudo modprobe ndiswrapper <press enter>
 
- close the terminal window
 
- wait a few minutes and see if your wireless "wakes up"
 
If this works:
 
- open a terminal window (applications/accessories/terminal)
 
- type: sudo gedit /etc/modules <press enter>
 
- go to the end of the file and add a line that says:
 
ndiswrapper
 
- save the file
- exit the editor
- close the terminal window
- REBOOT
 
See if the wireless comes back up after the boot.
 
Please post back any and all questions/comments/etc.. BTW - nobody here should worry about feeling "stupid" - this is the beginners forum. Heck I still ask a lot of questions here myself. As far as people not understanding a post because someone thinks you have more knowledge than you do - NEVER BE AFRAID TO ASK A QUESTION. Most of us have been where you are - after all, we were all "new" at some point in time. If you don't understand an answer or what someone is wanting you to do, just post back asking for clearer step-by-step instructions. They might not be immediate, but they will show up.
 
As far as the password thing is concerned: does it say it is asking for a keyring password, or is it showing a screen asking for the network password? I assume you mean the network password. There are a couple of possibilities here:
 
- the network is a "hidden" network - it's not broadcasting it's SSID (the name that would show in the list of available networks). In such cases, you must open network manager and click on the link to manually specify the connection. 
 
- you specified manually in network manager what to connect to, etc.. If any attempt is made this way and is found to be in error, you need to open network manager and use "Edit Connections" and remove the network, then manually describe it again with the correct information. I've seen too many times where the old description wasn't removed before a new attempt, and it results in the connection attempt being rejected - normally with the box back asking for the network password/passphrase again.
 
- the encryption type isn't matching (do you know if the router you connect to requires WEP, WPA or WPA2 encryption?)
 
- perhaps, but doubtful, the Windows driver being used doesn't support the encryption type specified on the router
 
- the password/passphrase you are entering doesn't match that on the router you are trying to connect to
 
- MAC filtering enabled on the router and the wireless adapters' MAC address is not in the router table. Since you have connected with Windows before, I will assume it's the same network you are trying to connect to, so this probably shouldn't apply.
 
 
 
Dave ;)
Nothings happening RE: I *think* I forgot 1 piece of the puzzle that would allow this to work. A I think I "messed up" Termial file as per post 69 as I didn't SAVE FILE! I don't know how to!!!! This might explain why wireless connection went dead after rebooted PC
 
When I open a Terminal and punch in this my wireless connection springs into life:-
 
mike@ubuntu:~$ sudo rmmod rt2500usb 
[sudo] password for mike: 
mike@ubuntu:~$ 
 
 
How do I save this file? ALSO Authentification Required by wireless network is now periodically popping up despite me entering "router key" info?
 
AND...Router encryption is WPA2, "Authetification Required" that pops up in ubuntu shows "WPA & WPA2 Personal" is this correct? and invites you to press "Connect Button".
 
Wireless connection has just gone dead!!!!!!!!!!

---

### Post by Lisiano on 2011-10-12
Type this in a terminal (Ctrl+Alt+T)
```
gksudo gedit /etc/modprobe.d/blacklist.conf
```
Then add those lines
```
rt2500
rt2500pci
rt2500usb
```
Now either look at the top left corner and press File -> Save OR press Ctrl+S. Now you can close Gedit.

Note: Don't use sudo on programs that have windows (A GUI) to avoid future problems. Basically stuff like the terminal, text editors, web browsers, etc.

For the WiFi password, it's good that it's asking for a WPA/WPA2 password. You probably either changed the password one day on the router and forgot or using the wrong one, to find the password you could use this tool on Windows XP
EDIT: I'll re-edit this post once I find a tool that gives the key in human-readable form


@Dave. The reason the OP has 2 cards is because we couldn't make his internal RT2500 work (We didn't try ndisswrapper) and he later purchased a AR5007G which for some magical reason, refused to work too.

@Dave a second time. Didn't say yet, but congrats on getting the Ubuntu member! A cake is in order! 
VGhlIGNha2UgaXMgYSBsaWUuCg==
VGhlIGNha2UgaXMgYSBsaWUuCg==
VGhlIGNha2UgaXMgYSBsaWUuCg==
VGhlIGNha2UgaXMgYSBsaWUuCg==

---

### Post by anewguy on 2011-10-12
> **Lisiano said:**
> Type this in a terminal (Ctrl+Alt+T)
```
gksudo gedit /etc/modprobe.d/blacklist.conf
```
Then add those lines
```
rt2500
rt2500pci
rt2500usb
```
Now either look at the top left corner and press File -> Save OR press Ctrl+S. Now you can close Gedit.

Note: Don't use sudo on programs that have windows (A GUI) to avoid future problems. Basically stuff like the terminal, text editors, web browsers, etc.

For the WiFi password, it's good that it's asking for a WPA/WPA2 password. You probably either changed the password one day on the router and forgot or using the wrong one, to find the password you could use this tool on Windows XP
EDIT: I'll re-edit this post once I find a tool that gives the key in human-readable form


@Dave. The reason the OP has 2 cards is because we couldn't make his internal RT2500 work (We didn't try ndisswrapper) and he later purchased a AR5007G which for some magical reason, refused to work too.

@Dave a second time. Didn't say yet, but congrats on getting the Ubuntu member! A cake is in order! 
VGhlIGNha2UgaXMgYSBsaWUuCg==
VGhlIGNha2UgaXMgYSBsaWUuCg==
VGhlIGNha2UgaXMgYSBsaWUuCg==
VGhlIGNha2UgaXMgYSBsaWUuCg==

Thanks for helping him out on the editor question - I've been off sleeping.  I know about the gksudo thing and the warning that comes for people like me, but so far I've never had a problem, so you know what that means - I'll probably keep doing it out of habit and then someday get burned and learn my lesson the hard way ;) ;)

I did notice when I scanned the net that it seemed most were going back to ndiswrapper for the rt2500usb so I figured it was worth a shot.  If it keeps working that's great!  Sometimes I get lucky ;)

And.....thank you very much for the congrads!  I was honestly a little surprised that I got it but I'm sure glad I did.  I guess I must contribute a little something around here from time to time!  Again, thanks very much!

If you don't mind watching the thread for a little while, now that I'm awake again I've got some "serious" errands to run (okay, it's the munchies - jeez I must be having flashbacks or something lately!).

Dave ;)

EDIT:  Forgot - if the OP is on while I'm gone, could you walk him through the "Edit Connections" in network manager?  I know from past experience that if you get it wrong once it seems to always default back to that wrong entry instead of what you've just typed in the request box.  It can get very frustrating tracking that down if the person isn't aware that it happens.

EDIT-EDIT:  Also be sure ndiswrapper is in the /etc/modules file.  And of course - after making the changes just reboot right away - we'll know if the changes "took" or not right away that way.


Mean Mr Mustard:  yes, rmmod'ing the rt2500usb probably would bring it back to life, at least temporarily.  We should probably give you an explanation of what this is all doing - if there's something you don't understand please just ask.

Linux allows dynamic additions/removals of some pieces the kernel uses.  The kernel is really just the internals of Linux.  In this case, 1 or more pieces that are by default being loaded (we call them kernel modules or objects) - rt2500, rt2500pci and/or rt2500usb - don't really work for your adapter.  So the first thing we have to do is to tell ubuntu not to load those by default when it starts up.  The way of doing this is by adding them to a file - the /etc/modprobe.d/blacklist.conf file.  This file is aptly named, as it is a list of modules we don't want the kernel to load.  So when we have you do the edit of that file and add those 3 items to it it stops those drivers modules from loading.  This is very important as anything we might do afterwards would probably fail, behave strangely, etc., because of these things "stepping" on each other.

So, once the blacklisting is done those modules won't be loaded at boot so they won't interfere with what we are doing.

The sudo rmmod rt2500usb is telling ubuntu to remove this module (hence rmmod) from the current running ubuntu.  This is only valid until the next reboot - that's why the blacklist file is needed.

Similarly, you can ask ubuntu to load additional modules.  The command to load a module into a running ubuntu session is modprobe - so you would sudo modprobe ndiswrapper as an example to load up ndiswrapper.

Just as there is the blacklist file for modules we don't want loaded, there is the converse - the /etc/modules file.  This file is used to tell ubuntu additional modules we want loaded at boot.  So when we had you edit this file and add ndiswrapper it was because we need ndiswrapper loaded now.

So....

- the blacklist file updates stopped conflicting drivers from loading by default

- the modules file update force ndiswrapper to be loaded at boot

- ndiswrapper -> a way to use Windows XP wireless driver files in Linux when there is either no "native" linux driver, or, as in your case, those drivers don't work and you need to use the Windows drivers.

I hope that explains a little what all the gobbly-gook we've had you typing here lately is all about and what it is doing to help solve your problem.

---

### Post by Lisiano on 2011-10-12
@Dave Got it.

As for the WPA Key, since you are using Windows XP, you won't get the key in human-readable form so no use trying. BUT, we can still get the key. Download this little tool and just open it
~snip~
As you can see in the screenshot bellow, you need to find your WiFi network and copy the key into a text file somewhere you can later find, please don't post it as someone can then access your network.
~snip~
The password is in the "Key (HEX)" field. It will probably not look like the password on the back of your router but it is still usable. This is how Windows XP stores the password.
So let's say you have a network called Pineapple and a password "I love pineapples" then you will see a "Key (HEX)" of "6646ebc7bf6c4ed9a808a792a3a67d0ee8316cfe06b90ef17952ede37adcc02d" you need to copy it somewhere you can later find. Now let's go over to Network Manager  and change the password you tried earlier (The Network Manager is the icon that you called a fan), click it and go to Edit connections
[IMG]http://ubuntuone.com/5iOVo0uy98VqV9t3JMiwjY[/IMG]
Now open the Wireless tab, find your network and press Edit
[IMG]http://ubuntuone.com/1YB4z3QepYWGxpvc3kDWm8[/IMG]
Now another window will open and go to Wireless Security, make sure it says WPA & WPA2 Personal
[IMG]http://ubuntuone.com/2dlKpuDWGgXelwDb2Qnksm[/IMG]
Then copy paste the password we got from the tool earlier into the Password field, now press Save
[IMG]http://ubuntuone.com/08cHlmxmZDaxfV2eFlDTsr[/IMG]
And close the other window (Save first). Now press the Network Manager and click your network name, you should get connected.

Note: Pictures in a few minutes once I make em and send over to Ubuntu One.

---

### Post by Mean Mr Mustard on 2011-10-12
What do you mean by "add these lines"...how do I do that? Do I just press "enter" after each entry 
Like this
mike@ubuntu:~$ rt2500 then press &#8220;enter&#8221; and repeat for the other two? Is that what you mean?
 
ALSO can't find SAVE button in FILE

---

### Post by Mean Mr Mustard on 2011-10-12
> **Lisiano said:**
> @Dave Got it.
 
 
Please DON'T use that command. That command will turn the wireless OFF, until you either type ```
sudo ifconfig wlan0 up
``` OR ```
sudo ifup wlan0
```
 
As for the WPA Key, since you are using Windows XP, you won't get the key in human-readable form so no use trying. BUT, we can still get the key. Download this little tool and just open it
[http://www.nirsoft.net/utils/wirelesskeyview.zip](http://www.nirsoft.net/utils/wirelesskeyview.zip)
As you can see in the screenshot bellow, you need to find your WiFi network and copy the key into a text file somewhere you can later find, please don't post it as someone can then access your network.
[IMG]http://www.nirsoft.net/utils/wirelesskeyview.gif[/IMG]
The password is in the "Key (HEX)" field. It will probably not look like the password on the back of your router but it is still usable. This is how Windows XP stores the password.
So let's say you have a network called Pineapple and a password "I love pineapples" then you will see a "Key (HEX)" of "6646ebc7bf6c4ed9a808a792a3a67d0ee8316cfe06b90ef17952ede37adcc02d" you need to copy it somewhere you can later find. Now let's go over to Network Manager and change the password you tried earlier (The Network Manager is the icon that you called a fan), click it and go to Edit connections, now open the Wireless tab, find your network and press Edit, now another window will open and go to Wireless Security, make sure it says WPA & WPA2 Personal, then copy paste the password we got from the tool earlier into the Password field, now press Save and close the other window (Save first). Now press the Network Manager and click your network name, you should get connected.
 
Note: Pictures in a few minutes once I make em and send over to Ubuntu One.
Attempted to download "little tool" file as you suggested and got WARNING FILE INFECTED withTrojan horse Generic 24.COLV by my Anti Virus program! ALSO...I know what my network key is as its the same one I use in XP and that works just fine?

---

### Post by anewguy on 2011-10-12
> **Mean Mr Mustard said:**
> What do you mean by "add these lines"...how do I do that? Do just press "enter" after each entry 
Like this
mike@ubuntu:~$ rt2500 then press “enter” and repeat for the other two? Is that what you mean?

If you are talking about the editing of the file, then it's like using any editor or word processor:

- go to the end of the file - hold down the control key (ctrl) and press the "end" key

- press enter a couple of times

- type in:

rt2500 <press enter>
rt2500pci <press enter>
rt2500usb <press enter>

This adds 3 lines - 1 for each of the modules.

Be sure to save the file when you are done! ;)  If you have any questions, Lisiano should be here for a while to help you out.  In the mean time, I really got to run on that munchies thing ;)

Dave ;)

---

### Post by anewguy on 2011-10-12
> **Mean Mr Mustard said:**
> Attempted to download "little tool" file as you suggested and got WARNING FILE INFECTED withTrojan horse Generic 24.COLV by my Anti Virus program! ALSO...I know what my network key is as its the same one I use in XP and that works just fine?

If you are absolutely certain of your network key, then I would think you'll need to do the "Edit Connections" in network manager and remove anything that shows there.

Dave ;)

- really, I'm leaving now! ;)

---

### Post by Lisiano on 2011-10-12
[IMG]http://ubuntuone.com/1EG4xt34aYtxDOfXReGkN1[/IMG]
Make it look like so then press the Save button I'm hovering with my mouse.

As for the trojan, it's a false positive
[http://www.virustotal.com/file-scan/report.html?id=3b7db83cd2093f2e8ad1a69725119f7cdf39e62fec28e804b5c679bbdcab35c9-1318450497](http://www.virustotal.com/file-scan/report.html?id=3b7db83cd2093f2e8ad1a69725119f7cdf39e62fec28e804b5c679bbdcab35c9-1318450497)
Notice the rating Goodware (Means the file might contain some code that anti-viruses consider viruses but it's used there to do what the tool does, no need for alarm in other words) Currently as I'm  typing it's already done analysing.

All tools that can extract information out of Windows are most of the times classified as HackTool/Virus/Trojan. There is no need to worry as if I did send you a virus, Dave probably would've already sicked the admins on me.

Edit: Still don't believe me? [NirSoft]("http://www.nirsoft.net/") is a known company that makes tools for recovery of passwords, network debugging, information gathering, etc.

Edit 2: [Pictures are up.]("http://ubuntuforums.org/showpost.php?p=11334925&postcount=78")

---

### Post by anewguy on 2011-10-12
> **Lisiano said:**
> [IMG]http://ubuntuone.com/1EG4xt34aYtxDOfXReGkN1[/IMG]
Make it look like so then press the Save button I'm hovering with my mouse.

As for the trojan, it's a false positive
[http://www.virustotal.com/file-scan/report.html?id=3b7db83cd2093f2e8ad1a69725119f7cdf39e62fec28e804b5c679bbdcab35c9-1318450497](http://www.virustotal.com/file-scan/report.html?id=3b7db83cd2093f2e8ad1a69725119f7cdf39e62fec28e804b5c679bbdcab35c9-1318450497)
Notice the rating Goodware (Means the file might contain some code that anti-viruses consider viruses but it's used there to do what the tool does, no need for alarm in other words) Currently as I'm  typing it's already done analysing.

All tools that can extract information out of Windows are most of the times classified as HackTool/Virus/Trojan. There is no need to worry as if I did send you a virus, Dave probably would've already sicked the admins on me.

Virus? Trojan?  Hummmm.....Linux sounds even better, eh?  ;)

I fight this all the time with my parents who live 2000 miles from here.  I set everything up for them, but being 80 they just don't really understand, so they don't understand keeping things up to date and being sure to scan anything that they download, etc..  The end result is usually several frustrating hours on the phone walking them through fixing it!

and YES - I'm DEFINITELY leaving now!! ;) ;)

As for the OP's latest post about adding the lines - I noticed his example he is typing at the command line, not in a file being edited.  If you could be sure he actually edits the file it would be appreciated!

Thanks again for helping him out!

Dave ;)

---

### Post by Lisiano on 2011-10-12
@Dave, SHO. Don't reply in the near hour.

@Mr. Mustard.
You should type this in a console
```
gksudo gedit /etc/modprobe.d/blacklist.conf
```
A window will pop up asking for your password, give it.
Now the program in the picture will open and you should put the lines like I did at the end of the file. Then press Save.

---

### Post by Mean Mr Mustard on 2011-10-12
> **Lisiano said:**
> @Dave, SHO. Don't reply in the near hour.

@Mr. Mustard.
You should type this in a console
```
gksudo gedit /etc/modprobe.d/blacklist.conf
```
A window will pop up asking for your password, give it.
Now the program in the picture will open and you should put the lines like I did at the end of the file. Then press Save.
Whats a console- sorry. This is frustrating for me too!

---

### Post by Lisiano on 2011-10-12
Sorry. I meant Terminal (Ctrl+Atl+T)

---

### Post by Mean Mr Mustard on 2011-10-12
> **Lisiano said:**
> @Dave, SHO. Don't reply in the near hour.

@Mr. Mustard.
You should type this in a console
```
gksudo gedit /etc/modprobe.d/blacklist.conf
```
A window will pop up asking for your password, give it.
Now the program in the picture will open and you should put the lines like I did at the end of the file. Then press Save.
[code] Done all that you said...wireless connectionstill greyed out? [code]

---

### Post by Lisiano on 2011-10-12
As Dave suggested, it's good practice to reboot to see if the changes we make are working, once you reboot it should become alive again, if you want to do this without rebooting you will have to do these steps again
[LIST]
[*]Type: sudo rmmod rt2500pci <press enter>
[*]Type: sudo rmmod rt2500usb <press enter>
[*]Type: sudo rmmod rt2500 <press enter>
[/LIST]
And it should start up again.

As Dave said, if you want to know what these commands do or think we are going over your head, ask us to explain them or to simplify them. We tend to forget someones experience level if we try to tackle more than 1 thread. Usually (Or at least I do) we assume that the person knows what a Terminal is and how to type some basic commands.

EDIT: Just noticed a edit Dave made, could you also post what the Terminal (Ctrl+Alt+T) tells you if you type this?
```
cat /etc/modules
```

---

### Post by Mean Mr Mustard on 2011-10-12
It is with enormous pleasure that I am able to confirm that my wirelss card IS WORKING and I CAN GET ON THE INTERNET!!!!! AND It is not tripping out. I just rebooted after the last saga after disabling the AR500G card and hey presto! my card rt2500usb roared into life!!!!
 
:KS:KS:KS:KS:KS THANK YOU THANK YOU THANK YOU ALL for your patience...I know how frustrating it WAS.

---

### Post by Lisiano on 2011-10-12
Thank Chili for the diagnostic work, Dave for finding and explaining how to do it using ndisswrapper and uhh... Me for simplifying it I guess.

Anyway, if you have ANY questions at all, just post here. If not then please mark the thread as solved using the Thread Tools on top of this page.

Have fun with Ubuntu.

---

### Post by Mean Mr Mustard on 2011-10-12
> **Lisiano said:**
> Thank Chili for the diagnostic work, Dave for finding and explaining how to do it using ndisswrapper and uhh... Me for simplifying it I guess.

Anyway, if you have ANY questions at all, just post here. If not then please mark the thread as solved using the Thread Tools on top of this page.

Have fun with Ubuntu.
Already have done the thanks to chili555  and Dave . You guys are AMAZING!

---

### Post by anewguy on 2011-10-12
Just glad we could get it working for you!  And you may not realize it, but as time goes by (and not really that much, BTW), you will find yourself in a position to answer some questions.  Now that you have this thread for reference you can answer if someone wants to know how to get the rt2500usb working!  So, when the time comes, just play it forward......that's how this forum was built and how it continues to grow.

Lisiano:  thanks for pitch-hitting for me while I was out.  I'm glad we got this solved for the OP!  ;)


Dave ;)

---

