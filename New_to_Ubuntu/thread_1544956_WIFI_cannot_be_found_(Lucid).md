---
title: "WIFI cannot be found (Lucid)"
date: 2010-08-03
forum: New to Ubuntu
---

### Post by aryangor on 2010-08-03
Posted this under Networks section, but no reply received for over 2 months, so re-posting here.

For the past 6 months I could pick up the WiFi spot in our house, until last weekend when it just disappeared from my network manager. Everyone else in my house can see the WiFi and connect, even the Karmic users - only me has nothing! I can see our neighbors' WiFi though - I could always see it, so I don't think the problem is with my hardware.

I tried to reinstall the connection via network manager - did not work. I reinstalled Lucid - no effect. I tried Karmic - nothing!! It just disappeared! I had connection 3 days ago, but now I don't know what to do.

Any help will be appreciated. Do you need to see any output here?

---

### Post by aryangor on 2010-08-03
**OUTPUT : lshw -c network**

*-network
description: Wireless interface
product: PRO/Wireless 3945ABG [Golan] Network Connection
vendor: Intel Corporation
physical id: 0
bus info: pci@0000:06:00.0
logical name: wmaster0
version: 02
serial: 00:13:02:34:a2:95
width: 32 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
configuration: broadcast=yes driver=iwl3945 latency=0 multicast=yes wireless=IEEE 802.11abg
resources: irq:28 memory:84000000-84000fff
*-network
description: Ethernet interface
product: PRO/100 VE Network Connection
vendor: Intel Corporation
physical id: 8
bus info: pci@0000:08:08.0
logical name: eth0
version: 01
serial: 00:16:d4:07:83:bd
size: 100MB/s
capacity: 100MB/s
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full firmware=N/A ip=192.168.0.250 latency=64 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100MB/s
resources: irq:20 memory:d2006000-d2006fff ioport:2000(size=64)
*-network DISABLED
description: Ethernet interface
physical id: 1
logical name: vboxnet0
serial: 0a:00:27:00:00:00
capabilities: ethernet physical
configuration: broadcast=yes multicast=yes

==================================================

**OUTPUT : dmesg | grep wl**

[   15.148367] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
[   15.148372] iwl3945: Copyright(c) 2003-2009 Intel Corporation
[   15.148495] iwl3945 0000:06:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   15.148511] iwl3945 0000:06:00.0: setting latency timer to 64
[   15.228577] iwl3945 0000:06:00.0: Tunable channels: 13 802.11bg, 23 802.11a channels
[   15.228582] iwl3945 0000:06:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   15.229150] iwl3945 0000:06:00.0: irq 28 for MSI/MSI-X
[   15.335755] phy0: Selected rate control algorithm 'iwl-3945-rs'
[ 7186.033046] iwl3945 0000:06:00.0: firmware: requesting iwlwifi-3945-2.ucode
[ 7186.092330] iwl3945 0000:06:00.0: loaded firmware version 15.32.2.9
[ 7186.165136] Registered led device: iwl-phy0::radio
[ 7186.165181] Registered led device: iwl-phy0::assoc
[ 7186.165219] Registered led device: iwl-phy0::RX
[ 7186.165255] Registered led device: iwl-phy0::TX
[ 7186.185135] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7196.539574] wlan0: deauthenticating from 00:02:6f:22:9a:3a by local choice (reason=3)
[ 7196.540981] wlan0: direct probe to AP 00:02:6f:22:9a:3a (try 1)
[ 7196.543177] wlan0: direct probe responded
[ 7196.543186] wlan0: authenticate with AP 00:02:6f:22:9a:3a (try 1)
[ 7196.548862] wlan0: authenticated
[ 7196.548906] wlan0: associate with AP 00:02:6f:22:9a:3a (try 1)
[ 7196.557117] wlan0: RX AssocResp from 00:02:6f:22:9a:3a (capab=0x421 status=0 aid=18)
[ 7196.557125] wlan0: associated
[ 7196.558905] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 7206.868017] wlan0: no IPv6 routers present

==================================================

**OUTPUT: dmesg | grep wlan0**

[ 7186.185135] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7196.539574] wlan0: deauthenticating from 00:02:6f:22:9a:3a by local choice (reason=3)
[ 7196.540981] wlan0: direct probe to AP 00:02:6f:22:9a:3a (try 1)
[ 7196.543177] wlan0: direct probe responded
[ 7196.543186] wlan0: authenticate with AP 00:02:6f:22:9a:3a (try 1)
[ 7196.548862] wlan0: authenticated
[ 7196.548906] wlan0: associate with AP 00:02:6f:22:9a:3a (try 1)
[ 7196.557117] wlan0: RX AssocResp from 00:02:6f:22:9a:3a (capab=0x421 status=0 aid=18)
[ 7196.557125] wlan0: associated
[ 7196.558905] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 7206.868017] wlan0: no IPv6 routers present

---

### Post by Peter09 on 2010-08-03
Can you also post the output of 
 
```
ifconfig
```

---

### Post by Peter09 on 2010-08-03
Note that you will need to do this with NO hardwired link attached.

---

### Post by aryangor on 2010-08-03
**OUTPUT: ifconfig**

eth0      Link encap:Ethernet  HWaddr 00:1d:92:00:6f:5f  
          inet addr:143.160.0.0  Bcast:143.160.11.255  Mask:255.255.252.0
          inet6 addr: fe80::21d:92ff:fe00:6f5f/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:7490 errors:1567 dropped:0 overruns:0 frame:1567
          TX packets:3112 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2728790 (2.7 MB)  TX bytes:252358 (252.3 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:98661 errors:0 dropped:0 overruns:0 frame:0
          TX packets:98661 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2887893 (2.8 MB)  TX bytes:2887893 (2.8 MB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:41.29.0.0  P-t-P:10.0.0.0  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:82 errors:0 dropped:0 overruns:0 frame:0
          TX packets:104 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:5100 (5.1 KB)  TX bytes:15082 (15.0 KB)

wlan0     Link encap:Ethernet  HWaddr 00:13:02:34:a2:95  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:30 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3433 (3.4 KB)  TX bytes:576 (576.0 B)

---

### Post by Peter09 on 2010-08-03
Can you tell me more about this?
 
> ppp0 Link encap:razz:oint-to-Point Protocol 
inet addr:41.29.0.0 P-t-P:10.0.0.0 Mask:255.255.255.255
UP POINTOPOINT RUNNING NOARP MULTICAST MTU:1500 Metric:1
RX packets:82 errors:0 dropped:0 overruns:0 frame:0
TX packets:104 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:3 
RX bytes:5100 (5.1 KB) TX bytes:15082 (15.0 KB)

---

### Post by aryangor on 2010-08-03
> **Peter09 said:**
> Can you tell me more about this?

Sorry forgot to mention - its my dial-up 3G modem. Whether on or off, it has no effect on my WiFi problems (tested!).. My ethernet is also off.

---

### Post by Peter09 on 2010-08-03
Your output in dmsg contains
 
> [ 7186.185135] ADDRCONF(NETDEV_UP): wlan0: link is not ready
 
Could this refer to your wifi being switched off - check any hardware wifi switches on the machine.
 
EDIT:  FORGET this as its ok later in the sequence

---

### Post by Peter09 on 2010-08-03
Have you checked to see if you are connected - just Network Manager is not showing the connection?

---

### Post by Tiberion on 2010-08-03
run sudo lshw -C network and post results here

---

### Post by aryangor on 2010-08-04
> **Peter09 said:**
> Have you checked to see if you are connected - just Network Manager is not showing the connection?

No connection - thats the nightmare part! To give a few examples:
- I was at the airport two weeks ago, my NManager picked up all hotspots there, and via it I connected to one of them;
- as I am at home, our neighbor's WiFi signals reach me and I am able to see their hotspot connection in NManager, and I can connect to it (then it asks for a pass).

The other laptop we have is in the same room, it runs Karmic, its NManager picks up OUR WiFi and can connect to it.

Is it possible that this laptop takes all connection for itself and there is no WiFi left for me? It sounds very dumb though... but maybe the hotspot can only support one connection at a time? Is something like this possible?

> **Tiberion said:**
> run sudo lshw -C network and post results here 
It is already posted above.

---

### Post by Peter09 on 2010-08-04
Try right clicking on network manager icon and select 'connect to other networks'. Does anything change?

---

### Post by Peter09 on 2010-08-04
Also found this as a way to reset network manager - worth a try
 
```

service network-manager stop
rm /var/lib/NetworkManager/NetworkManager.state
service network-manager start
```

---

### Post by aryangor on 2010-08-04
I left-clicked, and right-clicked many times, went into all possible options, tried crazy things, but to no avail.

As far as your second suggestion goes, it did not produce any result. I rebooted and now there is even more trouble. NetworkManager icon does not appear on my gnome panel any more. Yet, when I type **sudo NetworkManager**, the console says that it is already running. When I then say **sudo kill pid**, the icon on my panel appears...

Did I mention that my dual-boot windows has a similar problem? It picks up the signal, but a few seconds after it connects to my home WiFI, it disconnects again.

---

### Post by Tiberion on 2010-08-04
I sure hate to be the bearer of bad news but it sounds like your wifi card or the controller is failing.  I say this based on the fact that lshw didn't display anything.  The fact that windows is dropping connection also is another indicator that this is a hardware issue not an OS issue.  My dad has a Dell laptop doing the same thing.  AT one minute it connects to open networks and encrypted with no problem, then it will drop and not reconnect for sometimes hours.  I am sorry.

---

### Post by Peter09 on 2010-08-04
For the network manager icon

[http://www.ubuntugeek.com/possible-solutions-to-fix-the-missing-network-manager-icon-in-ubuntu-9-10.html](http://www.ubuntugeek.com/possible-solutions-to-fix-the-missing-network-manager-icon-in-ubuntu-9-10.html)

It does make a difference that you are having problems with Windows as well as that points to either signal strength or router configuration.

---

### Post by Tiberion on 2010-08-04
Peter09, I would like to be wrong for aryangor so i am curious can you explain why a router configuration would explain the dropping in signal in multiple locations.

---

### Post by xircon on 2010-08-04
> **Peter09 said:**
> Also found this as a way to reset network manager - worth a try
 
```

service network-manager stop
rm /var/lib/NetworkManager/NetworkManager.state
service network-manager start
```

Might be useful to display contents of above file before removing, coming back from a failed suspend sometimes screws this file, what does:
```
cat /var/lib/NetworkManager/NetworkManager.state

```
return?

if it returns WirelessEnabled=false edit and change to true.

---

### Post by Peter09 on 2010-08-04
Tiberion
> Peter09, I would like to be wrong for aryangor so i am curious can you  explain why a router configuration would explain the dropping in signal  in multiple locations.

Post 1 suggests that he can see his neighbors network and attempt to connect (although he does not have the key). That would suggest that its selective on his home network - although perhaps the OP could clarify.

---

### Post by Tiberion on 2010-08-04
Thank you for that clarification I made a perhaps erroneous assumtion that he could see it at one time but had lost that capability.  Thanks

---

### Post by Peter09 on 2010-08-04
Tiberion

No problems - always good to cover the bases.

Aryangor - 
many routers allow you to change the WiFi channel they transmit on - may be worth trying just in case there is some interference which your card is susceptible to (shot in the dark here) . Your other machines should automatically adapt.

---

### Post by aryangor on 2010-08-31
> **xircon said:**
> Might be useful to display contents of above file before removing, coming back from a failed suspend sometimes screws this file, what does:
```
cat /var/lib/NetworkManager/NetworkManager.state

```
return?

if it returns WirelessEnabled=false edit and change to true.

WirelessEnabled=true

Unfortunately this does not seem to be the problem...


> **Peter09 said:**
> 
many routers allow you to change the WiFi channel they transmit on - may be worth trying just in case there is some interference which your card is susceptible to (shot in the dark here) . Your other machines should automatically adapt.

Will try to look into this. Will post the results - the problem is IMHO too peculiar to let it pass.. :)

---

