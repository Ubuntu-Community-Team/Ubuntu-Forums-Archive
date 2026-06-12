---
title: "Hopeless to fix internet"
date: 2007-04-13
forum: Networking &amp; Wireless
---

### Post by Pidgin English on 2007-04-13
Alright, I downloaded Ubuntu Edgy Eft a few months ago hoping that things would "just work," and now my overconfidence in the guys behind Ubuntu has come back to haunt me. 

I started things up and everything looks awsome - I much prefer the interface to Windows - but not once has the internet been able to fire up. I tried a few things as directed by a few people in these forums (Including Static IPs), but every time it did nothing to revive my connection. I eventually gave up and tried to use my XP restore disk to get everything back to normal... Too bad that doesn't work either.

So, now I'm back here. I don't know what to do. I'm feeling like a real prick for just reading an article in POP SCI and deciding "Oh, I want to change my OS on a whim."

I'm just hoping that there's someone out there who is perhaps willing to aid me in fixing this.

Ask anything, just please put it in simple terms... After all, I am an idiot.

Oh, and if anyone is willing to talk me through things... I'm both a verizon subscriber, and I have an Xbox 360 [Heck, that voice chat is useful sometimes]. #-o

Cheers,
Rob.

---

### Post by Swab on 2007-04-13
Can you provide more details and links to previous threads where you have asked for help.  For starters we need to know the type of modem you have, and how it is connected to your PC.

---

### Post by tgm4883 on 2007-04-13
Desktop or laptop?  can you post the output of lspci?

---

### Post by dbott67 on 2007-04-13
If you can't get online at all, maybe you copy & paste the output to a text file & save it to USB/floppy and bring it over to a working computer (or use the 'redirect' command).

Can you please post the output of the following commands:

```
cat /etc/network/interfaces > interfaces.txt
```This will create a file in your home directory called 'interfaces.txt that you can copy to USB or floppy and then upload from Windows.  _**It won't display anything on screen.**_

Here's mine as an example (redirected to the screen only, not to a file):

```
dbott@dapper:~$ cat/etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid bott
wireless-key s:mysecretwepkey
```This command shows ALL network interfaces on the system (whether enabled or not).  Again, you should redirect the output to a file:

```
ifconfig -a > ifconfig.txt
``````
dbott@dapper:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:15:C5:0C:AD:XX
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:217

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:438044459 errors:0 dropped:0 overruns:0 frame:0
          TX packets:438044459 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1712747473 (1.5 GiB)  TX bytes:1712747473 (1.5 GiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:16:CE:31:88:XX
          inet addr:192.168.1.105  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:ceff:fe31:886f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:738503 errors:0 dropped:0 overruns:0 frame:0
          TX packets:500344 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:658372626 (627.8 MiB)  TX bytes:64530804 (61.5 MiB)
          Interrupt:169 Memory:dfcfc000-dfd00000
```This command outputs the network hardware detected:

```
sudo lshw -C network > lshw.txt
```Here's mine for comparison:

```
dbott@dapper:~$ sudo lshw -C network
Password:
  *-network
       description: Wireless interface
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0b:00.0
       logical name: wlan0
       version: 01
       serial: 00:16:ce:31:88:6f
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper driverversion=1.25 firmware=Broadcom,11/02/2005, 4.10.40.0 ip=192.168.1.105 link=yes multicast=yes wireless=IEEE 802.11b
       resources: iomemory:dfcfc000-dfcfffff irq:169
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@03:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:0c:ad:05
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=b44 driverversion=0.97 duplex=half link=no multicast=yes port=twisted pair speed=10MB/s
       resources: iomemory:df9fe000-df9fffff irq:217

```This command prints out your routing table:

```
route -n > route.txt
``````
dbott@dapper:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
```And finally, this command prints out PCI information:

```
lspci > lspci.txt
``````
dbott@dapper:~$ lspci

0000:00:00.0 Host bridge: Intel Corporation Mobile Memory Controller Hub (rev 03)
0000:00:01.0 PCI bridge: Intel Corporation Mobile PCI Express Graphics Port (rev 03)
0000:00:1b.0 0403: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
0000:00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
0000:00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
0000:00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
0000:00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
0000:00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
0000:00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
0000:00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
0000:00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
0000:00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controllers cc=IDE (rev 01)
0000:00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 7145
0000:03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
0000:03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd: Unknown device 0832
0000:03:01.1 0805: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
0000:03:01.2 System peripheral: Ricoh Co Ltd: Unknown device 0843 (rev 01)
?000:03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
0000:03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
[COLOR=Red]0000:0b:00.0 Network controller: Broadcom Corporation: Unknown device 4311 (rev 01)
[/COLOR]
```After you've run the 5 commands, copy the files (interfaces.txt, ifconfig.txt, lshw.txt, route.txt and lspci.txt) to a floppy or USB drive and them post them up here.

Thanks,
Dave

---

### Post by briantm on 2007-04-13
Sorry to butt in on the thread but I'm having the very same problem.

Just installed Xubuntu on my dell X1 and it wont connect to the net. I have DHCP but set it to static to see if that would work.

The settings you asked (someone else, sorry again) for:

**interfaces**

auto lo
iface lo inet loopback


auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp




iface eth0 inet static
address 10.44.1.233
netmask 255.255.255.0
gateway 10.44.1.1

auto eth0


**ifconfig**

eth0      Link encap:Ethernet  HWaddr 00:13:72:6B:18:38  
          inet addr:10.44.1.233  Bcast:10.44.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:72ff:fe6b:1838/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:426 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:38907 (37.9 KiB)  TX bytes:4630 (4.5 KiB)
          Interrupt:16 

eth1      Link encap:Ethernet  HWaddr 00:16:6F:54:B7:6C  
          inet addr:10.2.2.118  Bcast:10.2.2.127  Mask:255.255.255.240
          inet6 addr: fe80::216:6fff:fe54:b76c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1257 errors:0 dropped:0 overruns:0 frame:0
          TX packets:455 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:189235 (184.7 KiB)  TX bytes:54760 (53.4 KiB)
          Interrupt:18 Base address:0x8000 Memory:dfcff000-dfcfffff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:224 errors:0 dropped:0 overruns:0 frame:0
          TX packets:224 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15458 (15.0 KiB)  TX bytes:15458 (15.0 KiB)



**lshw**


  *-network
       description: Ethernet interface
       product: NetXtreme BCM5751 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@01:00.0
       logical name: eth0
       version: 01
       serial: 00:13:72:6b:18:38
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.72 duplex=full firmware=5751-v3.29a ip=10.44.1.233 latency=0 link=no multicast=yes port=twisted pair speed=100MB/s
       resources: iomemory:dfdf0000-dfdfffff irq:16
  *-network
       description: Wireless interface
       product: PRO/Wireless 2200BG Network Connection
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@02:03.0
       logical name: eth1
       version: 05
       serial: 00:16:6f:54:b7:6c
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.0kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) ip=10.2.2.118 latency=64 link=yes maxlatency=24 mingnt=3 multicast=yes wireless=IEEE 802.11g
       resources: iomemory:dfcff000-dfcfffff irq:18


**routing**


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.2.2.112      0.0.0.0         255.255.255.240 U     0      0        0 eth1
10.44.1.0       0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
0.0.0.0         10.44.1.1       0.0.0.0         UG    0      0        0 eth0
0.0.0.0         10.2.2.113      0.0.0.0         UG    0      0        0 eth1



**lspci**


00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express (rev 01)
02:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3)
02:01.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 08)
02:01.2 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 17)
02:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)






Any help you could give would be greatly appreciated.

B :confused: 


Sorry again for butting into the thread

---

### Post by dbott67 on 2007-04-13
@briantm: try disabling one of the interfaces (such as the wireless):
```
sudo ifdown eth1
```-Dave

---

### Post by Pidgin English on 2007-04-14
Alright, I can only get on here about once or twice daily, so I'll try to get some information out.

Here's the link to the previous thread: [http://ubuntuforums.org/showthread.php?t=368896]("http://ubuntuforums.org/showthread.php?t=368896")

And to repeat the information in that thread:

Computer: Sony VAIO desktop [Kinda old, but I lack the expertise to replace any hardware...]

Modem: DSL Westell 6100 [Could it be a windows-only modem? I was told that by someone.)

Router: WIRED Linksys Cable/**DSL** Router Model: BEFSR41 [Works great on my XP (I'm using it to write this message) and it hardly ever has trouble assigning IPs to this box.]

I have frequent connection troubles with my DSL [I don't know what might be the cause, but it just doesn't work sometimes]. That might have something to do with it.

For more info, check the mentioned thread.




The results you wanted, Dave:

Interfaces:
```
auto lo
iface lo inet loopback


iface eth0 inet dhcp
address 192.168.1.3
netmask 255.255.255.0
gateway 192.168.1.1

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


iface dsl-provider inet ppp
provider dsl-provider







auto eth0
```

Ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 00:0C:6E:72:0E:32  
          inet6 addr: fe80::20c:6eff:fe72:e32/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:217 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:39 errors:0 dropped:0 overruns:0 frame:0
          TX packets:39 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3391 (3.3 KiB)  TX bytes:3391 (3.3 KiB)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


```

lshw:
```
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: d
       bus info: pci@01:0d.0
       logical name: eth0
       version: 10
       serial: 00:0c:6e:72:0e:32
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=8139too driverversion=0.9.27 duplex=full link=yes multicast=yes port=MII speed=100MB/s
       resources: ioport:b800-b8ff iomemory:ee800000-ee8000ff irq:217

```

Route:
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

```

Ispci:
```
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
01:0d.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:0e.0 FireWire (IEEE 1394): NEC Corporation uPD72874 IEEE1394 OHCI 1.1 3-port PHY-Link Ctrlr (rev 01)

```

Thanks for taking interest!

-Rob

---

### Post by Pidgin English on 2007-04-14
Oh, and don't worry about butting in briantm. Just try putting your text files in code boxes.

```
 REPLY WITH A QUOTE TO SEE HOW TO DO IT 
```

---

### Post by dbott67 on 2007-04-14
Hi Rob,

If the computer is connected to the Linksys Router, you do not need the line in your interfaces file that refers to the dsl-provider (it's only required if the DSL modem is directly connected to the computer, instead of the router).  The Linksys router handles the modem connection, you only need to get your computer to talk to the router (which should be fairly simple).

You also need to add 'auto eth0' somewhere in the file (it doesn't matter where, but you can just put it where I've shown it):
```
auto lo
iface lo inet loopback

[COLOR=Red]auto eth0    *[COLOR=Blue]# <-- you need to add this command[/COLOR]*[/COLOR]
iface eth0 inet dhcp
address 192.168.1.3
netmask 255.255.255.0
gateway 192.168.1.1

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


[COLOR=Blue]#[/COLOR] iface dsl-provider inet ppp  *[COLOR=Blue]# <--- comment out these 2 lines[/COLOR]*
[COLOR=Blue]# [/COLOR]provider dsl-provider  [COLOR=Blue][I]# <--- comment out these 2 lines
[/I][/COLOR]
```[COLOR=Blue][COLOR=Black]

Does your setup look similar to the attached diagram?  If so, the Linksys router handles the connection and authentication with your ISP; your Ubuntu computer should just be connected to the Linksys router via ethernet cable.

Other than that, everything else looks fine.  The problem is that the interfaces file is not set to automatically enable the interface (eth0).  By adding the 'auto eth0' to the file, it tells the system to automatically activate the card.  Without the command there, you would need to activate in manually by typing the following command in a terminal:
```
sudo ifup eth0
```Before you do anything, boot into Ubuntu and open a terminal & type that command to see if you get online.  If you do, edit the interfaces file as I have suggested.

-Dave
[/COLOR][/COLOR]

---

### Post by dbott67 on 2007-04-14
@Rob: I'm not sure if you want/need to use static IP addressing in Ubuntu (you would if you want to be able to access the computer via IP or you're hosting a server, such as web, mail, ftp, ssh, vnc, etc.).

If you're not doing any of that, you can use DHCP to obtain the network configuration settings.  Change this part of your **/etc/network/interfaces** file from this:
```
auto eth0
iface eth0 inet dhcp
address 192.168.1.3
netmask 255.255.255.0
gateway 192.168.1.1
```to this:
```

auto eth0
iface eth0 inet dhcp
```

By default, the Linksys router provides a DHCP service so that users can just plug in the network cable and start surfing... no network configuration required.
-Dave

---

### Post by dbott67 on 2007-04-14
I just read through the other thread and have a few thoughts:

1. Are you dual-booting with Windows & Ubuntu, or are they separate computers?

2. The Linksys Router is really just a little computer running some sort of Linux-variant.  Sometimes the DHCP service can hang.  Just unplug (power) the router & modem for a few minutes and then plug them back in.  The router & modem should re-boot & initialize.  After a couple of minutes, re-boot into Ubuntu and see what happens.

3. Try updating the firmware to your Linksys modem.  Using your Windows computer, go to the Linksys Website and find your router model.  [Download the latest firmware]("http://www.linksys.com/servlet/Satellite?c=L_CASupport_C2&childpagename=US%2FLayout&cid=1166859876500&packedargs=sku%3DBEFSR41&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=7650076500B01&displaypage=download") & follow the instructions to update your router.

-Dave

---

### Post by Pidgin English on 2007-04-14
I tried entering the following command:

```
sudo ifup eth0
```

And it came up with something like:

```
interface eth0 already configured
```

...and firefox still doesn't work.


Also, how do you access files so that you can edit their contents? 

What do you mean by commenting out those two lines? Do you want me to delete them?

You have to excuse my poor computer skills.

-Rob

---

### Post by Pidgin English on 2007-04-14
Further answers:

1. The windows and Linux boxes are seperate.

2. I tried restarting my modem and router, but still had no connection.

3. I updated my firmware and still... no internet.

---

### Post by dbott67 on 2007-04-14
Try this command first:
```
sudo ifdown eth0
```Then try:
```
sudo ifup eth0
```You can edit those files using the following command:
```
sudo gedit /etc/network/interfaces
```Which will open the file (as root) using the program 'gedit' (a graphical editor for Gnome).

Commenting out (sometimes referred to as 'remarks') are lines that are ignored by the system.  In many cases, programmers use them to provide comments (or remarks) about what the command does.  For example, here is a little script that I wrote to reset the network interface:
```
[COLOR=Red]#!/bin/bash[/COLOR]
# Any line that begins with a '#' will be ignored (except [COLOR=Red]#!/bin/bash[/COLOR])
# Now, I can provide some instructions without the computer trying to execute 
# my plain English explanation.
#
# Or I can use a comment (#) to temporarily prevent a command from running
# by placing it at the beginning of the line.  It's better than deleting the command
# in case you ever want to restore it.
#
# This script will reset your network interface card

# Bring down the interface (de-activate)
[COLOR=Red] sudo ifdown eth0[/COLOR]

# Bring up the interface (activate)
[COLOR=Red] sudo ifup eth0[/COLOR]

# There are only 3 lines that the computer reads:
# the [COLOR=Red]**#!/bin/bash**[/COLOR] (it's a special line)
# and [COLOR=Red]**sudo ifdown eth0**[/COLOR] and [B][COLOR=Red]sudo ifup eth0[/COLOR]
[/B]# Everything else is ignored.
```

---

### Post by Pidgin English on 2007-04-14
Further answers:

1. The windows and Linux boxes are seperate.

2. I tried restarting my modem and router, but still had no connection.

3. I updated my firmware and still... no internet. :confused:

---

### Post by Pidgin English on 2007-04-14
I don't know what I've done now, but this cannot be good:

```
pidgin@Feathered-Circuits:~$ sudo ifdown eth0
Password:
There is already a pid file /var/run/dhclient.eth0.pid with pid 4592
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:0c:6e:72:0e:32
Sending on   LPF/eth0/00:0c:6e:72:0e:32
Sending on   Socket/fallback
pidgin@Feathered-Circuits:~$ sudo ifup eth0
There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:0c:6e:72:0e:32
Sending on   LPF/eth0/00:0c:6e:72:0e:32
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 19
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
pidgin@Feathered-Circuits:~$ sudo gedit /etc/network/interfaces
pidgin@Feathered-Circuits:~$ sudo ifdown eth0
/etc/network/interfaces:29: interface eth0 declared allow-auto twice
ifdown: couldn't read interfaces file "/etc/network/interfaces"
pidgin@Feathered-Circuits:~$ sudo ifup eth0
/etc/network/interfaces:29: interface eth0 declared allow-auto twice
ifup: couldn't read interfaces file "/etc/network/interfaces"
pidgin@Feathered-Circuits:~$ sudo gedit /eth/network/interfaces

** (gedit:5189): WARNING **: Hit unhandled case 1 (File not found) in gedit_unrecoverable_saving_error_message_area_new.
pidgin@Feathered-Circuits:~$ sudo ifup eth0
/etc/network/interfaces:29: interface eth0 declared allow-auto twice
ifup: couldn't read interfaces file "/etc/network/interfaces"
pidgin@Feathered-Circuits:~$ sudo ifdown eth0
/etc/network/interfaces:29: interface eth0 declared allow-auto twice
ifdown: couldn't read interfaces file "/etc/network/interfaces"
pidgin@Feathered-Circuits:~$ 

```

I changed the file as you told me to and now it's telling me that it cannot read the file...

---

### Post by dbott67 on 2007-04-14
I think it's because you didn't close the gedit program.  The other error:
```
/etc/network/interfaces:29: interface eth0 declared allow-auto twice
``` is because the statement 'auto eth0' occurs twice.  Make sure there's only one instance of the 'auto eth0'.

From a configuration standpoint, everything looks good, but I'm starting to question the ethernet cable or perhaps the port on the router.

Here's what we know:

A. The cable (let's call it 'Cable #1) connected to your _**Windows computer**_ is good (because Windows can get online).
B. The port that Cable #1 is plugged into (let's call it Port #1) is also good.

1. Disconnect the known-working cable #1 from the back on the Windows computer and plug it into the back of the Ubuntu computer and try to get online again.

This will eliminate the possibility of a bad cable or port on the router.

You can also take the cable that used to connect to the Ubuntu computer and plug it into the back of the Windows machine & try to get online.  If you have troubles, then there's a problem with the cable, the port on the router, or the connection.  Double check to make sure the cables are firmly plugged in and that the lights on the router port & NIC card are lit up.

-Dave

---

### Post by Pidgin English on 2007-04-14
Alrighty then, I've done the equivalent (unplugged the cable from my Xbox 360 - which I was playing just yesturday - and tried that in the Ubuntu box). Although, even after restarting the router and modem, my Ubuntu still refuses to connect.


*I have a messenger account, if that's easier for you*

---

### Post by dbott67 on 2007-04-14
Can  you post the output of the following commands again:
```
ifconfig -a > ifconfig1.txt
```
```
route -n > route1.txt
```
```
ping 127.0.0.1 -c 4 > ping1.txt
```
```
ping 192.168.1.1 -c 4 > ping2.txt
```
```
dmesg | grep eth0 > dmesg.txt
```

You may have to re-direct them to a file, as you did in a previous post, copy them over to USB and upload them using Windows.

-Dave

---

### Post by Pidgin English on 2007-04-14
Results:

ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 00:0C:6E:72:0E:32  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:217 Base address:0xc000 

lo        Link encap:Local Loopback  
          LOOPBACK  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


```

route:
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

```

dmesg:
```
[17179591.344000] eth0: RealTek RTL8139 at 0xd018c000, 00:0c:6e:72:0e:32, IRQ 217
[17179591.344000] eth0:  Identified 8139 chip type 'RTL-8101'

```


_**I couldn't connect to either 127.0.0.1 nor 192.168.1.1.**_

---

### Post by dbott67 on 2007-04-14
If you are unable to ping 127.0.0.1, then your network card is likely not functioning properly (it could be a driver issue or a hardware failure).  The next step is to take a known working NIC and try it to see if it works.

You can also pickup an inexpensive D-Link NIC for ~$15 or $20 from a local computer shop.  

-Dave

---

### Post by Pidgin English on 2007-04-14
Alright, I'll get back to you on that. :) 

~Rob

---

