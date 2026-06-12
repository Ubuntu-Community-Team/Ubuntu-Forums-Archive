---
title: "Wireless just wont seem to work"
date: 2008-08-02
forum: Networking &amp; Wireless
---

### Post by Eagle8708 on 2008-08-02
I have a Netgear WN511t Wireless card connecting to a wireless N router. For some reason, I cannot get wireless to work. There is not even an option for wireless in my network manager, any help is appreciated. Once i get wireless to work, this is going to be my main operating system. here is the info that I know to get. I am hooked to a Ethernet cable right now.

This is my lshw -C network
  *-network               
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 01
       serial: 00:0d:56:e8:a3:cb
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 ip=192.168.1.6 latency=32 module=ssb multicast=yes
  *-network UNCLAIMED
       description: Ethernet controller
       product: Marvell Technology Group Ltd.
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 03
       width: 32 bits
       clock: 66MHz
       capabilities: cap_list
       configuration: latency=0

My iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

And my ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0d:56:e8:a3:cb  
          inet addr:192.168.1.6  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2826 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2423 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3093420 (2.9 MB)  TX bytes:405377 (395.8 KB)
          Interrupt:7 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:40 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2000 (1.9 KB)  TX bytes:2000 (1.9 KB)

I have installed and did everything i could think of with NDIS wrapper... any other suggestions is welcomed

---

### Post by jualin on 2008-08-02
Check #48 in the [Ndiswrapper card list]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_m-n/") website

---

### Post by jualin on 2008-08-02
To make sure that #49 applies to you, post the results of > lsusb
lspcmcia when you write it on the terminal. You can check my signature for help on Ndiswrapper.

---

### Post by Eagle8708 on 2008-08-02
Its the number 48 one i am using the newest drivers...think that can make a difference?

lsusb is
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 046d:c01b Logitech, Inc. MX310 Optical Mouse
Bus 001 Device 001: ID 0000:0000 

lspcmcia is
Socket 0 Bridge:   	[yenta_cardbus] 	(bus ID: 0000:02:04.0)
  CardBus card -- see "lspci" for more information

---

### Post by Eagle8708 on 2008-08-02
LSPCI is

00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 02)
02:01.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
02:04.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
03:00.0 Ethernet controller: Marvell Technology Group Ltd. Unknown device 2a02 (rev 03)

---

### Post by jualin on 2008-08-02
So you are using the PCMCIA one?

---

### Post by jualin on 2008-08-02
Try installing the driver supplied on the [Ndiswrapper website]("http://firmware.netgear-forum.com/index.php?dlfile=705"). Maybe that will help you. However the card is not showing with the lspcmcia command. What have you tried so far to make the card work?

---

### Post by Eagle8708 on 2008-08-02
Right, its a PCMIA WN511T

I followed the instructions on [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#Automatically%20loading%20at%20start-up](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#Automatically%20loading%20at%20start-up) 

to the best of my abilities.

I have the drivers installed and the NDISWrapper interface says they were installed..

---

### Post by jualin on 2008-08-02
Try running > sudo ndiswrapper -l on the terminal. Download the driver from [the Netgear Website]("http://firmware.netgear-forum.com/index.php?dlfile=705") suggested in #48 and then let me know when you are done to try installing this new driver.

---

### Post by jualin on 2008-08-02
Remember that we need to remove the driver first > sudo ndiswrapper -e <driver name>, and then install the new driver that you just downloaded from the Netgear website that I mentioned.

---

### Post by Eagle8708 on 2008-08-02
Installing the driver that is suggested from NDIS wrapper i dont belive is possible...there is no INF file in that exe, i did a cabextract and it only had
 extracting Disk1/_isuser.dll
  extracting Disk1/ikernel.ex_
  extracting Disk1/data1.hdr
  extracting Disk1/data1.cab
  extracting Disk1/data2.cab
  extracting Disk1/Setup.exe
  extracting Disk1/Setup.ini
  extracting Disk1/Setup.inx
  extracting Disk1/layout.bin

in it.

Also the NDIS wrapper driver is uninstalled

---

### Post by jualin on 2008-08-02
I am running on a Windows machine right now so I will be able to install the driver on my system and send you a link with the .inf files. I am doing it right now, just a second.

---

### Post by jualin on 2008-08-02
Got it, I uploaded to [Media Fire]("http://www.mediafire.com/?jm9ebgonuju"). I am not sure if those were the correct .inf files, but you can give it a try. Hope it works!

---

### Post by jualin on 2008-08-02
Don't forget to post the results of > sudo ndiswrapper -l
********the "l" is a lower case **L**********

---

### Post by Eagle8708 on 2008-08-02
Success!!!

Thank you very much for you help. 
That was my main problem!

The connection seems to be a bit slower. but other than that it works!

---

### Post by jualin on 2008-08-02
Glad it worked. Welcome to the family!

---

### Post by jualin on 2008-08-02
> **Eagle8708 said:**
> Success!!!

Thank you very much for you help. 
That was my main problem!

The connection seems to be a bit slower. but other than that it works!

If the connection feels a little slower it may be because of IPv6 in Firefox, you can disable this in Firefox by writing > about:config on the Address bar (where you type the web address) and then search for "IPV6" and toggle the value from "false" to "true".

---

