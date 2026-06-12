---
title: "problem copying files over network"
date: 2008-01-12
forum: Networking &amp; Wireless
---

### Post by Wintergedaerm on 2008-01-12
I have a server with ubuntu server 7.0 installed.
When i try to copy a file via a shared samba directory to my windows xp pc(tried it with two different xp machines) the data transfer aborts with the error message  "The specified network name is no longer available".
When i try to copy a file via a mounted nfs share to my debian it simply hangs.

In both cases navigating through the file system works flawless.
I already changed network cards in the server machine but the same problem still persists.

**lspci:**

00:00.0 Host bridge: VIA Technologies, Inc. VT82C585VP [Apollo VP1/VPX] (rev 23)
00:07.0 ISA bridge: VIA Technologies, Inc. VT82C586/A/B PCI-to-ISA [Apollo VP] (rev 27)
00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:09.0 VGA compatible controller: ATI Technologies Inc 3D Rage Pro 215GP (rev 5c)
00:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)


**ifconfig:**

eth1      Link encap:Ethernet  HWaddr 00:02:44:16:9E:A1
          inet addr:192.168.123.2  Bcast:192.168.123.255  Mask:255.255.255.0
          inet6 addr: fe80::202:44ff:fe16:9ea1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:32995 errors:0 dropped:0 overruns:0 frame:0
          TX packets:55419 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2459551 (2.3 MB)  TX bytes:72086531 (68.7 MB)
          Interrupt:11 Base address:0x6000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:76 errors:0 dropped:0 overruns:0 frame:0
          TX packets:76 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:6064 (5.9 KB)  TX bytes:6064 (5.9 KB)



Any ideas?  Thnx

---

### Post by Wintergedaerm on 2008-01-13
Setting the speed of the network card to 10MB with
> sudo ethtool -s eth1 speed 10 duplex full  autoneg off
seems to solve the problem even though 10MB is painfully slow.

its not the network card as i tried different ones,  same goes with the 
network cable.

Any ideas how to get it to 100Mbit? the server hardware is quite old with 100Mhz and 64MB memory.

---

### Post by svennils on 2008-02-09
I've got a similar problem, except in my case the client hangs. 2 laptops& 1 server.
100mbit wired network, all machines run gutsy. One laptop will up&download fine any filesize, the other will download anything and will hang on large uplaods (at 100 megs or so). first it hangs the copy process, then all network activity. Umounting the nfs share claims it it busy. Any hints? The functioning laptop is a Compaq Evo N800v, 100mbit intel pro 100 card. The crashing one is a Hp compaq Nc8000 with broadcom netxtreme_2 Gigabit  lan card.

EDIT:
Just mounted the same server via samba & smb4k, the "faulty" laptop will up&download fine with smb. not so with nfs.

---

