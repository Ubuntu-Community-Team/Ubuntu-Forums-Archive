---
title: "Trouble with networking"
date: 2007-11-05
forum: Networking &amp; Wireless
---

### Post by pcd927 on 2007-11-05
Hi
Im kind of new to linux i used it before but didnt really stay long on it. But now I'm dual booting Windowes vista ultimate and ubuntu 7.10.

I have a  [Compaq Presario C555NR Notebook PC]("http://search.hp.com/query.html?hpvc=HHOall&hpl=0&sw=1&charset=iso-8859-1&lk=1&la=en&nh=10&st=1&rf=0&qp=url%3Ahttp&qs=&qt=c555nr&h_audience=hho&hps=Home+%26+Home+Office&hpr=http%3A//www.shopping.hp.com/webapp/shopping/home.do&h_audiencerestrict=&hph=&hpo=hphqhhomktg&hpn=Return+to+Home+%26+Home+Office&hpl=0&hpa=http%3A//www.homeandoffice.hp.com/hho/us/en/contact_hp.html&uf=1") And i dont know if you can see on the pictures or not but it has a blue LCD that tells that the network is turned on. When i boot into windows vista the light is on. However, when i boot into ubuntu it turns off. I did see that is was on once but never after that. I also noticed that after i followed the totorial on this forums, [HOWTO: Broadcom 43xx based wireless cards the EASY way.]("http://ubuntuforums.org/showthread.php?t=405990"), i went to click on the networking panal on the top right hand corner that it only showed wired networking. Before i followed the tutorial there was also a wireless section. I think that i had a problem during installation because every time i boot into Ubuntu some "error" messages are shown that Ubuntu couldn't load some things(I'll update the post later saying exactly what it says.)


Here are my computers specifications

 Processor, Memory, and Motherboard

    * Hardware Platform: PC
    * Processor: 1.6 Mobile Intel Celeron Processor
    * Number of Processors: 1
    * RAM: 512 MB
    * RAM Type: DDR2 SDRAM

Hard Drive

    * Size: 80 GB
    * Type: Serial ATA

Cases and Expandability

    * Size (LWH): 14.1 inches, 10.2 inches, 1.38 inches
    * Weight: 6.6 pounds

Wireless

    * Wireless Type: Broadcom Wireless LAN 802.11B(I'm not sure what the exact model number is)

Thank you, in advance

---

### Post by elctb on 2007-11-05
First you need to find out which wireless controller you have. You can use the command "lspci" to find out.

Then you need to load the right driver. sudo modprobe <driver>.
Verify a wireless interface is created with the "iwconfig" command.

---

### Post by pcd927 on 2007-11-05
I did the lspci code and i got this, in which i couldnt find the model of my wireless controller

gutsy00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03) 
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03) 
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03) 
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01) 
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01) 
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01) 
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01) 
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01) 
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01) 
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01) 
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1) 
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01) 
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01) 
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 01) 
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01) 
06:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01) 
08:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

---

### Post by pcd927 on 2007-11-05
Ok i got the model number i jusst can't find the drivers

---

### Post by pcd927 on 2007-11-05
Its a Broadcom Corporation BCM94311MCG wlan mini-PCI 

Please help

---

### Post by elctb on 2007-11-07
It seems that for your device you need to use ndiswrapper. See this thread:

[http://ubuntuforums.org/showthread.php?t=601773&highlight=BCM94311MCG](http://ubuntuforums.org/showthread.php?t=601773&highlight=BCM94311MCG)

---

