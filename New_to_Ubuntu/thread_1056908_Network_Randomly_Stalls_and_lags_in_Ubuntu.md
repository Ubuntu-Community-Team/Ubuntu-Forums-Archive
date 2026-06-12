---
title: "Network Randomly Stalls and lags in Ubuntu"
date: 2009-02-01
forum: New to Ubuntu
---

### Post by 133794m3r on 2009-02-01
Ok, i'm on a compaq presario m2301nr laptop. I hate it it's old. But anyway to the point. Lately the network has been randomly lagging and stalling. I talk to my roomate who's on teh same connection and asked him if he's having the same issues. And he is not. This has just started happening for the past few days. I'm on ubuntu Intrepid. Is there anyway to fix this?

---

### Post by 133794m3r on 2009-02-02
bump

---

### Post by Praxicoide on 2009-02-02
Are you connected using a wireless card? If so, do you know the type of card?

can you post the output each of the following?:

```
lspci
lsusb
iwconfig
```

---

### Post by 133794m3r on 2009-02-02
I'm connectd through an ethernet cable.

lspi
```
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 80)
00:14.6 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
05:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
05:09.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
```
lsusb
```
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

iwconfig
```
 iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"Scytale"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

---

### Post by Praxicoide on 2009-02-02
So it's your wired connection that's stalling? Apologies for assuming otherwise. Could you post the output of the following:

```
ifconfig
```

Some people have experienced internet lagging because of the Ipv6 module. Maybe that is your case as well. You can try to disable this module and checking if the problem persists. 

If you want to try this, then you need to edit your /etc/modprobe.d/aliases file. If you're using ubuntu that's by typing the following in a terminal:

```
gksudo gedit /etc/modprobe.d/aliases
```

(change gedit for kate in Kubuntu or mousepad in xubuntu)

in the file check for the part that says the following:

```
net-pf-10 ipv6
```

and change it to 

```
net-pf-10 ipv6 off
```

And save. You will need to reboot for this to take effect.

---

### Post by 133794m3r on 2009-02-02
Also i tried that thing you said.

ifconfig
```
eth0      Link encap:Ethernet  HWaddr 00:1b:24:40:f8:46  
          inet addr:69.26.207.170  Bcast:69.26.207.255  Mask:255.255.255.0
          inet6 addr: fec0::8:21b:24ff:fe40:f846/64 Scope:Site
          inet6 addr: 2002:451a:cf07:8:21b:24ff:fe40:f846/64 Scope:Global
          inet6 addr: 2002:451a:cd2a:8:21b:24ff:fe40:f846/64 Scope:Global
          inet6 addr: 2002:451a:cfb8:8:21b:24ff:fe40:f846/64 Scope:Global
          inet6 addr: fe80::21b:24ff:fe40:f846/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3141 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1295 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1443693 (1.4 MB)  TX bytes:238491 (238.4 KB)
          Interrupt:18 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:598 (598.0 B)  TX bytes:598 (598.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:14:a5:22:aa:e1  
          inet6 addr: fe80::214:a5ff:fe22:aae1/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:208 (208.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-14-A5-22-AA-E1-61-65-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

---

