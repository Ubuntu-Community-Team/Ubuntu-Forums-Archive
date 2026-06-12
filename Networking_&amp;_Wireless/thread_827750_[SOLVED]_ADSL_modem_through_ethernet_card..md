---
title: "[SOLVED] ADSL modem through ethernet card."
date: 2008-06-13
forum: Networking &amp; Wireless
---

### Post by diwas on 2008-06-13
I have TP-LINK (model number: TD-8817), ADSL 2/2+ Ethernet/USB router. And a newly bought UMAX (model number: ULC-RTL8139D) 10/100Mbps fast ethernet adapter. 

When im in XP, i use internet through the ADSL modem connected with the ethernet card and it runs quite smooth. But in ubuntu i have to connect throught the USB port.

The LAN stuff wont work...i dont know what is the problem with this...i ran through the help and was successful to connect throught the USB not LAN..

I wud like to connect through LAN...so can anyone help me out?

Thanks.

---

### Post by nickdbliss on 2008-06-13
Just make sure driver for ur LAN card is installed. THen you can follow the simple guide to setup ADSL using ubuntu help in menu.

---

### Post by nickdbliss on 2008-06-13
run
#lspci

Make sure it shows ur card.After that u can run
 #sudo pppoeconf
That will setup your internet connection 
then run
#sudo pon dsl-provider
to connect to internet and
#sudo poff dsl-provider
to turn it off. 

Worked for me.Hope it will work for you too.

---

### Post by diwas on 2008-06-13
Where can i find the driver?? Its not in the cd...though. I havnt installed the ethernet card's driver.

---

### Post by nickdbliss on 2008-06-13
give me the output of following commands.

#lshw -C network
and
#ifconfig
 
Type them in terminal and paste the output here.thanks

---

### Post by diwas on 2008-06-13
~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8139D [Realtek] PCI 10/100BaseTX ethernet adaptor
       vendor: Hangzhou Silan Microelectronics Co., Ltd.
       physical id: 1
       bus info: pci@0000:01:01.0
       logical name: eth0
       version: 01
       serial: 00:18:46:01:4e:e3
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sc92031 driverversion=2.0c latency=32 maxlatency=40 mingnt=20 module=sc92031 multicast=yes
  *-network
       description: Ethernet interface
       physical id: 1
       logical name: eth1
       serial: 00:1d:0f:a9:0c:c2
       capabilities: ethernet physical
       configuration: broadcast=yes driver=rndis_host driverversion=22-Aug-2005 firmware=RNDIS device ip=192.168.1.2 multicast=yes
diwas@diwas-desktop:~$ 
diwas@diwas-desktop:~$ sudo lshw -C network
[sudo] password for diwas:
  *-network               
       description: Ethernet interface
       product: RTL8139D [Realtek] PCI 10/100BaseTX ethernet adaptor
       vendor: Hangzhou Silan Microelectronics Co., Ltd.
       physical id: 1
       bus info: pci@0000:01:01.0
       logical name: eth0
       version: 01
       serial: 00:18:46:01:4e:e3
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sc92031 driverversion=2.0c duplex=half latency=32 link=no maxlatency=40 mingnt=20 module=sc92031 multicast=yes port=MII speed=10MB/s
  *-network
       description: Ethernet interface
       physical id: 1
       logical name: eth1
       serial: 00:1d:0f:a9:0c:c2
       capabilities: ethernet physical
       configuration: broadcast=yes driver=rndis_host driverversion=22-Aug-2005 firmware=RNDIS device ip=192.168.1.2 link=yes multicast=yes


diwas@diwas-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:18:46:01:4E:E3  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:20 Memory:ff8ffc00-ff8ffcff 

eth1      Link encap:Ethernet  HWaddr 00:1D:0F:A9:0C:C2  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:fff:fea9:cc2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1462 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1543 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1236819 (1.1 MB)  TX bytes:270454 (264.1 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:140 (140.0 b)  TX bytes:140 (140.0 b)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:10.1.30.158  P-t-P:10.1.0.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:1431 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1466 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:1221528 (1.1 MB)  TX bytes:161053 (157.2 KB)


eth0 is my USB drive i guess.

---

### Post by diwas on 2008-06-13
diwas@diwas-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
01:01.0 Ethernet controller: Hangzhou Silan Microelectronics Co., Ltd. RTL8139D [Realtek] PCI 10/100BaseTX ethernet adaptor (rev 01)
01:02.0 Modem: PCTel Inc HSP56 MicroModem (rev 04)


Incase you need it too.

---

### Post by diwas on 2008-06-16
bump..

---

### Post by diwas on 2008-07-24
I installed new version of ubuntu. And it works great!!

---

