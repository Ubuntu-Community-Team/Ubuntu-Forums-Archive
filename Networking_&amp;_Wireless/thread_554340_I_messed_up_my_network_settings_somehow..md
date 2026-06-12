---
title: "I messed up my network settings somehow."
date: 2007-09-18
forum: Networking &amp; Wireless
---

### Post by Auax on 2007-09-18
And now I can only connect to my network in Windows. -_-

Is there a way to completely revert all settings back to the defaults?

---

### Post by Auax on 2007-09-20
Help?

---

### Post by noob12 on 2007-09-20
I don't know of anything to reset things to defaults.  You'll need to reconfigure things.

Post these to let people see what you have and how you are configured so far:
```

lspci -nn

sudo lshw -C network

ifconfig -a

cat /etc/network/interfaces

```

If you post the **ipconfig /all** and **route print** output from Windows, it can help suggest the right settings for your Ubuntu host.

---

### Post by Auax on 2007-09-20
Ok, here's the windows stuff:

```

Microsoft Windows [Version 6.0.6000]
Copyright (c) 2006 Microsoft Corporation.  All rights reserved.

C:\Users\admin>ipconfig /all

Windows IP Configuration

   Host Name . . . . . . . . . . . . : Hades
   Primary Dns Suffix  . . . . . . . :
   Node Type . . . . . . . . . . . . : Hybrid
   IP Routing Enabled. . . . . . . . : No
   WINS Proxy Enabled. . . . . . . . : No
   DNS Suffix Search List. . . . . . : hsd1.or.comcast.net.

Wireless LAN adapter Wireless Network Connection:

   Connection-specific DNS Suffix  . : hsd1.or.comcast.net.
   Description . . . . . . . . . . . : Atheros AR5005G Wireless Network Adapter
   Physical Address. . . . . . . . . : 00-19-7D-68-23-28
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes
   Link-local IPv6 Address . . . . . : fe80::6cd3:e622:e625:7395%9(Preferred)
   IPv4 Address. . . . . . . . . . . : 192.168.0.101(Preferred)
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Lease Obtained. . . . . . . . . . : Thursday, September 20, 2007 4:57:58 AM
   Lease Expires . . . . . . . . . . : Thursday, September 27, 2007 4:58:57 AM
   Default Gateway . . . . . . . . . : 192.168.0.103
   DHCP Server . . . . . . . . . . . : 192.168.0.103
   DHCPv6 IAID . . . . . . . . . . . : 151001469
   DNS Servers . . . . . . . . . . . : 192.168.0.103
   NetBIOS over Tcpip. . . . . . . . : Enabled

Ethernet adapter Local Area Connection:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Realtek RTL8139/810x Family Fast Ethernet
 NIC
   Physical Address. . . . . . . . . : 00-16-D4-AF-12-95
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes

Tunnel adapter Local Area Connection* 6:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : isatap.{EDD10845-C906-44E4-9CDB-EE18B60FC
688}
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes

Tunnel adapter Local Area Connection* 9:

   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Teredo Tunneling Pseudo-Interface
   Physical Address. . . . . . . . . : 02-00-54-55-4E-01
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes
   IPv6 Address. . . . . . . . . . . : 2001:0:4136:e38e:800:2ba3:3f57:ff9a(Prefe
rred)
   Link-local IPv6 Address . . . . . : fe80::800:2ba3:3f57:ff9a%11(Preferred)
   Default Gateway . . . . . . . . . : ::
   NetBIOS over Tcpip. . . . . . . . : Disabled

Tunnel adapter Local Area Connection* 10:

   Connection-specific DNS Suffix  . : hsd1.or.comcast.net.
   Description . . . . . . . . . . . : isatap.hsd1.or.comcast.net.
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes
   Link-local IPv6 Address . . . . . : fe80::5efe:192.168.0.101%12(Preferred)
   Default Gateway . . . . . . . . . :
   DNS Servers . . . . . . . . . . . : 192.168.0.103
   NetBIOS over Tcpip. . . . . . . . : Disabled

```
```

Microsoft Windows [Version 6.0.6000]
Copyright (c) 2006 Microsoft Corporation.  All rights reserved.

C:\Users\admin>route print
===========================================================================
Interface List
  9 ...00 19 7d 68 23 28 ...... Atheros AR5005G Wireless Network Adapter
  8 ...00 16 d4 af 12 95 ...... Realtek RTL8139/810x Family Fast Ethernet NIC
  1 ........................... Software Loopback Interface 1
 10 ...00 00 00 00 00 00 00 e0  isatap.{EDD10845-C906-44E4-9CDB-EE18B60FC688}
 11 ...02 00 54 55 4e 01 ...... Teredo Tunneling Pseudo-Interface
 12 ...00 00 00 00 00 00 00 e0  isatap.hsd1.or.comcast.net.
===========================================================================

IPv4 Route Table
===========================================================================
Active Routes:
Network Destination        Netmask          Gateway       Interface  Metric
          0.0.0.0          0.0.0.0    192.168.0.103    192.168.0.101     25
        127.0.0.0        255.0.0.0         On-link         127.0.0.1    306
        127.0.0.1  255.255.255.255         On-link         127.0.0.1    306
  127.255.255.255  255.255.255.255         On-link         127.0.0.1    306
      192.168.0.0    255.255.255.0         On-link     192.168.0.101    281
    192.168.0.101  255.255.255.255         On-link     192.168.0.101    281
    192.168.0.255  255.255.255.255         On-link     192.168.0.101    281
        224.0.0.0        240.0.0.0         On-link         127.0.0.1    306
        224.0.0.0        240.0.0.0         On-link     192.168.0.101    281
  255.255.255.255  255.255.255.255         On-link         127.0.0.1    306
  255.255.255.255  255.255.255.255         On-link     192.168.0.101    281
===========================================================================
Persistent Routes:
  None

IPv6 Route Table
===========================================================================
Active Routes:
 If Metric Network Destination      Gateway
 11     18 ::/0                     On-link
  1    306 ::1/128                  On-link
 11     18 2001::/32                On-link
 11    266 2001:0:4136:e38e:800:2ba3:3f57:ff9a/128
                                    On-link
  9    281 fe80::/64                On-link
 11    266 fe80::/64                On-link
 12    286 fe80::5efe:192.168.0.101/128
                                    On-link
 11    266 fe80::800:2ba3:3f57:ff9a/128
                                    On-link
  9    281 fe80::6cd3:e622:e625:7395/128
                                    On-link
  1    306 ff00::/8                 On-link
 11    266 ff00::/8                 On-link
  9    281 ff00::/8                 On-link
===========================================================================
Persistent Routes:
  None

```

I'll boot into Kubuntu and copy the other stuff to my windows partition, then boot back into Windows and post it...

---

### Post by Auax on 2007-09-20
Linux stuff:

```
administrator@Hades:~$ lspci -nn
00:00.0 Host bridge [0600]: ATI Technologies Inc RS480 Host Bridge [1002:5950] (rev 10)
00:01.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a3f]
00:04.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a36]
00:05.0 PCI bridge [0604]: ATI Technologies Inc Unknown device [1002:5a37]
00:12.0 IDE interface [0101]: ATI Technologies Inc ATI 4379 Serial ATA Controller [1002:4379] (rev 80)
00:13.0 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB Host Controller [1002:4374] (rev 80)
00:13.1 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB Host Controller [1002:4375] (rev 80)
00:13.2 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB2 Host Controller [1002:4373] (rev 80)
00:14.0 SMBus [0c05]: ATI Technologies Inc IXP SB400 SMBus Controller [1002:4372] (rev 83)
00:14.1 IDE interface [0101]: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI [1002:4376] (rev 80)
00:14.2 Audio device [0403]: ATI Technologies Inc SB450 HDA Audio [1002:437b] (rev 01)
00:14.3 ISA bridge [0601]: ATI Technologies Inc IXP SB400 PCI-ISA Bridge [1002:4377] (rev 80)
00:14.4 PCI bridge [0604]: ATI Technologies Inc IXP SB400 PCI-PCI Bridge [1002:4371] (rev 80)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RS482 [Radeon Xpress 200M] [1002:5975]
06:01.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
06:02.0 Ethernet controller [0200]: Atheros Communications, Inc. AR5005G 802.11abg NIC [168c:001a] (rev 01)
06:04.0 CardBus bridge [0607]: ENE Technology Inc CB-712/4 Cardbus Controller [1524:1412] (rev 10)
06:04.1 FLASH memory [0501]: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller [1524:0530] (rev 01)
06:04.2 Generic system peripheral [0805]: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller [1524:0550] (rev 01)
06:04.3 FLASH memory [0501]: ENE Technology Inc FLASH memory: ENE Technology Inc: [1524:0520] (rev 01)
06:04.4 FLASH memory [0501]: ENE Technology Inc Unknown device [1524:0551] (rev 01)

``` 


```
administrator@Hades:~$ sudo lshw -C network
Password:
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@06:01.0
       logical name: eth0
       version: 10
       serial: 00:16:d4:af:12:95
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
       resources: ioport:a000-a0ff iomemory:c0210000-c02100ff irq:21
  *-network:1
       description: Wireless interface
       product: AR5005G 802.11abg NIC
       vendor: Atheros Communications, Inc.
       physical id: 2
       bus info: pci@06:02.0
       logical name: wifi0
       version: 01
       serial: 00:19:7d:68:23:28
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci driverversion=0.9.4.5 (0.9.3.1) latency=168 maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11g
       resources: iomemory:c0200000-c020ffff irq:22

```

```
administrator@Hades:~$ ifconfig -a
ath0      Link encap:Ethernet  HWaddr 00:19:7D:68:23:28  
          inet6 addr: fe80::219:7dff:fe68:2328/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

eth0      Link encap:Ethernet  HWaddr 00:16:D4:AF:12:95  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:21 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:32 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2190 (2.1 KiB)  TX bytes:2190 (2.1 KiB)

wifi0     Link encap:UNSPEC  HWaddr 00-19-7D-68-23-28-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1917 errors:0 dropped:0 overruns:0 frame:394
          TX packets:267 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:138056 (134.8 KiB)  TX bytes:12282 (11.9 KiB)
          Interrupt:22 

```


```
administrator@Hades:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
```

---

### Post by noob12 on 2007-09-20
OK.  Can you clarify if you are talking about connecting via your wired interface or your wireless?  It looks like wireless.  

Regarding your wired interface.   It shows no link detected and the interface is not up. Judging from the agreement from the Windows side, this is really the case.  You aren't plugged into a wire.   It is also not configured to be brought up automatically. Please confirm.

Were you using the regular NetworkManager that ships with Ubuntu?  or did you install something else, like wicd?  If you are using NetworkManager, I would recommend that you remove all of the configuration stanzas you have in /etc/network/interfaces *except* the first one for the loopback (lo).

For your wireless interface, it seems to have the ath_pci driver associated with it already and the same version that ships in the linux-restricted-modules package with Ubuntu.   If you don't remember replacing that with something else, then this is fine.  If you remember building newer versions of the madwifi drivers then we will need to go back and do that, but I think these will work reasonably well with your device and NM.

Your wireless interface didn't get a proper DHCP address from your router.
Can you post the output of
```

sudo iwlist scan

iwconfig

```

Can you describe how you are trying to connect and what happens when you try to connect?

---

### Post by Auax on 2007-09-21
Yeah, I just use wireless, and have always connected via ath0 (My atheros card). 

Yes, I use Network Manager

I connect to the network fine now, but still can't get online.

I'll boot into Kubuntu and post that stuff in a while.

---

### Post by noob12 on 2007-09-21
OK.  Then instead of the above, after you connect wireless, can you collect the output of these,

```

ifconfig -a

route -n

cat /etc/resolv.conf

```

Ping your router.  If you do not know your router address, find the UG line in the route -n output.  The router's address is in the second column.  If there is no UG row, that's a problem. 

Ping one external point.  Here's an OpenDNS server address you can just try to ping:
**ping 208.67.222.222**

---

