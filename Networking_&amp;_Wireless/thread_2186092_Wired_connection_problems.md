---
title: "Wired connection problems"
date: 2013-11-05
forum: Networking &amp; Wireless
---

### Post by avents on 2013-11-05
I have cable and a router. But quite often there is no WiFi. 
But after a   reboot everything is fine again.
This has become a frequent occurence.
Is the router failing? 
Thanks

The machine is an older Dell desktop with a router.

```
 lspci
00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 04)
00:1d.0 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.3 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
00:1d.7 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d4)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04)
00:1f.2 IDE interface: Intel Corporation 82801FR/FRW (ICH6R/ICH6RW) SATA Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
03:02.0 Communication controller: Conexant Systems, Inc. HSF 56k Data/Fax Modem
03:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller (rev 04)



```
[CODE
~$ lsusb
Bus 001 Device 004: ID 0644:0200 TEAC Corp. All-In-One Multi-Card Reader CA200/B/S
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 0461:4d15 Primax Electronics, Ltd Dell Optical Mouse
Bus 002 Device 002: ID 413c:2003 Dell Computer Corp. Keyboard
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub][/CODE]

---

### Post by varunendra on 2013-11-06
> **avents said:**
> I have cable and a router. But quite often there is no **[COLOR="#FF0000"]WiFi[/COLOR]**.

Was that a typo or do you really mean **[COLOR="#FF0000"]WiFi[/COLOR]**? The outputs show no wireless devices, so I think you mean your Ethernet (cable) connection.

If so, please install ethtool -
```
sudo apt-get install ethtool
```
and post back the outputs of -
```
sudo ethtool eth0
ifconfig -a
nm-tool
```

As a sanity check, try replacing the cable with a fresh one. More than often the wired connection problems are caused by bad contacts.

---

### Post by avents on 2013-11-06
Thanks varun, it's indeed the Ethernet. I will also check the cables, but for me it is hard to get to the back, so as soon as somebody comes in I'll check the cables.

```
ethtool is already the newest version.
-------------------------------------
:~$ sudo ethtool eth0
Settings for eth0:
    Supported ports: [ TP MII ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
    Supported pause frame use: No
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
    Advertised pause frame use: Symmetric
    Advertised auto-negotiation: Yes
    Link partner advertised link modes:  10baseT/Half 10baseT/Full 
                                         100baseT/Half 100baseT/Full 
    Link partner advertised pause frame use: Symmetric
    Link partner advertised auto-negotiation: Yes
    Speed: 100Mb/s
    Duplex: Full
    Port: MII
    PHYAD: 1
    Transceiver: internal
    Auto-negotiation: on
    Supports Wake-on: g
    Wake-on: g
    Current message level: 0x00000007 (7)
                   drv probe link
    Link detected: yes
-----------------------------------------------------------------
:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:xx.....  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:20ff:febc:63da/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:823 errors:0 dropped:0 overruns:0 frame:0
          TX packets:870 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:692966 (692.9 KB)  TX bytes:120321 (120.3 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:228 errors:0 dropped:0 overruns:0 frame:0
          TX packets:228 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:22047 (22.0 KB)  TX bytes:22047 (22.0 KB)
-------------------------------------------
:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            e100
  State:             connected
  Default:           yes
  HW Address:        00:xx.......

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.100
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1

 
```

---

### Post by varunendra on 2013-11-06
> **avents said:**
> 
```

    **Supported ports: [ TP MII ]**
....
    Advertised auto-negotiation: **Yes**
....
    Port: MII
....
    Auto-negotiation: **on**
..
-----------------------------------------------------------------
:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:xx.....  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          **inet6 addr: fe80::213:20ff:febc:63da/64 Scope:Link**
 
```

Based on above quoted parts, I think there are exactly four things I can suggest, in no particular order -

[LIST=1]
[*]Easiest first - Try setting IPv6 to "Ignore" in Network Manager settings. Or completely disable it following [post=12640479]this post[/post].
[*]Try changing the port type from MII to TP (Twisted Pair) -```
sudo ethtool -s eth0 port tp
``` Check "sudo ethtool eth0" again to see if it accepted the change.
[*]Try turning autonegotiation off and fixing the speed/duplex (it can also be used in combination of above (port tp))-```
sudo ethtool -s eth0 speed 100 duplex full autoneg off
```
[*]Try setting the MTU value to 1492 in Network Manager settings, although your current ifconfig shows no frame errors that usually suggest a problem due to higher MTU. Usually 1492 is supposed to be most optimal value, although you can set it to even lower values. Read more about it [here]("http://www.orangeproblems.co.uk/kitz/"), especially this part at the bottom -> Many routers have a setting in which you can alter its MTU size. You can change this, but you must make sure that the MTU setting on your router is the same as on your PC. It does not matter too much if the MTU on your router is higher than that on your PC, but the setting in your router must not be less than the MTU on your PC.
[/LIST]


If none of these help, then probably there is nothing more I can offer.

---

### Post by avents on 2013-11-06
I set IPv6 to "Ignore"  but it did not help.
No 2 did not work : 'Cannot set new settings: Invalid argument
  not setting port'
No 3 ' sudo ethtool -s eth0 speed 100 duplex full autoneg off '   was accepted but so far did nothing,

It is like this: I start my Ubuntu 13.10 and Ethernet does not work (in the upper right corner icon says that it works though obviously there is no connection).
After I stop and restart the router and reboot Ubuntu connection comes back.
Thanks

---

### Post by varunendra on 2013-11-06
> **avents said:**
> It is like this: I start my Ubuntu 13.10 and Ethernet does not work (in the upper right corner icon says that it works though obviously there is no connection).
After I stop and restart the router and reboot Ubuntu connection comes back.
Oh, good to have that clear now, earlier I thought it stopped working **AFTER** some time of activity (working at first, then gradually come to a halt). The above description can also be indicative of a DHCP issue.

Does the ethernet get IP from DHCP in the router? Or is it a manually assigned IP?

If it is getting its IP from DHCP, try manual mode for a test, and also check -
```
grep -i dhclient /var/log/syslog
```
..after a fresh boot when the connection doesn't work.

By the way, the probability of a bad physical connection is always there, check it whenever you have a chance.

Also, when it works, check the output of "**ifconfig**" after a considerably long time of usage, and considerably large amount of data transfer. If it shows any errors, like **errors, drops, frame, carrier** etc., it may give a hint if there is a physical or logical problem. If it is all good, then almost certainly it is a problem in 'Initial handshake', of which the dhclient is an important part.

---

### Post by avents on 2013-11-08
After a period of suspend ,  there was no connection when restarted from suspend. 
:~$ grep -i dhclient /var/log/syslog showed:
```

Nov  8 07:10:46 .... my Id.... kernel: [   12.598771] type=1400 audit(1383912643.005:2): apparmor="STATUS" operation="profile_load" parent=320 profile="unconfined" name="/sbin/dhclient" pid=323 comm="apparmor_parser"
Nov  8 07:10:46 .... my Id.... kernel: [   12.598809] type=1400 audit(1383912643.005:4): apparmor="STATUS" operation="profile_load" parent=320 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=323 comm="apparmor_parser"
Nov  8 07:10:46 .... my Id.... kernel: [   12.606589] type=1400 audit(1383912643.013:6): apparmor="STATUS" operation="profile_replace" parent=320 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=323 comm="apparmor_parser"
Nov  8 07:10:46 .... my Id.... kernel: [   12.607435] type=1400 audit(1383912643.013:7): apparmor="STATUS" operation="profile_replace" parent=320 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=323 comm="apparmor_parser"
Nov  8 07:10:48 .... my Id.... NetworkManager[741]: <info> dhclient started with pid 819
Nov  8 07:10:48 .... my Id.... dhclient: Internet Systems Consortium DHCP Client 4.2.4
Nov  8 07:10:48 .... my Id.... dhclient: Copyright 2004-2012 Internet Systems Consortium.
Nov  8 07:10:48 .... my Id.... dhclient: All rights reserved.
Nov  8 07:10:48 .... my Id.... dhclient: For info, please visit https://www.isc.org/software/dhcp/
Nov  8 07:10:48 .... my Id.... dhclient: 
Nov  8 07:10:48 .... my Id.... dhclient: Listening on LPF/eth0/00:xx....
Nov  8 07:10:48 .... my Id.... dhclient: Sending on   LPF/eth0/00:xx.....
Nov  8 07:10:48 .... my Id.... dhclient: Sending on   Socket/fallback
Nov  8 07:10:48 .... my Id.... dhclient: DHCPREQUEST of 192.168.1.100 on eth0 to 255.255.255.255 port 67 (xid=0xd9a8175)
Nov  8 07:10:48 .... my Id.... dhclient: DHCPACK of 192.168.1.100 from 192.168.1.1
Nov  8 07:10:48 .... my Id.... dhclient: bound to 192.168.1.100 -- renewal in 276091 seconds.
Nov  8 07:13:22 .... my Id.... kernel: [   12.019935] type=1400 audit(1383912799.431:2): apparmor="STATUS" operation="profile_load" parent=321 profile="unconfined" name="/sbin/dhclient" pid=326 comm="apparmor_parser"
Nov  8 07:13:22 .... my Id.... kernel: [   12.019967] type=1400 audit(1383912799.431:4): apparmor="STATUS" operation="profile_load" parent=321 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=326 comm="apparmor_parser"
Nov  8 07:13:22 .... my Id.... kernel: [   12.021759] type=1400 audit(1383912799.435:6): apparmor="STATUS" operation="profile_replace" parent=321 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=326 comm="apparmor_parser"
Nov  8 07:13:22 .... my Id.... kernel: [   12.022599] type=1400 audit(1383912799.435:7): apparmor="STATUS" operation="profile_replace" parent=321 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=326 comm="apparmor_parser"
Nov  8 07:13:24 .... my Id.... NetworkManager[679]: <info> dhclient started with pid 696
Nov  8 07:13:24 .... my Id.... dhclient: Internet Systems Consortium DHCP Client 4.2.4
Nov  8 07:13:24 .... my Id.... dhclient: Copyright 2004-2012 Internet Systems Consortium.
Nov  8 07:13:24 .... my Id.... dhclient: All rights reserved.
Nov  8 07:13:24 .... my Id.... dhclient: For info, please visit https://www.isc.org/software/dhcp/
Nov  8 07:13:24 .... my Id.... dhclient: 
Nov  8 07:13:24 .... my Id.... dhclient: Listening on LPF/eth0/00:xx........
Nov  8 07:13:24 .... my Id.... dhclient: Sending on   LPF/eth0/00:xx..........
Nov  8 07:13:24 .... my Id.... dhclient: Sending on   Socket/fallback
Nov  8 07:13:24 .... my Id.... dhclient: DHCPREQUEST of 192.168.1.100 on eth0 to 255.255.255.255 port 67 (xid=0x774ead93)
Nov  8 07:13:24 .... my Id.... dhclient: DHCPACK of 192.168.1.100 from 192.168.1.1
Nov  8 07:13:24 .... my Id.... dhclient: bound to 192.168.1.100 -- renewal in 253233 seconds.
Nov  8 07:13:24 .... my Id.... kernel: [   17.235799] type=1400 audit(1383912804.647:20): apparmor="STATUS" operation="profile_replace" parent=751 profile="unconfined" name="/sbin/dhclient" pid=780 comm="apparmor_parser"

``` 
Additionally, it did not let me restart or Shut Down (just hanging or rather ignoring command).  
  'sudo reboot now' did shut down but then was hanging at some point  and only rebooted  after I used Cntr+Alt+Del. 
And (miraculously!) connection was back.

Thank you so much varunendra for trying to get to the bottom of this.

BTW : [B]ifconfig  done yesterday showed no errors.
Thanks
[/B]

---

### Post by varunendra on 2013-11-08
> **avents said:**
> Additionally, it did not let me restart or Shut Down (just hanging or rather ignoring command).  
  'sudo reboot now' did shut down but then was hanging at some point  and only rebooted  after I used Cntr+Alt+Del.

That could be caused by some other driver that does not properly unload/load during a suspend --> resume cycle, not necessarily a network interface driver.

However, even the DHCP seems to be working fine and, if the above output was indeed from 'AFTER' resuming from suspend, both physical and logical connections between the computer and the router look perfectly ok (the PC is requesting a DHCP pack, and is getting the same from the router) -
```
Nov  8 07:13:24 .... my Id.... dhclient: DHCPREQUEST of 192.168.1.100 on eth0 to 255.255.255.255 port 67 (xid=0x774ead93)
Nov  8 07:13:24 .... my Id.... dhclient: **DHCPACK of 192.168.1.100 from 192.168.1.1**
Nov  8 07:13:24 .... my Id.... dhclient: **bound to 192.168.1.100** -- renewal in 253233 seconds.
```

When the connection 'seems' to be hung, can you ping the router or any external IP? Try these -
```
ping -c 4 192.168.1.1
ping -c 4 8.8.8.8
```
Do you get replies in the above ping attempts? Does the first one succeeds and the second one fails?

---

### Post by avents on 2013-11-12
Got a new router and the problem went away.
Thank you all for the help

---

