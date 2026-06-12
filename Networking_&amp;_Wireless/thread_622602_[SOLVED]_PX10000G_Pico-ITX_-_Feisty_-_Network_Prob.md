---
title: "[SOLVED] PX10000G Pico-ITX - Feisty - Network Problem"
date: 2007-11-24
forum: Networking &amp; Wireless
---

### Post by shutslar on 2007-11-24
Ubuntu 7.04 Feisty installs onto a 2.5" drive from the livecd just fine EXCEPT I have no network connection.  I also tried 7.10 Gutsy and had the exact same issue.

lspci output looks like this:
00:00.0 Host bridge: VIA Technologies, Inc. CX700 Host Bridge (rev 10)
00:00.1 Host bridge: VIA Technologies, Inc. CX700 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. CX700 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. CX700 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. CX700 Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. CX700 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:0f.0 IDE interface: VIA Technologies, Inc. Unknown device 5324
00.11.0 ISA bridge: VIA Technologies, Inc. CX700 PCI to ISA Bridge
00.11.7 Host bridge: VIA Technologies, Inc. CX700 Internal Module Bus
00.13.0 Host bridge: VIA Technologies, Inc. CX700 Host Bridge
00.13.1 PCI bridge: VIA Technologies, Inc. CX700 PCI to PCI Bridge
01.00.0 VGA compatible controller: VIA Technologies, Inc. Unknown device 3157 (rev 03)
02.06.0 Ethernet controller: VIA Technologies, Inc. VT6105 (Rhine-III) (rev 8b)
80.01.0 Audio device: VIA Technologies, Inc. VIA High Definition Audio Controller (rev 10)

ifconfig looks like this:
eth0 Link encap:Ethernet HWaddr 00:40:63:F2:4D:A8
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)
Interrupt:16 Base address:0xde00

eth0:avah Link encap:Ethernet HWaddr 00:40:63:F2:4D:A8
inet addr:169.254.8.89 Bcast:169.254.255.255 Mask:255.255.0.0
UP BROADCAST MULTICAST MTU:1500 Metric:1
Interrupt:16 Base address:0xde00

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask 255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP BROADCAST MULTICAST MTU:16436 Metric:1
RX packets:2 errors:0 dropped:0 overruns:0 frame:0
TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:100 (100.0 b) TX bytes:100 (100.0 b)

We can get a good ping reply on 127.0.0.1
We cannot get a ping reply from 192.168.1.1 (my Linksys router/gateway) 

Any suggestions for how to overcome?

---

### Post by shutslar on 2007-11-27
Hello all.  I thought I would update this thread for those that run into this issue with the little Via Pico-ITX system board.  We did get the networking functioning.  And I want to thank splat_ed and leetrefz over at [http://forums.viaarena.com]("http://forums.viaarena.com") for helping resolve the problem.  

The root cause is a problem with either the board or the firmware.  If the network cable is not already connected to router and the motherboard **_BEFORE_** the power is connected, the board will not recognize the network connection and it will fail to connect to the router.  This means you **MUST NOT BE PROVIDING ANY ELECTRICITY** to the board before the network cable is connected.

To fix the issue:
[LIST=1]
[*]Shut down the system
[*]Disconnect the power cable from the system board
[*]Connect the network cable to the router/gateway
[*]Connect the network cable to the system board
[*]Connect power to the system board
[*]Start the computer normally
[/LIST]

Again, this has nothing to do with the operating system or the network configuration. This problem exists with 7.04 and 7.10 as well as different distributions.  If you have already looked your networking configuration and it all appears correct and before you pull your hair out trying to configure your way out of this issue, run the following command:

```
sudo ethtool eth0
```

replace eth0 with your network device name (i.e. eth0, eth1, eth2, etc.)

The last line of the output should say "Link detected: yes".  If it says "Link detected: no", your system board is not recognizing that you have a network connection.  Try the above solution and it may resolve your issue.

Good Luck.

---

