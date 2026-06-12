---
title: "Lacking Internet connection and a brain. TL-WN321G"
date: 2011-02-01
forum: New to Ubuntu
---

### Post by Omegus on 2011-02-01
salutations. Ill give you a slight back story on my problem. It all began when i purchased my brand new computer stats here.
Optical drive : Sony 24x Sata DVDRW
Powersupply: Xion 700W
Harddrives: 2x WD 500GB SATA-2 WD5000KS
Motherboard: MSI 890GXM-G65
Videocard: Radeon HD5850 1GB
Ram: 2x 4GB DDR3-1333 Single
Processor: AMD Phenom II x6 1055T Tray
Raid setting: Raid-0 

I couldn't wait to Install Ubuntu 10.10 so I hit a little snag when I didn't realize that when I was installing that my user name had to be lowercased. (Foreshadowing.....) After I surfed your wonderful forums for a bit I found that I was an Idiot and sorted my self out. After the Installation process was finished . I remember I had only purchased Intel 100/1000 ethernet card without wireless. so I tried setting up the ethernet cable. I drilled a few holes in the floor (DEAR GOD POWER TOOLS!!!) and after plugging the cable into the tower and modem and running the ifconfig for all my info......nothing. I also tried to set it up in the Network connctions in preference.

I had come back to the forums for help and was more confused then when I came in . I found 40 differant methods to one problem and I tried them all at once. I lost my mind and proceeded to chase the next door neighbors children and make them cry.

I gave up on the wired and bought without thinking a Wireless USB Adapter model number TL-WN321G v2 . I once again came back to the forums for help and found out I needed Ndiswrapper so I downloaded the files and installed it to desktop and the drivers for hardware. This is where I hit a snag I don't know what to do now. I still have no connection and Ubuntu is not showing that there is any sort of wireless in the terminal. 

At this point I just want some sort of connection. I will reinstall Ubuntu if need be for a clean slate, But I am losing my mind on this. Ill upload all my finding in a few mins. But any help or input would be nice.

Update 20:11 pm-  ok when I type "ifconfig" here is my info
omegus@omegus-MS-7642:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 6c:62:6d:81:95:de  
          inet addr:192.168.2.12  Bcast:192.168.2.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:45 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1200 (1.2 KB)  TX bytes:1200 (1.2 KB)

---

