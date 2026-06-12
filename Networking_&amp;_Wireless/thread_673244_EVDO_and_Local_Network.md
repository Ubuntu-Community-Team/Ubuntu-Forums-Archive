---
title: "EVDO and Local Network"
date: 2008-01-20
forum: Networking &amp; Wireless
---

### Post by shawnjones on 2008-01-20
Hello everyone,

I have a Dell Inspiron 9300 with Intel 2200 for wireless, I also have a Verizon EVDO "Aircard" for internet access. I've had the Intel card working before but after I installed the aircard it knocks out the local wireless. If I activate the wireless connection, I loose the internet connection, if I try to run wvdial again, it says device or resource busy. Has anyone had this problem. 

The reason for this is I have a server in the house that handles all of my music and video files. I access the server via SSH to transfer files back and forth on the class "C" net. I use the aircard to access the internet because there is no ISP in the area that I live. Here are some details:

Dell Inspiron 9300
Dual boot XP/Ubuntu 7.10 
PCMCIA Aircard
Mini-PCI internal wireless

The aircard shows as ttyACM0 in dmesg, here is a look:

[ 3238.832000] ohci_hcd 0000:04:00.1: irq 17, io mem 0x54001000
[ 3238.916000] usb usb7: configuration #1 chosen from 1 choice
[ 3238.916000] hub 7-0:1.0: USB hub found
[ 3238.916000] hub 7-0:1.0: 1 port detected
[ 3241.320000] usb 6-1: new full speed USB device using ohci_hcd and address 2
[ 3241.532000] usb 6-1: configuration #1 chosen from 1 choice
[ 3241.536000] cdc_acm 6-1:1.0: ttyACM0: USB ACM device
[ 3241.544000] airprime 6-1:1.2: airprime converter detected
[ 3241.544000] usb 6-1: airprime converter now attached to ttyUSB0
[ 3241.544000] usb 6-1: airprime converter now attached to ttyUSB1
[ 3241.544000] usb 6-1: airprime converter now attached to ttyUSB2

Thanks in advance,
Shawn

---

