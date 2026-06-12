---
title: "billions of dropped packets on ifconfig"
date: 2008-08-24
forum: Networking &amp; Wireless
---

### Post by gobble on 2008-08-24
Hi there

Any ideas why do i see so many dropped packets on my interface? 



:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1f:d0:56:bd:8b  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:d0ff:fe56:bd8b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:29518 errors:0 dropped:640233008 overruns:0 frame:0
          TX packets:28694 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:26509495 (25.2 MB)  TX bytes:5404094 (5.1 MB)
          Interrupt:222 Base address:0xa000 


I ran a tcpdump for 2 hours and only got valid traffic like rss feeds and my FF toolbar checking my gmail inbox etc... Would a TCP RST be counted as dropped traffic? I doubt it. Would like to understand if this is a device driver bug or something else.

2.6.24-19-generic #1 SMP Fri Jul 11 23:41:49 UTC 2008 i686 GNU/Linux
:~$ ethtool -i eth0
driver: r8169
version: 2.2LK
firmware-version: 
bus-info: 0000:02:00.0

Would like an opinion if I should post a bug report or not. Besides my ISP bill bombed on me last month for the volume.

TIA

---

### Post by gobble on 2008-08-25
PS: if you look at   RX bytes:22249227 (21.2 MB)  TX bytes:4371791 (4.1 MB)

does it exclude dropped packets in receive count? Why isn't tcpdump logging the dropped packets? I couldn't find anything anomalous from a 2hr tcpdump when my pc was idle or even  iptables logging of ALL traffic. 

HTH

TIA

---

### Post by Crafty Kisses on 2008-08-25
Packet loss can be caused by a number of factors, including signal degradation over the network medium, oversaturated network links, corrupted packets rejected in-transit, faulty networking hardware, maligned system drivers or network applications, or normal routing routines.

Some network transport protocols such as TCP provide for reliable delivery of packets. In the event of packet loss, the receiver asks for retransmission or the sender automatically resends any segments that have not been acknowledged.

You might want to check if there is any interference with like a phone or a microwave or even possibly a lamp. I know it sounds stupid but my lamp for some reason was causing some interference with my router, that can all lead to packet loss.

Hope this helps. :)

---

### Post by dmizer on 2008-08-25
Could be that your router isn't handling ipv6 well. Think I'd start by disabling that and see if there's any change: [https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4)

What about local traffic? Are you using something like samba for local file transfer? Try disabling network services like samba, ftp, nfs and the like to see if that makes a difference too.

---

### Post by Crafty Kisses on 2008-08-25
> **dmizer said:**
> Could be that your router isn't handling ipv6 well. Think I'd start by disabling that and see if there's any change: [https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4)

What about local traffic? Are you using something like samba for local file transfer? Try disabling network services like samba, ftp, nfs and the like to see if that makes a difference too.

That's what I was also thinking I just wasn't sure, thanks for that post man.

---

### Post by gobble on 2008-08-26
My ISP line is clean:

xx.xx.xx.xx (ABTS-KK-Dynamic-XXXXXX-airtelbroadband.in)
    Partial loss:      0 / 1472 (0%)
    Partial char:      rtt = 25.274518 ms, (b = 0.009110 ms/B), r2 = 0.995879
                       stddev rtt = 0.071388, stddev b = 0.000088
    Partial queueing:  avg = 0.003343 ms (1264 bytes)
    Hop char:          rtt = --.--- ms, bw = 85008.293912 Kbps
    Hop queueing:      avg = -0.001174 ms (0 bytes)

This is a single desktop connected to ADSL modem. No Samba, but let me try disabling virtualbox at startup. 

The ipv6 problem only affects people with DNS servers that don't respond correctly to ipv6.


Would a lamp affect wired cat5 ETH link? I got a lava lamp a few weeks back besides it was off when I observed the loss. 

Appreciate it if someone can throw some more light on it (no pun intended).

Cheers

---

### Post by dmizer on 2008-08-26
I am in no way suggesting that ipv6 is something you should simply do away with. My thinking is, that even if there's reasonable doubt that it could cause your issue there's no reason not to test it as part of a "process of elminiation". If nothing else, in the process of testing, you may stumble across the real issue. After all, it's not like disabling ipv6 is irreversable.

Also, I believe that even if you can correctly route ipv6, you may still encounter problems with Firefox unless the ipv6 Firefox thing has been fixed.

If your ISP link is clean, then your problem is local, which makes it sound as though you have a wayward service.

I think the only other way to go about this would be with packet inspection. Unfortunately, I have very limited knowledge of how to go about analyzing specific packets (or the tools necessary) to determine where the request originated. So I'm stuck with process of elimination, which might be slower, but is also effective.

Lava lamps, TVs, power cables, power supplies, and other entertainment electronics (when powered on) put out both heat and gobs of RF, both of which could adversely effect cat5.

---

### Post by gobble on 2008-08-27
Thanks. I will let you know when I narrow down the cause ..

Cheers

---

### Post by RaccoonBoy on 2008-11-19
This thread hasn't been updated in a while, so I don't know if you solved your problem or not, however, I was having the same problem and fixed it by changing from r8169.  Since you also have that driver I recommend changing it out.  I changed to r8101 which is what was recommended for my card.  So for anyone who has the same problem and found this thread like I did, but didn't find the solution, changing out r8169 worked for me.

---

### Post by patryk77 on 2008-11-19
How do I change the drivers?

It may also help me with my network problems.
Thannks.


           *-network
                description: Ethernet interface
                product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 02
                serial: 00:1e:68:e7:dd:6b
                capacity: 1GB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no module=r8169 multicast=yes port=twisted pair

---

### Post by Circa Lucid on 2010-05-18
I have an Asus P5G41M-LX with the Realtek RTL8111/8168B PCI Express Gigabit Ethernet controller with Ubuntu 10.04. I was getting between 30-70% packet loss on pinging to and from the box. I went into the BIOS and disabled "Memory Remap Feature", which apparently remaps PCI memory into >4GB RAM but I only had 1GB RAM, and everything is working flawlessly. Give it a look.

---

