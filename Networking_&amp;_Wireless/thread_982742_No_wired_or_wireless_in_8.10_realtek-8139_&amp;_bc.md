---
title: "No wired or wireless in 8.10 realtek-8139 &amp; bcm4306"
date: 2008-11-15
forum: Networking &amp; Wireless
---

### Post by Jive Turkey on 2008-11-15
I just installed Intrepid Ibex amd64 on my laptop, in 7.10 and 8.04 I could connect the ethernet port to my router and get the bcm43xx fw cutter thing and it would work.  In 8.10 my realtek ethernet port doesn't work either. so I can't dl the fwcutter/bcm driver at all.  It sure would be nice if the restricted driver manager would offer a url to the user so they could get it on a working computer after cleverly trying to dl the package with no internet connection.  ...or better yet just put the package on the install cd.  Anyway, here are some outputs that might help someone offer a solution, many thanks

```
:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0f:b0:4a:87:3c  
          inet6 addr: fe80::20f:b0ff:fe4a:873c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1203 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:133530 (133.5 KB)  TX bytes:3546 (3.5 KB)
          Interrupt:18 Base address:0x7000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:242 errors:0 dropped:0 overruns:0 frame:0
          TX packets:242 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15328 (15.3 KB)  TX bytes:15328 (15.3 KB)

```
```
[COLOR="#c0c0c0"]:~$ lspci
00:00.0 Host bridge: nVidia Corporation nForce3 Host Bridge (rev a4)
00:01.0 ISA bridge: nVidia Corporation nForce3 LPC Bridge (rev a6)
00:01.1 SMBus: nVidia Corporation nForce3 SMBus (rev a4)
00:02.0 USB Controller: nVidia Corporation nForce3 USB 1.1 (rev a5)
00:02.1 USB Controller: nVidia Corporation nForce3 USB 1.1 (rev a5)
00:02.2 USB Controller: nVidia Corporation nForce3 USB 2.0 (rev a2)
00:06.0 Multimedia audio controller: nVidia Corporation nForce3 Audio (rev a2)
00:06.1 Modem: nVidia Corporation nForce3 Audio (rev a2)
00:08.0 IDE interface: nVidia Corporation nForce3 IDE (rev a5)
00:0a.0 PCI bridge: nVidia Corporation nForce3 PCI Bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation nForce3 AGP Bridge (rev a4)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 440 Go 64M] (rev a3)
02:00.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)[/COLOR]
[COLOR="Red"]02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)[/COLOR][COLOR="Silver"]
02:04.0 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01)
02:04.1 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01)
02:04.2 System peripheral: Texas Instruments PCI1620 Firmware Loading Function (rev 01)[/COLOR]

```
```
:~$ sudo lshw -C network
[sudo] ...
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 10
       serial: 00:0f:b0:4a:87:3c
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
  *-network:1
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
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:90:4b:a8:ae:fa
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: a6:0f:97:bd:5b:5c
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

---

### Post by iponeverything on 2008-11-15
eth0      Link encap:Ethernet  HWaddr 00:0f:b0:4a:87:3c  
          inet6 addr: fe80::20f:b0ff:fe4a:873c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
[COLOR="Red"]          RX packets:1203 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:133530 (133.5 KB)  TX bytes:3546 (3.5 KB)
[/COLOR]          Interrupt:18 Base address:0x7000 

It appears to be working..

Try this -- run:

```
sudo dhclient
```

If that fails to acquire an ip, Address it yourself:

```
sudo ifconfig eth0 192.168.1.22 netmask 255.255.255.0 gw 192.168.1.1

```

Where the ip address netmask and gw are appropriate for your router.

---

### Post by Jive Turkey on 2008-11-15
The first command didn't work out after polling each interface, no response from the router.

heres the output from the second command:
```
:~$ sudo ifconfig eth0 192.168.1.105 netmask 255.255.255.0 gw 192.168.1.1
gw: Unknown host
ifconfig: `--help' gives usage information.

```

My other computer sees 192.168.1.1(the router) just fine.  I use address reservation that binds that mac address to that IP.  I'd prefer static IP but then if I have visitors it gets too tricky for them to connect.  It also becomes a PITA to manage shared folders on my network and if I have to switch to public wifi it's easier if I am already on dhcp from the start.

---

### Post by iponeverything on 2008-11-15
> **Jive Turkey said:**
> The first command didn't work out after polling each interface, no response from the router.

heres the output from the second command:
```
:~$ sudo ifconfig eth0 192.168.1.105 netmask 255.255.255.0 gw 192.168.1.1
gw: Unknown host
ifconfig: `--help' gives usage information.

```

My other computer sees 192.168.1.1(the router) just fine.  I use address reservation that binds that mac address to that IP.  I'd prefer static IP but then if I have visitors it gets too tricky for them to connect.  It also becomes a PITA to manage shared folders on my network and if I have to switch to public wifi it's easier if I am already on dhcp from the start.

sorry about that.. do

```
sudo ifconfig eth0 192.168.1.105 netmask 255.255.255.0 
sudo route add default gw 192.168.1.1
```

---

### Post by Jive Turkey on 2008-11-15
> **iponeverything said:**
> sorry about that.. do

```
sudo ifconfig eth0 192.168.1.105 netmask 255.255.255.0 
sudo route add default gw 192.168.1.1
```

That didn't work either I'm afraid, the first command made the nm applet look busy for a sec.  The second didn't really seem to do anything, no errors though.

The good news is I got the b43 fwcutter thing going after finding some files it needed to work.  The eternet plug would be nice but it isn't critical for my laptop.  Now I'm moving on to the nvidia 440go video drivers.  Thanks for your help.

---

