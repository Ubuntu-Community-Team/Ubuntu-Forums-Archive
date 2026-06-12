---
title: "missing eth0?"
date: 2008-09-13
forum: Networking &amp; Wireless
---

### Post by MadKAT on 2008-09-13
Hello,

I have ubunut Hardy on an HP Pavillion zx5000 notebook, upgraded since Feisty. Now, I can't connect to the network via the LAN. The wireless (broadcom) is still working, but somehow the wired connection isn't working.

I only noticed this now because I'm usually connected via wireless, but when I decided to connect via wired today, I can't. I don't know if it was the Hardy upgrade or if my hardware is busted, but I'm sure it was working when I was in Gutsy because at that time I couldn't connect via wireless until I installed the broadcom stuff.

If I click "configure" in the Network applet, it says "Device does not exist". If I changed eth1 to eth0, it just says "Error"

Please help, don't know where to start here.



I checked my ifconfig now and it doesn't list eth0. 
```
$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:90:4b:91:c9:c2  
          inet addr:192.168.1.10  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::290:4bff:fe91:c9c2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:205713 errors:0 dropped:0 overruns:0 frame:0
          TX packets:163925 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:270563424 (258.0 MB)  TX bytes:21530706 (20.5 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1853 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1853 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:93388 (91.1 KB)  TX bytes:93388 (91.1 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-90-4B-91-C9-C2-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

---

### Post by Ayuthia on 2008-09-13
> **MadKAT said:**
> Hello,

I have ubunut Hardy on an HP Pavillion zx5000 notebook, upgraded since Feisty. Now, I can't connect to the network via the LAN. The wireless (broadcom) is still working, but somehow the wired connection isn't working.

I only noticed this now because I'm usually connected via wireless, but when I decided to connect via wired today, I can't. I don't know if it was the Hardy upgrade or if my hardware is busted, but I'm sure it was working when I was in Gutsy because at that time I couldn't connect via wireless until I installed the broadcom stuff.

If I click "configure" in the Network applet, it says "Device does not exist". If I changed eth1 to eth0, it just says "Error"

Please help, don't know where to start here.



I checked my ifconfig now and it doesn't list eth0. 
```
$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:90:4b:91:c9:c2  
          inet addr:192.168.1.10  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::290:4bff:fe91:c9c2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:205713 errors:0 dropped:0 overruns:0 frame:0
          TX packets:163925 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:270563424 (258.0 MB)  TX bytes:21530706 (20.5 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1853 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1853 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:93388 (91.1 KB)  TX bytes:93388 (91.1 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-90-4B-91-C9-C2-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

You might check and see if your card exists by going into the Terminal and trying:
```
lspci -nn
lshw -C network
```
The first will list out our pci cards.  You should be able to find your wireless card and your wired card in the list.  If the wired card is not there, then you might have a hardware problem.

The second command will tell you the status of your network cards.  It should give you the logical name (eth0, eth1, etc...) and the driver information.  It might be possible that the wired driver is not loaded.

You can also just post those results and we can help try and figure what is happening.

---

### Post by MadKAT on 2008-09-14
Thanks for the reply!

Darn, my hardware may be broken. :-(
what do you think? Here are the outputs of the commands you suggested:
```
$ lspci -nn
00:00.0 Host bridge [0600]: ATI Technologies Inc Radeon 9100 IGP Host Bridge [1002:5833] (rev 02)
00:01.0 PCI bridge [0604]: ATI Technologies Inc Radeon 9100 IGP AGP Bridge [1002:5838]
00:13.0 USB Controller [0c03]: ATI Technologies Inc OHCI USB Controller #1 [1002:4347] (rev 01)
00:13.1 USB Controller [0c03]: ATI Technologies Inc OHCI USB Controller #2 [1002:4348] (rev 01)
00:14.0 SMBus [0c05]: ATI Technologies Inc SMBus [1002:4353] (rev 16)
00:14.1 IDE interface [0101]: ATI Technologies Inc Dual Channel Bus Master PCI IDE Controller [1002:4349]
00:14.3 ISA bridge [0601]: ATI Technologies Inc Unknown device [1002:434c]
00:14.4 PCI bridge [0604]: ATI Technologies Inc IXP200 3COM 3C920B Ethernet Controller [1002:4342]
00:14.5 Multimedia audio controller [0401]: ATI Technologies Inc IXP150 AC'97 Audio Controller [1002:4341]
00:14.6 Modem [0703]: ATI Technologies Inc IXP AC'97 Modem [1002:434d] (rev 01)
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10] [1002:4e50]
02:00.0 FireWire (IEEE 1394) [0c00]: Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link) [104c:8026]
02:02.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)
02:04.0 CardBus bridge [0607]: Texas Instruments PCI1620 PC Card Controller [104c:ac54] (rev 01)
02:04.1 CardBus bridge [0607]: Texas Instruments PCI1620 PC Card Controller [104c:ac54] (rev 01)
02:04.2 System peripheral [0880]: Texas Instruments PCI1620 Firmware Loading Function [104c:8201] (rev 01)
02:07.0 USB Controller [0c03]: NEC Corporation USB [1033:0035] (rev 43)
02:07.1 USB Controller [0c03]: NEC Corporation USB [1033:0035] (rev 43)
02:07.2 USB Controller [0c03]: NEC Corporation USB 2.0 [1033:00e0] (rev 04)

```

```
$ sudo lshw -C network
  *-network               
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network
       description: Wireless interface
       physical id: 2
       logical name: eth1
       serial: 00:90:4b:91:c9:c2
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.10 multicast=yes wireless=IEEE 802.11g

```

---

### Post by Ocelaris on 2008-09-16
Hi, sorry to barge in, but I'm in a similar situation, I have an onboard ethernet nic, a cheap Realtek and a nice dual nic PCI Intel E1000 card... 

I have my /etc/network/interfaces set up like I want, but how do I "turn on" the eth1 and eth2 ? IT looks like the "size 100MB/s" of the realtek is inferior to the "size: 1GB/s" of the intel card, I'm using this as a file server, should I instead use the intel card as my main port you think... The other I have set up for the VMWare network... Thanks, Bill

```
bill@server:~/vmware/vmware-server-distrib$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
#iface eth0 inet dhcp
iface eth0 inet static
address 192.168.0.10
netmask 255.255.255.0
gateway 192.168.0.1

#auto eth1
#iface eth1 inet dhcp
iface eth1 inet static
address 192.168.0.11
netmask 255.255.255.0
gateway 192.168.0.1

#auto eth2
#iface eth2 inet dhcp
iface eth2 inet static
address 192.168.0.12
netmask 255.255.255.0
gateway 192.168.0.1

```

> 

bill@server:~/vmware/vmware-server-distrib$ sudo lshw -C network
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:e0:4d:90:ef:bf
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full ip=192.168.0.10 latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=100MB/s


  *-network:0
       description: Ethernet interface
       product: 82546GB Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 6
       bus info: pci@0000:04:06.0
       logical name: eth1
       version: 03
       serial: 00:04:23:d5:5b:32
       capacity: 1GB/s
       width: 64 bits
       clock: 66MHz
       capabilities: pm pcix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.20-k2-NAPI firmware=N/A ip=192.168.0.11 latency=64 link=no mingnt=255 module=e1000 multicast=yes port=twisted pair


  *-network:1 DISABLED
       description: Ethernet interface
       product: 82546GB Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 6.1
       bus info: pci@0000:04:06.1
       logical name: eth2
       version: 03
       serial: 00:04:23:d5:5b:33
       size: 1GB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 66MHz
       capabilities: pm pcix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.20-k2-NAPI duplex=full firmware=N/A latency=64 link=no mingnt=255 module=e1000 multicast=yes port=twisted pair speed=1GB/s

---

### Post by Ayuthia on 2008-09-17
> **MadKAT said:**
> Thanks for the reply!

Darn, my hardware may be broken. :-(
what do you think? Here are the outputs of the commands you suggested:
```
$ lspci -nn
00:00.0 Host bridge [0600]: ATI Technologies Inc Radeon 9100 IGP Host Bridge [1002:5833] (rev 02)
00:01.0 PCI bridge [0604]: ATI Technologies Inc Radeon 9100 IGP AGP Bridge [1002:5838]
00:13.0 USB Controller [0c03]: ATI Technologies Inc OHCI USB Controller #1 [1002:4347] (rev 01)
00:13.1 USB Controller [0c03]: ATI Technologies Inc OHCI USB Controller #2 [1002:4348] (rev 01)
00:14.0 SMBus [0c05]: ATI Technologies Inc SMBus [1002:4353] (rev 16)
00:14.1 IDE interface [0101]: ATI Technologies Inc Dual Channel Bus Master PCI IDE Controller [1002:4349]
00:14.3 ISA bridge [0601]: ATI Technologies Inc Unknown device [1002:434c]
00:14.4 PCI bridge [0604]: ATI Technologies Inc IXP200 3COM 3C920B Ethernet Controller [1002:4342]
00:14.5 Multimedia audio controller [0401]: ATI Technologies Inc IXP150 AC'97 Audio Controller [1002:4341]
00:14.6 Modem [0703]: ATI Technologies Inc IXP AC'97 Modem [1002:434d] (rev 01)
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10] [1002:4e50]
02:00.0 FireWire (IEEE 1394) [0c00]: Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link) [104c:8026]
02:02.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)
02:04.0 CardBus bridge [0607]: Texas Instruments PCI1620 PC Card Controller [104c:ac54] (rev 01)
02:04.1 CardBus bridge [0607]: Texas Instruments PCI1620 PC Card Controller [104c:ac54] (rev 01)
02:04.2 System peripheral [0880]: Texas Instruments PCI1620 Firmware Loading Function [104c:8201] (rev 01)
02:07.0 USB Controller [0c03]: NEC Corporation USB [1033:0035] (rev 43)
02:07.1 USB Controller [0c03]: NEC Corporation USB [1033:0035] (rev 43)
02:07.2 USB Controller [0c03]: NEC Corporation USB 2.0 [1033:00e0] (rev 04)

```

```
$ sudo lshw -C network
  *-network               
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network
       description: Wireless interface
       physical id: 2
       logical name: eth1
       serial: 00:90:4b:91:c9:c2
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.10 multicast=yes wireless=IEEE 802.11g

```

Sorry for the late reply, but I am not for sure if that is the case, but it kinda looks that way.  If you are dual-booting, you could try and see if it works on the other OS.  If you don't you could try the liveCD and see if you can see your card there.

---

### Post by MadKAT on 2008-09-24
Yeah, i guess it's officially a broken hardware. The LiveCD doesn't detect it either. And neither in Windows (although I dont know if it ever detected it before since I never connect the internet on the very few occasions I boot on Windows).

Thanks for the reply.

---

### Post by shanix on 2008-09-24
If you are running the version 8.10, for your Gigabit Ethernet card, you might be hit by this bug:

[intrepid] 2.6.27 e1000e driver places Intel ICH8 and ICH9 gigE chipsets at risk
[https://bugs.launchpad.net/ubuntu/intrepid/+source/linux/+bug/263555](https://bugs.launchpad.net/ubuntu/intrepid/+source/linux/+bug/263555)

Rolling back to the previous kernel version will be the work around for now.

---

### Post by Iowan on 2008-09-24
> **Ocelaris said:**
>  but how do I "turn on" the eth1 and eth2 Uncomment (delete the #) the "auto" lines for eth1 and eth2... or add them to the existing "auto" line (eg. **auto lo eth0 eth1 eth2**).

---

### Post by MadKAT on 2008-10-03
> **shanix said:**
> If you are running the version 8.10, for your Gigabit Ethernet card, you might be hit by this bug:

[intrepid] 2.6.27 e1000e driver places Intel ICH8 and ICH9 gigE chipsets at risk
[https://bugs.launchpad.net/ubuntu/intrepid/+source/linux/+bug/263555](https://bugs.launchpad.net/ubuntu/intrepid/+source/linux/+bug/263555)

Rolling back to the previous kernel version will be the work around for now.

Hmmmm.... I just read about this bug. Interesting...

However, I'm only on 8.04 with the 2.6.24. Is it possible that this was also the problem and it existed already in this version? Right now, I don't really have a clue, I can't even remember if my system used the e1000 driver at all, because it just worked before and I didn't bother to check what brand it was. 

:cry:

---

### Post by Ayuthia on 2008-10-03
> **MadKAT said:**
> 
what do you think? Here are the outputs of the commands you suggested:
```
$ lspci -nn
00:14.4 PCI bridge [0604]: ATI Technologies Inc IXP200 3COM 3C920B Ethernet Controller [1002:4342]

```

Can you try the following:
```
lshw -C bridge
```
I think that your ethernet card is listed as a bridge.  I forgot that recently the pci information was updated and it changed some ethernet controllers to bridges.  

So I think the item that I snipped from your lspci -nn info is your wired card.

---

### Post by MadKAT on 2008-10-04
Here's the output of lshw -C bridge. 
I see a "IXP200 3COM 3C920B Ethernet Controller" but I have no idea what any of it means though :)

```

$ sudo lshw -C bridge
  *-pci                   
       description: Host bridge
       product: Radeon 9100 IGP Host Bridge
       vendor: ATI Technologies Inc
       physical id: 100
       bus info: pci@0000:00:00.0
       version: 02
       width: 32 bits
       clock: 66MHz
       configuration: driver=agpgart-ati latency=64 module=ati_agp
     *-pci:0
          description: PCI bridge
          product: Radeon 9100 IGP AGP Bridge
          vendor: ATI Technologies Inc
          physical id: 1
          bus info: pci@0000:00:01.0
          version: 00
          width: 32 bits
          clock: 66MHz
          capabilities: pci normal_decode bus_master
     *-isa
          description: ISA bridge
          product: ATI Technologies Inc
          vendor: ATI Technologies Inc
          physical id: 14.3
          bus info: pci@0000:00:14.3
          version: 00
          width: 32 bits
          clock: 66MHz
          capabilities: isa bus_master
          configuration: latency=0
     *-pci:1
          description: PCI bridge
          product: IXP200 3COM 3C920B Ethernet Controller
          vendor: ATI Technologies Inc
          physical id: 14.4
          bus info: pci@0000:00:14.4
          version: 00
          width: 32 bits
          clock: 66MHz
          capabilities: pci subtractive_decode bus_master
        *-pcmcia:0
             description: CardBus bridge
             product: PCI1620 PC Card Controller
             vendor: Texas Instruments
             physical id: 4
             bus info: pci@0000:02:04.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192 module=yenta_socket
        *-pcmcia:1
             description: CardBus bridge
             product: PCI1620 PC Card Controller
             vendor: Texas Instruments
             physical id: 4.1
             bus info: pci@0000:02:04.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192 module=yenta_socket

```

---

### Post by Ayuthia on 2008-10-04
> **MadKAT said:**
> Here's the output of lshw -C bridge. 
I see a "IXP200 3COM 3C920B Ethernet Controller" but I have no idea what any of it means though :)

```

$ sudo lshw -C bridge
  *-pci                   
       description: Host bridge
       product: Radeon 9100 IGP Host Bridge
       vendor: ATI Technologies Inc
       physical id: 100
       bus info: pci@0000:00:00.0
       version: 02
       width: 32 bits
       clock: 66MHz
       configuration: driver=agpgart-ati latency=64 module=ati_agp
     *-pci:0
          description: PCI bridge
          product: Radeon 9100 IGP AGP Bridge
          vendor: ATI Technologies Inc
          physical id: 1
          bus info: pci@0000:00:01.0
          version: 00
          width: 32 bits
          clock: 66MHz
          capabilities: pci normal_decode bus_master
     *-isa
          description: ISA bridge
          product: ATI Technologies Inc
          vendor: ATI Technologies Inc
          physical id: 14.3
          bus info: pci@0000:00:14.3
          version: 00
          width: 32 bits
          clock: 66MHz
          capabilities: isa bus_master
          configuration: latency=0
     *-pci:1
          description: PCI bridge
          product: IXP200 3COM 3C920B Ethernet Controller
          vendor: ATI Technologies Inc
          physical id: 14.4
          bus info: pci@0000:00:14.4
          version: 00
          width: 32 bits
          clock: 66MHz
          capabilities: pci subtractive_decode bus_master
        *-pcmcia:0
             description: CardBus bridge
             product: PCI1620 PC Card Controller
             vendor: Texas Instruments
             physical id: 4
             bus info: pci@0000:02:04.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192 module=yenta_socket
        *-pcmcia:1
             description: CardBus bridge
             product: PCI1620 PC Card Controller
             vendor: Texas Instruments
             physical id: 4.1
             bus info: pci@0000:02:04.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192 module=yenta_socket

```
Well, I looked around for some information about this and did stumble upon another person who has this ethernet controller and they also had an ethernet interface card which was their wired connection.

If you look at where the cord is plugged into the ethernet card, are there any lights on and does the router have any lights to reflect that it sees the connection?  If there are no lights, then it might be that the card is bad since there are no lights and the system is not seeing the card.

---

### Post by MadKAT on 2008-10-04
Awww... no, there are no lights when the wires are plugged in, and no activity on the router port... :cry:

Thanks for your efforts trying to help me out. Truly appreciate it.

---

### Post by fitzman49 on 2008-10-04
See the end of this thread to get intel e1000 devices working again

[http://ubuntuforums.org/showthread.php?t=927943]("http://ubuntuforums.org/showthread.php?t=927943")

---

### Post by msound on 2009-01-12
I had a similar problem with a brand new acer power series machine on which I was trying to install ubuntu server 8.10. After a lot of searching, I installed windoze XP and that too did not detect any network card. I concluded it is a hardware problem and called up customer care and they advised me to go to BIOS settings and load default settings, and eth0 appeared immediately. Even though the problem is not with Ubuntu, I thought it might be helpful for someone who might be facing same issue.

Disclaimer: Since it was a brand new machine, it was fine for me to load defaults, as I did not have fear of losing any settings. This might work differently for you!

---

