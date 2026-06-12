---
title: "Trouble getting D-Link DWA-548 PCIe Wi-Fi card working!"
date: 2014-06-20
forum: Networking &amp; Wireless
---

### Post by Steve_Par on 2014-06-20
Seems that I have a very similar issue to the one described [here]("http://ubuntuforums.org/showthread.php?t=2071830").

I've just upgraded to 14.04 64 bit in an effort to get ndiswrapper to work with my D-Link DWA-548 PCIe Wi-Fi card using the WinXPX64 driver, but it doesn't seem to like it.

ndiswrapper -l shows the following response:

```
drt2860 : driver installed
    device (1814:5392) present (alternate driver: rt2800pci)
```

lshw -C network gives the following:

```
*-network               
       description: Ethernet interface
       product: NetXtreme BCM5764M Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 10
       serial: d0:27:88:07:63:94
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.134 duplex=full firmware=5764m-v3.35 ip=192.168.100.2 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:45 memory:feaf0000-feafffff
  *-network UNCLAIMED
       description: Network controller
       product: RT5392 PCIe Wireless Network Adapter
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:febf0000-febfffff

```

nm-tool returns:

```
NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 3] -------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             connected
  Default:           yes
  HW Address:        D0:27:88:07:63:94

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.100.2
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.100.1

    DNS:             192.168.100.1

```


lspci returns:

```
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
00:1a.0 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
00:1a.1 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
00:1a.2 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
00:1a.7 USB controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 1
00:1c.1 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 2
00:1c.3 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 4
00:1d.0 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
00:1d.1 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
00:1d.2 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
00:1d.7 USB controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller
00:1f.2 IDE interface: Intel Corporation 82801JI (ICH10 Family) 4 port SATA IDE Controller #1
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
00:1f.5 IDE interface: Intel Corporation 82801JI (ICH10 Family) 2 port SATA IDE Controller #2
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5764M Gigabit Ethernet PCIe (rev 10)
03:00.0 Network controller: Ralink corp. RT5392 PCIe Wireless Network Adapter


```

I could follow the advice given by [**[COLOR=#000000]chili555[/COLOR]**]("http://ubuntuforums.org/member.php?u=35909") but I don't know what > I assume you have the downloaded file on your Desktop. Right-click it  and select 'extract here.' It is handily a bz2.bz2 file, so you may have  to 'extract here' a couple of times. Good work, Realtek! Now open a  terminal and do: refers to, so I can't.

---

### Post by chili555 on 2014-06-20
It seems that a driver already exists for your device, rt2800pci. Did it not work as expected?

Let's verify your device further:```
lspci -nn | grep 0280
```Thanks.

---

### Post by Steve_Par on 2014-06-20
Thanks for your prompt reply, it's much appreciated!

```
03:00.0 Network controller [0280]: Ralink corp. RT5392 PCIe Wireless Network Adapter [1814:5392]
```

---

### Post by chili555 on 2014-06-20
Your device is covered by rt2800pci:```
modinfo rt2800pci | grep 5392
alias:          pci:v0000[COLOR="#FF0000"]1814[/COLOR]d0000[COLOR="#FF0000"]5392[/COLOR]sv*sd*bc*sc*i*
```What was it that didn't work as expected?

---

### Post by Steve_Par on 2014-06-20
Well, when I disconnect the wired network and try and connect on the wireless network it doesn't even attempt to connect.  Other device that I have have no problem in connecting to the wifi.  Furthermore, under network connections 'Wireless connection 1' under last used indicates never, which is consistent with my experience.  Also, if I run iwconfig, shouldn't it show an > ra0  ?

iwconfig though returns:

```
eth0      no wireless extensions.

lo        no wireless extensions.
```

ifconfig return:

```
eth0      Link encap:Ethernet  HWaddr d0:27:88:07:63:94  
          inet addr:192.168.100.2  Bcast:192.168.100.255  Mask:255.255.255.0
          inet6 addr: fe80::d227:88ff:fe07:6394/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:153168 errors:0 dropped:0 overruns:0 frame:0
          TX packets:134917 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:153394166 (153.3 MB)  TX bytes:17278577 (17.2 MB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:14218 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14218 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1289639 (1.2 MB)  TX bytes:1289639 (1.2 MB)

```

I would have expected, if the driver was properly installed, if I attempted to connect to my wifi it would at least attempt to do something, but it never has, leading me to think this is actually a driver issue.

---

### Post by chili555 on 2014-06-20
Let's load the driver and check the log for interesting clues:```
sudo modprobe rt2800pci
dmesg | grep rt2
```Please do so with the ethernet detached, capture and post any errors, warnings, etc. Thanks.> Also, if I run iwconfig, shouldn't it show an
ra0For either ndiswrapper or rt2800pci, it would be wlan0; in any event, it is missing.

---

### Post by Steve_Par on 2014-06-20
You're a gentleman, Sir........

ifconfig returns: 

```
eth0      Link encap:Ethernet  HWaddr d0:27:88:07:63:94  
          inet6 addr: fe80::d227:88ff:fe07:6394/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:278922 errors:0 dropped:0 overruns:0 frame:0
          TX packets:245313 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:254752455 (254.7 MB)  TX bytes:36602020 (36.6 MB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:18745 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18745 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1763870 (1.7 MB)  TX bytes:1763870 (1.7 MB)

wlan0     Link encap:Ethernet  HWaddr c4:a8:1d:03:66:f2  
          inet addr:192.168.100.4  Bcast:192.168.100.255  Mask:255.255.255.0
          inet6 addr: fe80::c6a8:1dff:fe03:66f2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3092 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2966 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3049649 (3.0 MB)  TX bytes:377165 (377.1 KB)


```

This message is being brought to you over wifi!

Thank you kindly.  If you find yourself in sunny Bangkok, let me buy you a beer!

---

### Post by chili555 on 2014-06-21
Glad it's working! If you have any other troubles with it, post back and we'll be happy to help.

---

