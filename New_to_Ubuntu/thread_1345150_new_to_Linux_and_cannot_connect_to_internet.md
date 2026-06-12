---
title: "new to Linux and cannot connect to internet"
date: 2009-12-03
forum: New to Ubuntu
---

### Post by serkit on 2009-12-03
I have no idea what to do- this is the first time I ever use Linux and i got the ubuntu cd 4 days ago- 9.10 version- i tried it on my sister's laptop and without installing it, it would connect to the internet and work fine, on mine however (completely installed), it doesn't even detect the internet and we're using the same wireless internet connection. can anyone help me?

---

### Post by melrokz on 2009-12-03
you are within a public wifi range?

---

### Post by amsum on 2009-12-03
If yours is Atheros Wireless Card, then try this one.

Look into the file
/etc/modprobe.d/blacklist-ath_pci.conf

and then comment out the line...
blacklist ath5k

so it should look like
#blacklist ath5k

Now Save it and reboot the system. It must recognize the wireless after rebooting.

---

### Post by themusicalduck on 2009-12-03
See if you can connect using an ethernet cable, then go to System > Administation > Hardware Drivers and you might be able to download and install a driver from there.

---

### Post by serkit on 2009-12-03
I'm not within a public wifi spot, i have no idea how to check what wireless card i have and I just tried connecting through the ethernet- it recognizes the connection for the dsl but still won't connect, plus i was kind of hoping to use it wirelessly since i'm not the only one who uses it

---

### Post by serkit on 2009-12-03
no i'm not, but i'm right next to my wireless router

---

### Post by serkit on 2009-12-03
how do i check what wireless card i have?

---

### Post by serkit on 2009-12-03
it detects the connection if i connect the cable but it doesn't connect

---

### Post by themusicalduck on 2009-12-03
It recognises the connection? Does the network applet on the panel indicate that something has connected? or does it just attempt to connect and then fail?

If it connects, do you just not have internet? If it does connect at all, it might be worth typing ```
ifconfig
``` into a terminal and posting the output here.

In theory if you can get ethernet to work, you can then download and install the drivers which will make your wireless work.

---

### Post by Some Penguin on 2009-12-03
> **serkit said:**
> I'm not within a public wifi spot, i have no idea how to check what wireless card i have and I just tried connecting through the ethernet- it recognizes the connection for the dsl but still won't connect, plus i was kind of hoping to use it wirelessly since i'm not the only one who uses it

Have you done any searching?

First hit for "identifying wireless in Ubuntu":
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

---

### Post by serkit on 2009-12-03
yes, it tries to connect but then fails- i'm going to try it again and put that ifconfig and i should be back in a few min with output, thanks!

---

### Post by serkit on 2009-12-03
ok here is what it says- it still doesn't connect to the internet though...

   eth0      Link encap:Ethernet  HWaddr 00:1e:68:b3:85:b6  
  
            inet6 addr: fe80::21e:68ff:feb3:85b6/64 Scope:Link
  
            UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
  
            RX packets:71 errors:0 dropped:0 overruns:0 frame:0
  
            TX packets:59 errors:0 dropped:0 overruns:0 carrier:0
  
            collisions:0 txqueuelen:1000 
  
            RX bytes:4348 (4.3 KB)  TX bytes:6986 (6.9 KB)
  
            Interrupt:27 Base address:0x6000 
  
   
   
  lo        Link encap:Local Loopback  
  
            inet addr:127.0.0.1  Mask:255.0.0.0
  
            inet6 addr: ::1/128 Scope:Host
  
            UP LOOPBACK RUNNING  MTU:16436  Metric:1
  
            RX packets:4 errors:0 dropped:0 overruns:0 frame:0
  
            TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
  
            collisions:0 txqueuelen:0 
  
            RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

---

### Post by themusicalduck on 2009-12-03
I'm not sure what to suggest if you can't connect through ethernet either.

Last thing to try is to find out exactly what hardware you have and  do a bit of google searching to see if you can find out more about it on linux.

Type ```
lspci
``` into the terminal and it'll list all your hardware including any network hardware.

Post it here too and someone might know more about that specific card.

---

### Post by serkit on 2009-12-03
00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
  
  00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
  
  00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
  
  00:01.2 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
  
  00:01.3 Co-processor: nVidia Corporation MCP67 Co-processor (rev a2)
  
  00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
  
  00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
  
  00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
  
  00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
  
  00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1)
  
  00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
  
  00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2)
  
  00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2)
  
  00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
  
  00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
  
  00:0d.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
  
  00:12.0 VGA compatible controller: nVidia Corporation C67 [GeForce 7150M / nForce 630M] (rev a2)
  
  00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
  
  00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
  
  00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
  
  00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
  
  02:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
  
  02:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
  
  02:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
  
  02:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
  
  02:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
  
  03:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)




here it is
ill try to google it thanks for ur help

---

### Post by Some Penguin on 2009-12-03
Interesting.  You've got an IPv6 address from the router, but not an IPv4 one.   

[http://www.linuxquestions.org/questions/linux-networking-3/eth0-no-longer-works-does-not-have-inet-address-ubuntu-8.10-704691/](http://www.linuxquestions.org/questions/linux-networking-3/eth0-no-longer-works-does-not-have-inet-address-ubuntu-8.10-704691/)

seems relevant.  In particular, the bit about in /etc/network/interfaces


auto eth0
iface eth0 inet dhcp

---

### Post by OmegaSage on 2009-12-09
Having the same problem as this guy. We installed Ubuntu on my brothers desktop computer, and it runs great and all, however will not connect to the internet. Same general problem as this guy, it detects it, but when it tries to connect it just kinda fails. I read through this thread and tried following what you said here. The information that came up doing those terminal commands are vastly different, so maybe you can help me better than you could him.


ifconfig:

eth0
Link encap:Ethernet  HWaddr 00:08:02:97:fd:d7
UP BROADCAST MULTICAST  MTU:1500  Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo
Link encap:Local Loopback
inet addr:127:0:0:1  Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING  MTU:16436  Metric:1
RX packets:52169 errors:0 dropped:0 overruns:0 frame:0
TX packets:52169 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:10571436 (10.5 MB)  TX bytes:10571436 (10.5 MB)

wlan0
Link encap:Ethernet  HWaddr 00:30:bd:65:4f:1d
UP BROADCAST MULTICAST  MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 xtqueuelen:1000
RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0
Link encap:UNSPEC  HWaddr 00-30-BD-65-4F-1D-00-00-00-00-00-00-00-00-00-00
UP RUNNING  MTU:0  Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 xtqueuelen:1000
RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


lspci:

00:00.0 Host bridge: Intel Coporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:02.0 VGA compatible controller: Intel Coporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-L/ICH4-M) USB2 EHCI Controller (rev01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Coporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
05:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VM (LOM) Ethernet Controller (rev 81)

---

### Post by ukripper on 2009-12-09
conect the cable and post output of following commands:
```
ifconfig
```
```
sudo lshw -C network
```

---

