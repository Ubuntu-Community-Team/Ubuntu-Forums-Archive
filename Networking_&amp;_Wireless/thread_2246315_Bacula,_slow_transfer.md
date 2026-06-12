---
title: "Bacula, slow transfer"
date: 2014-09-29
forum: Networking &amp; Wireless
---

### Post by bphillips2 on 2014-09-29
I use Bacula to backup my office server at my house.  I have been fighting with some painfully slow transfer speeds.  It is in the .5kb/s range.  That means a backup can take 3-4 days.  I have checked my internet speeds and they are faster (3.5mb upload speed where the office server is and 12mb download speed at home where the backup server is).  I have also done an iperf test and am getting some similarly slow results (see below).  Assuming the transfer rate (as opposed to the bandwidth rate) on my iperf test is the number I should be looking at, it appears this is a network issue.  Any ideas how to speed it up or even where to start?

Iperf test results
> 
[ ID] Interval       Transfer       Bandwidth
[  3]  0.0- 2.0 sec   768 KBytes  3.15 Mbits/sec
[  3]  2.0- 4.0 sec   384 KBytes  1.57 Mbits/sec
[  3]  4.0- 6.0 sec   384 KBytes  1.57 Mbits/sec
[  3]  6.0- 8.0 sec   512 KBytes  2.10 Mbits/sec
[  3]  8.0-10.0 sec   384 KBytes  1.57 Mbits/sec
[  3] 10.0-12.0 sec   512 KBytes  2.10 Mbits/sec
[  3] 12.0-14.0 sec   384 KBytes  1.57 Mbits/sec
[  3] 14.0-16.0 sec   512 KBytes  2.10 Mbits/sec
[  3] 16.0-18.0 sec   384 KBytes  1.57 Mbits/sec
[  3] 18.0-20.0 sec   384 KBytes  1.57 Mbits/sec
[  3] 20.0-22.0 sec   768 KBytes  3.15 Mbits/sec
[  3] 22.0-24.0 sec   640 KBytes  2.62 Mbits/sec
[  3] 24.0-26.0 sec   768 KBytes  3.15 Mbits/sec
[  3] 26.0-28.0 sec   640 KBytes  2.62 Mbits/sec
[  3] 28.0-30.0 sec   640 KBytes  2.62 Mbits/sec
[  3] 30.0-32.0 sec   640 KBytes  2.62 Mbits/sec
[  3] 32.0-34.0 sec   640 KBytes  2.62 Mbits/sec
[  3] 34.0-36.0 sec   512 KBytes  2.10 Mbits/sec
[  3] 36.0-38.0 sec   640 KBytes  2.62 Mbits/sec
[  3] 38.0-40.0 sec   640 KBytes  2.62 Mbits/sec
[  3] 40.0-42.0 sec   512 KBytes  2.10 Mbits/sec
[  3] 42.0-44.0 sec   768 KBytes  3.15 Mbits/sec
[  3] 44.0-46.0 sec   640 KBytes  2.62 Mbits/sec
[  3] 46.0-48.0 sec   768 KBytes  3.15 Mbits/sec
[  3] 48.0-50.0 sec   640 KBytes  2.62 Mbits/sec
[  3] 50.0-52.0 sec   512 KBytes  2.10 Mbits/sec
[  3] 52.0-54.0 sec   384 KBytes  1.57 Mbits/sec
[  3] 54.0-56.0 sec   640 KBytes  2.62 Mbits/sec
[  3] 56.0-58.0 sec   512 KBytes  2.10 Mbits/sec
[  3] 58.0-60.0 sec   512 KBytes  2.10 Mbits/sec
[  3]  0.0-60.6 sec  16.8 MBytes  2.32 Mbits/sec

---

### Post by TheFu on 2014-09-30
check the cards, cables, switch ports.
Use a wired connection.

Did it work faster before? Is everything slow - everything or just a few specific programs?
What card, driver, are being used on both sides?

---

### Post by bphillips2 on 2014-09-30
Both servers are are direct wired to the routers.  They don't have separate network cards, just use the motherboard network port.

It has always been this slow.

---

### Post by Michael_McKenney on 2014-10-02
I installed an Intel PCIe 1X NIC last night.  My old Nvidia NIC gave poor performance of over 5 hours to backup a remote box.  The Intel PCIe X1 was $39.99 at Micro Center.  Backup performance jumped to fastest level ever, 2200 MB/min on the HP LTO3 tape drive and 1 hour 22 minutes.  Everything I read about the Reversed Engineered Nividia 0.64 driver pointed to replacing it with a Intel based NIC.   Ubuntu 14.04 Intel NIC drivers are robust from what I read and am seeing.   Both boxes are using the same Intel NIC.  I am looking at a way to run iperf on my Windows 7 x64 workstation to test its NIC performance to the Tape server Bacula/Ubuntu box.  

My Bacula is 5.2.6.  I am looking at upgrading to 5.2.13 and getting my three concurrent jobs working before jumping to Bacula 7.x.x.  Symantec Backup Exec could do three concurrent tape backups.   My goal is get it to the same concurrent levels.

---

### Post by TheFu on 2014-10-02
Intel PRO/1000 NICs are the industry standard and are available for less than $20 on newegg.
In the old days, before GigE was standard, cheaper cards topped out around 200-400 Mbps, and the Intel cards were 700+Mbps.  These days, the intel cards are cheap enough there really isn't much excuse NOT to get those if a slot is available.

With intel cards, iperf shows 900Mbps+ throughput with translates to real world 850Mbps-ish transfers. Of course, storage speeds impact large transfers once the disk cache is full.

Until the OP posts the requested information, it will be nearly impossible to help.

---

### Post by bphillips2 on 2014-10-03
I posted the requested information.  Both computers are wired to the router and I am using the basic ethernet port on the motherboard.  They both have [this]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813157236") motherboard.  Not sure on the exact driver, but it would be the basic driver for that motherboard.

I'm topping out at 0.5 mbps.  Surely the standard motherboard port an handle higher speeds than that.

---

### Post by Michael_McKenney on 2014-10-03
ethtool eth0 

or what ever ethx x is the number.

ifconfig
[FONT=Courier New]dmesg | grep -i eth0[/FONT]

Check your cables for CAT 5, 5e or 6.  You need 5e or 6 for gigabit.  What is your router?  100 Mbps or Gigabit.

---

### Post by TheFu on 2014-10-03
We cannot assume anything. The exact driver on the system is needed.
[http://blog.jdpfu.com/2013/04/27/linux-troubleshooting-101-knowing-your-hardware](http://blog.jdpfu.com/2013/04/27/linux-troubleshooting-101-knowing-your-hardware)
and
[http://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking](http://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking)

Us assuming anything will lead to mis-diagnosis. Only you can provide the details.

---

### Post by bphillips2 on 2014-10-03
> **Michael_McKenney said:**
> ethtool eth0 

or what ever ethx x is the number.

ifconfig
[FONT=Courier New]dmesg | grep -i eth0[/FONT]

Check your cables for CAT 5, 5e or 6.  You need 5e or 6 for gigabit.  What is your router?  100 Mbps or Gigabit.

Cables are Cat 5e.

Here is my output of the command on the director
```
brad@ubuntu:~$ dmesg | grep -i eth0[    2.287458] r8169 0000:05:00.0 eth0: RTL8168evl/8111evl at 0xffffc90000c6c000, 90:2b:34:12:e7:68, XID 0c900800 IRQ 41
[    2.287462] r8169 0000:05:00.0 eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[    7.601613] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   10.267222] r8169 0000:05:00.0 eth0: link down
[   10.267240] r8169 0000:05:00.0 eth0: link down
[   10.267269] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   12.229690] r8169 0000:05:00.0 eth0: link up
[   12.229697] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[335945.539510] r8169 0000:05:00.0 eth0: link down
[335949.422022] r8169 0000:05:00.0 eth0: link up
[335962.760083] r8169 0000:05:00.0 eth0: link down
[335978.395611] r8169 0000:05:00.0 eth0: link up
[335996.670375] r8169 0000:05:00.0 eth0: link down
[335998.658243] r8169 0000:05:00.0 eth0: link up
[1424171.046962] r8169 0000:05:00.0 eth0: link down
[1424173.006678] r8169 0000:05:00.0 eth0: link up
[1424186.357980] r8169 0000:05:00.0 eth0: link down
[1424202.829335] r8169 0000:05:00.0 eth0: link up
[1424221.197275] r8169 0000:05:00.0 eth0: link down
[1424223.176842] r8169 0000:05:00.0 eth0: link up
```

And the client
```
justin@ubuntu:/var/www$ dmesg | grep -i eth0[    8.211603] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   13.648583] atl1c 0000:04:00.0: atl1c: eth0 NIC Link is Up<100 Mbps Full Duplex>
```

> **TheFu said:**
> We cannot assume anything. The exact driver on the system is needed.
[http://blog.jdpfu.com/2013/04/27/linux-troubleshooting-101-knowing-your-hardware](http://blog.jdpfu.com/2013/04/27/linux-troubleshooting-101-knowing-your-hardware)
and
[http://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking](http://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking)

Us assuming anything will lead to mis-diagnosis. Only you can provide the details.

Thanks for the link.  Here is my output of *lshw -c network* on the Director system which should show the details needed.
```
brad@ubuntu:~$ sudo lshw -c network[sudo] password for brad: 
  *-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 06
       serial: 90:2b:34:12:e7:68
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168e-3_0.0.4 03/27/12 ip=192.168.0.234 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:41 ioport:c000(size=256) memory:f0004000-f0004fff memory:f0000000-f0003fff
```

And on the client
```
justin@ubuntu:/var/www$ sudo lshw -c network[sudo] password for justin: 
  *-network               
       description: Ethernet interface
       product: AR8151 v2.0 Gigabit Ethernet
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: c0
       serial: 00:25:22:b2:ce:bd
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.1-NAPI duplex=full ip=192.168.1.106 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:53 memory:fe600000-fe63ffff ioport:e000(size=128)
```

---

### Post by Michael_McKenney on 2014-10-03
justin@ubuntu:/var/www$ dmesg | grep -i eth0[    8.211603] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   13.648583] atl1c 0000:04:00.0: atl1c: eth0 NIC Link is Up<100 Mbps Full Duplex>

This shows 100 Mbps Full Duplex.  I would hard set your NIC to 1000 Mbps Full Duplex on both computers to start with.   The up - down - up is usually speed or duplex are mismatched.  If one side is hard set and other is not, it can happen.  So set both computers to 1000 Full Duplex to start.

---

### Post by Michael_McKenney on 2014-10-03
How long are you Cat 5e cables?  Do they cross over electrical or lighting.  Are they in walls or ceiling?

---

### Post by bphillips2 on 2014-10-03
Thanks,

I have done this on both computers using the instructions [here]("https://help.ubuntu.com/10.04/serverguide/network-configuration.html")

I'll see if that improves it.

---

### Post by TheFu on 2014-10-03
If the router or switch is 10/100, you'll never get GigE speeds.  11MB/s or 90Mbps-ish is all you can expect. If any part of the connection is 100base-tx, that will limit the entire connection.

Also, the MTU appears to be set to 9200 bytes (or am I reading that wrong?) - even for jumbo frames, that seems high and many network devices don't support it.  Usually, jumbo frames have to be manually enabled - so better to go back to the default size (non-jumbo) - 1500.  All my devices support jumbo frames, but time sync via NTP stopped working to a Windows machine here, so had to go back to 1500 bytes. I still routinely see 75MB/s NFS file copies even with the default MTU.

So - does ifconfig and/or lshw show a 1000base-tx connection? No need to test if those do not show that speed. Also, if the subnetting isn't correct everywhere, things may work, just poorly.

---

### Post by bphillips2 on 2014-10-03
> **TheFu said:**
> If the router or switch is 10/100, you'll never get GigE speeds.  11MB/s or 90Mbps-ish is all you can expect. If any part of the connection is 100base-tx, that will limit the entire connection.

Also, the MTU appears to be set to 9200 bytes (or am I reading that wrong?) - even for jumbo frames, that seems high and many network devices don't support it.  Usually, jumbo frames have to be manually enabled - so better to go back to the default size - 1500.  All my devices support jumbo frames, but time sync via NTP stopped working to a Windows machine here, so had to go back to 1500 bytes. I still routinely see 75MB/s NFS file copies even with the default MTU.

So - does ifconfig and/or lshw show a 1000base-tx connection? No need to test of those do not show that speed.

I'm not seeing anything in ifconfig or lshw that shows 1000base-tx.  I'm sure my router and switch are 10/100/1000.  But even if they weren't, I would be happy with 11mb/s, as that would be 22x faster than I'm seeing.

---

### Post by bphillips2 on 2014-10-03
> **Michael_McKenney said:**
> How long are you Cat 5e cables?  Do they cross over electrical or lighting.  Are they in walls or ceiling?
They are shorter than 5 feet from the router to the server.  Not in any walls or ceilings.  On the director side they are near other electrical equipment (DVD player, cable box, stereo receiver).

---

### Post by TheFu on 2014-10-03
11 mb/s is nothing.  Perhaps you mean 11MB/s?  Case matters.  Software people think in terms of bytes, but network people ALWAYS talk bits.
B = bytes
b = bits (8x smaller)

BTW, it could be helpful if you posted the updated output from those commands.
The cards appear to be capable of GigE speeds, but something is preventing that from happening. Normally it would be the cables, switch, or router.  If both devices are connected to a GigE switch, then the router doesn't matter.

It would be worth trying different cables and different ports on the switch.  Sometimes ports go bad.

---

### Post by bphillips2 on 2014-10-03
> **TheFu said:**
> 11 mb/s is nothing.  Perhaps you mean 11MB/s?  Case matters.  Software people think in terms of bytes, but network people ALWAYS talk bits.
B = bytes
b = bits (8x smaller)

BTW, it could be helpful if you posted the updated output from those commands.
The cards appear to be capable of GigE speeds, but something is preventing that from happening. Normally it would be the cables, switch, or router.  If both devices are connected to a GigE switch, then the router doesn't matter.

Yep, I meant 11MB/s.  I didn't know about the bytes/bits before.  Thanks for explaining.

Here is the output after the changes.  This stuff is very over my head, so hopefully I'm doing it correctly.

Client side
```
justin@ubuntu:~$ sudo lshw -c network[sudo] password for justin: 
  *-network               
       description: Ethernet interface
       product: AR8151 v2.0 Gigabit Ethernet
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: c0
       serial: 00:25:22:b2:ce:bd
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.1-NAPI duplex=full ip=192.168.1.106 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:53 memory:fe600000-fe63ffff ioport:e000(size=128)
```

Director side
```
brad@ubuntu:~$ sudo lshw -c network[sudo] password for brad: 
  *-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 06
       serial: 90:2b:34:12:e7:68
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168e-3_0.0.4 03/27/12 ip=192.168.0.234 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:41 ioport:c000(size=256) memory:f0004000-f0004fff memory:f0000000-f0003fff
```

---

### Post by Michael_McKenney on 2014-10-03
What is your router make and model?  Does it even support Gigabit?  Most newer ones do.  5 foot cables should work with 5e unless they are damaged on Gigabit.  Unless your router is Gigabit, you will not get Gigabit speeds.  You will need 100 Mbps full duplex.

---

### Post by TheFu on 2014-10-03
ifconfig on both machines?
Also - exactly which device (vendor and model) do both computers plug into on the network side.

Even after we get all the networking figured out, that doesn't necessarily mean that backula will be faster - it is just the first thing. BTW, I don't use backula.

---

### Post by bphillips2 on 2014-10-03
> **Michael_McKenney said:**
> What is your router make and model?  Does it even support Gigabit?  Most newer ones do.  5 foot cables should work with 5e unless they are damaged on Gigabit.  Unless your router is Gigabit, you will not get Gigabit speeds.  You will need 100 Mbps full duplex.

Client side:
Asus RT-N66r Router [http://www.newegg.com/Product/Product.aspx?Item=N82E16833320154](http://www.newegg.com/Product/Product.aspx?Item=N82E16833320154)
actiontec C1000a (century link) modem [http://internethelp.centurylink.com/internethelp/modem-c1000a.html](http://internethelp.centurylink.com/internethelp/modem-c1000a.html)
Netgear FS728TP Switch (might be my problem as it looks to be a 10/100)  [http://www.newegg.com/Product/Product.aspx?Item=N82E16833122177](http://www.newegg.com/Product/Product.aspx?Item=N82E16833122177)

Director side I'm unsure of right now, but it is no older than 2 years old.

---

### Post by Michael_McKenney on 2014-10-03
I use Bacula 5.2.6.  It is a pain to configure and get working.  I managed to get two tape drives working on two jobs.  HP LTO3 is at 2200 MB/min.  Not bad for the ATA 100 drive it is backing up.

Working with Matt S. to upgrade it to 5.2.13 tonight.

---

### Post by bphillips2 on 2014-10-03
> **TheFu said:**
> ifconfig on both machines?
Also - exactly which device (vendor and model) do both computers plug into on the network side.

Even after we get all the networking figured out, that doesn't necessarily mean that backula will be faster - it is just the first thing. BTW, I don't use backula.
Ifconfig on director

```
brad@ubuntu:~$ ifconfigeth0      Link encap:Ethernet  HWaddr 90:2b:34:12:e7:68  
          inet addr:192.168.0.234  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::922b:34ff:fe12:e768/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:831595546 errors:0 dropped:0 overruns:0 frame:0
          TX packets:443032638 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1246813429232 (1.2 TB)  TX bytes:31849564060 (31.8 GB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:5828 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5828 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2928357 (2.9 MB)  TX bytes:2928357 (2.9 MB)
```


Client
```
justin@ubuntu:~$ ifconfigeth0      Link encap:Ethernet  HWaddr 00:25:22:b2:ce:bd  
          inet addr:192.168.1.106  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::225:22ff:feb2:cebd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:32656374 errors:0 dropped:0 overruns:0 frame:0
          TX packets:60887204 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:2346158226 (2.3 GB)  TX bytes:91388722337 (91.3 GB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:6867627 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6867627 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:11930334651 (11.9 GB)  TX bytes:11930334651 (11.9 GB)
```

---

### Post by Michael_McKenney on 2014-10-03
inet addr:192.168.0.234  Bcast:192.168.0.255  Mask:255.255.255.0
and 
inet addr:192.168.1.106  Bcast:192.168.1.255  Mask:255.255.255.0

What is your router's internal address?  You can't use two separate subnets on your home router.  192.168.0 or 192.168.1.

My Cisco 2911 can do it.  Your router can't.  You have to be in the same subnet.

---

### Post by bphillips2 on 2014-10-03
> **Michael_McKenney said:**
> inet addr:192.168.0.234  Bcast:192.168.0.255  Mask:255.255.255.0
and 
inet addr:192.168.1.106  Bcast:192.168.1.255  Mask:255.255.255.0

What is your router's internal address?  You can't use two separate subnets on your home router.  192.168.0 or 192.168.1.

My Cisco 2911 can do it.  Your router can't.  You have to be in the same subnet.

The client and director are on a different network.  The client is at my office, the director is at my house 5 miles away.  I'm doing an offsite backup.

---

### Post by Michael_McKenney on 2014-10-03
OK.  So you are trying to go across a WAN connection backup.  Run [www.speedtest.net]("http://www.speedtest.net") and check your pipe speed.  It could be 10 Mbps.

---

### Post by bphillips2 on 2014-10-03
> **Michael_McKenney said:**
> OK.  So you are trying to go across a WAN connection backup.  Run [www.speedtest.net]("http://www.speedtest.net") and check your pipe speed.  It could be 10 Mbps.

Yep.  Client side at my office is 25MB/s down and 3.5MB/s up.  Director side at my house is 10MB/s down and 0.5MB/s up.  My assumption, since the files are coming from the client to the director, is that my limiting speed is the client side upload speed of 3.5MB/s.  Correct?

---

### Post by TheFu on 2014-10-04
So these are on different subnets too!
That is important to share.

That means the uplink side of at least (and perhaps both) routers matters too.

Can you draw a picture of the network and post that somewhere?  Crude stick drawing with good labeling is fine.  Old network hardware had slow uplink ports.  However, how old it is doesn't mean anything about the connection links supported.  If you didn't specifically get GigE then it is unlikely to be GigE.  Also - most routers have a firewall built in, perhaps stateful packet inspection (slower) and QoS are getting in the way?  If there are thousands of other connections going (bittorrent), often the default settings are poor.

---

### Post by TheFu on 2014-10-04
> **bphillips2 said:**
> The client and director are on a different network.  The client is at my office, the director is at my house 5 miles away.  I'm doing an offsite backup.

Geeze - perhaps saying that sooner would have been helpful!!!!!

I'm out.

---

### Post by Michael_McKenney on 2014-10-04
Yes, You pipe is the limiting factor.   Just like with hosting sites the pipe controls the speed.  The reason I use tape drives and tapes is I can bring them offsite each night.   Your home is not a good place for a backup server.  Home connections share with everyone in your neighborhood.   Time of the backup can also limit you.   Most business class ISPs are same up and down.   I would go back to the ISP and find out your actual speeds you should be getting.  If it is 25/25, you can see what is tying up the 22 Mbps and shape the traffic on servers and QoS rules on routers and layer 3 switches.  We have a Barracuda backup device.   We have 10 Mbps Metro Ethernet connection to the ISP.  During production hours, the Barracuda QoS is set to 2 Mbps.  After hours, 7 Mbps.

As TheFu stated, when posting provide all the information known.  It would have given you a faster solution.

---

### Post by bphillips2 on 2014-10-04
implied in my first post that these computers were on a different network

> [COLOR=#000000]I use Bacula to backup **my office server at my house**. I have been fighting with some painfully slow transfer speeds. It is in the .5kb/s range. That means a backup can take 3-4 days. I have checked my internet speeds and they are faster (**3.5mb upload speed where the office server is and 12mb download speed at home where the backup server is**)[/COLOR]

Next time I'll be more obvious about it.

I appreciate the help.  We are opening a satellite office in a couple months.  I'll just deal with it until then and then place the backup server there.

---

### Post by Michael_McKenney on 2014-10-05
I run a data center.   Our connection is 10 / 10.  We use a Barracuda device and it is slow.   I limit it during work to 2 Mbps.   We added a second connection but we need a new firewall to have two separate connections link balanced for 20 / 20.  I narrowed my choices to the Checkpoint 4600 and 4800 vs. Fortinet 800C and 1000C.   $12,000 or $20,000 solution.   I am also implementing VMware DR.  It will backup all the VMs to VMware's DR site for a warm recovery plan.  $3000 a month.   I still recommend tape drives as an economy choice for offsite storage.  I take tapes home each night and the rest are in a fire proof safe.

---

