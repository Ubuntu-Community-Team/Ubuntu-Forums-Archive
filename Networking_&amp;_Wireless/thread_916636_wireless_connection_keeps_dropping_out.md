---
title: "wireless connection keeps dropping out"
date: 2008-09-11
forum: Networking &amp; Wireless
---

### Post by jubei80 on 2008-09-11
Bump?

Help,(now that I finally have a breather from my course) I have done a fresh install of Ubuntu 8.4 and unlike 7.10 the wireless keeps dropping out quite frequently (I'd say twice every 10mins)I have no clue whats wronge granted I am somewhat of a noob, all my research has amounted to naught. I did change the default network manager to Wicd hoping it would correct this, it didn't. But anytime it goes off all i have to do is disconnect and reconnect (almost in one continuous motion) and my signal & connection is back.

Here are all the terminal outputs I think you will need :


jubei@jubei-laptop:~$ sudo lshw | grep Wireless
[sudo] password for jubei: 
       description: Wireless interface
jubei@jubei-laptop:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub [8086:27a0] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 [8086:27d2] (rev 02)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 [8086:27d4] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801G (ICH7 Family) IDE Controller [8086:27df] (rev 02)
00:1f.2 IDE interface [0101]: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller [8086:27c4] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801G (ICH7 Family) SMBus Controller [8086:27da] (rev 02)
06:05.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
jubei@jubei-laptop:~$ 
 
jubei@jubei-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
06:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

jubei@jubei-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 5
       bus info: pci@0000:06:05.0
       logical name: eth0
       version: 10
       serial: 00:03:0d:6c:54:42
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=32 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:19:db:99:d0:12
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.0.3 multicast=yes wireless=IEEE 802.11g
jubei@jubei-laptop:~$ 

jubei@jubei-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:03:0d:6c:54:42  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1464 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1464 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:76129 (74.3 KB)  TX bytes:76129 (74.3 KB)

wlan0     Link encap:Ethernet  HWaddr 00:19:db:99:d0:12  
          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::219:dbff:fe99:d012/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13982 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9705 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:19670980 (18.7 MB)  TX bytes:1134175 (1.0 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-19-DB-99-D0-12-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


I am partially convinced it is a problem of the cnnection not looping since I am having to do it manually, although i dont know why, here is a copy of the interface text in /etc/network/interfaces

auto lo
iface lo inet loopback

Help pls!:(

---

### Post by jubei80 on 2008-09-11
Bump!1

---

### Post by jubei80 on 2008-09-15
Bump 2

---

### Post by liyanricaoqiyue1314 on 2008-09-15
[size=2]Nude-calendar 1177, human and Shouzu the third "Battle of Lawson," Lawson barriers on the ground before the start of the Gap. [Runescape Gold](http://www.runescape-shop.com/runescape-gold/runescape-gold.php)This is a historic campaign, the campaign is "human beast seven years of war" in the first three major campaigns, the history of bare-called "people's car used to launch the war." [Runescape Power leveling](http://www.runescape-shop.com/runescape-power-leveling/runescape-power-leveling.php)Because, the bare-three million migrant workers has made in a month-20,000 warships, and timely expansion to the navy,[Runescape Powerleveling](http://www.runescape-shop.com/runescape-power-leveling/runescape-power-leveling.php) so that mankind has made the absolute superiority in the sea, with both sides of the back to. And the barren Shouzufengru the mainland until the 37th of the people of God the outbreak of war. [runescape shop](http://www.runescape-shop.com/)And it is precisely because of this campaign, the first time in the bare-war history, referred to the "Portland Ruo-yun," the name, many historians experts to the expansion of the war of special significance. Some people even said that, if not the war, as there will be a great hero was inspired by, of course, will be impossible for a human return to the mainland seven glorious history. [age of conan power leveling](http://www.aoc-power-leveling.org)Moreover, we said to this great man, in this war also made a bit of good results? [Runescape Gold Farm](http://www.runescape-shop.com/runescape-gold-farm/runescape-gold-farm.php)Portland Ruo-yun from Lawson on the Fort Fangyanwangqu, with both sides of the narrow ground to beat the Shouzu row over the army. [aoc power leveling](http://www.aoc-power-leveling.org)A tall face of ferocious ethnic people Zhengning the claws, but the body is more moderate and flexible people who foot, body, wrapped in a layer of black scales in the long tentacles of the Long Tuzhuo ethnic people. Of course, the master control of the air wing wizard and although their number less, but also with the team in the final, when prone radio ready siege of human soldiers guarding the wall. [/size][size=2][buy age of conan power leveling](http://www.aoc-power-leveling.org)Mankind's troops began to open Lawson barriers, 200,000 of the green collar Tieqi, hidden in two wings of the Tieqi second only to God bow of the 50,000 camp bow riders, and are in the final of the 300,000 Yazhen infantry. [buy aoc power leveling](http://www.aoc-power-leveling.org)Interval between the two sides about two kilometers distance from each other to see the other side of the bright banner of omnipresent there shaking. Ma Si Ming and the anger of the arms occasionally break out the [Runescape money](http://www.runescape-shop.com/runescape-gold/runescape-gold.php)sound of the collision, but the two sides is almost non-soldiers heard voices, the silence before the war that is reinforced by the kind of Qishixiongxiong Fengyuyulai. [Runescape Mini Game](http://www.runescape-shop.com/rs-mini-game/runescape-mini-game.php)The weather has also Laicourenao this time, to beat the dark clouds gradually from the [Rs Power leveling](http://www.runescape-shop.com/runescape-power-leveling/runescape-power-leveling.php) floating over the horizon, live coverage of the original is also clear skies, Yuan Yidian gradually so that the soldiers almost clear of each other's faces, the temperature suddenly dropped. So many people and irritable, even more tense over the past fainted. [Rs Gold](http://www.runescape-shop.com/runescape-gold/runescape-gold.php)Line-up finish. Last night talk election effort a silvery white armor, general Pigua&#24471;&#19981;skin to stay one point, struggling carrying a spear, at the moment Lawson body trembling from the Fort-Ruo-yun, although aware that this time only The first student, is not played with, but on the battlefield or Sheyu powerful Shaqi, the lack of tension in the Tuiruan body. [/size]

---

