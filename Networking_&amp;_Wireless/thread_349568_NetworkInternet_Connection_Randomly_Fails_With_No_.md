---
title: "Network/Internet Connection Randomly Fails With No Apparent Change - Edgy Eft"
date: 2007-01-30
forum: Networking &amp; Wireless
---

### Post by oldestree on 2007-01-30
Thanks in advance for your time and help.

I have recently installed Edgy on a laptop with the Intel PRO/Wireless 2100 adapter, which Ubuntu seems to have configured automatically using the ipw2100 driver. Everything works wonderfully, except after a random amount of time, usually between 5 and 15 minutes, the internet connection stops working. Everything I have tried indicates it is still connected, but I cannot access or ping anything, even my router, all return "Destination host unreachable" (these were run after the connection stopped):

iwconfig:

> lo        no wireless extensions.

eth1      IEEE 802.11b  ESSID:"wireless"  Nickname:"ipw2100"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:32:48:CA:94:6A  
          Bit Rate=11 Mb/s   Tx-Power:16 dBm  
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=95/100  Signal level=-63 dBm 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

ifconfig:

> eth1      Link encap:Ethernet  HWaddr 00:03:21:7A:7F:A4 
          inet addr: 192.168.0.101  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2185 errors:2 dropped:2 overruns:0 frame:0
          TX packets:1828 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1742553 (1.6 MiB)  TX bytes:330840 (323.0 KiB)
          Interrupt:5 Base address:0x2000 Memory:e0200000-e0200fff

lo        Link encap:Local Loopback 
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:84 (84.0 b)  TX bytes:84 (84.0 b)

route:

> Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     0      0        0 eth1
default         192.168.0.1     0.0.0.0         UG    0      0        0 eth1

lspci:

> 02:07.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)
02:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller (rev 81)

I captured the packets from the eth1 wireless with wireshark after the connection stopped, it just alternates between the ARP request and the SSPD notifys, with the occasional Browse Master message from my other XP machine on the network (however I cannot ping the browse master's IP, even though it receives these):

> Frame 118 (42 bytes on wire, 42 bytes captured)
Ethernet II, Src: Intel_7a:7f:a4 (00:03:21:7A:7F:A4), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Address Resolution Protocol (request)

No.     Time        Source                Destination           Protocol Info
    119 131.320062  Intel_7a:7f:a4        Broadcast             ARP      Who has 192.168.0.1?  Tell 192.168.0.101

Frame 119 (42 bytes on wire, 42 bytes captured)
Ethernet II, Src: Intel_7a:7f:a4 (00:03:21:7A:7F:A4), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Address Resolution Protocol (request)

No.     Time        Source                Destination           Protocol Info
    120 132.320130  Intel_7a:7f:a4        Broadcast             ARP      Who has 192.168.0.1?  Tell 192.168.0.101

Frame 120 (42 bytes on wire, 42 bytes captured)
Ethernet II, Src: Intel_7a:7f:a4 (00:03:21:7A:7F:A4), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Address Resolution Protocol (request)

No.     Time        Source                Destination           Protocol Info
    121 133.320188  Intel_7a:7f:a4        Broadcast             ARP      Who has 192.168.0.1?  Tell 192.168.0.101

Frame 121 (42 bytes on wire, 42 bytes captured)
Ethernet II, Src: Intel_7a:7f:a4 (00:03:21:7A:7F:A4), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Address Resolution Protocol (request)

No.     Time        Source                Destination           Protocol Info
    122 148.563667  192.168.0.1           239.255.255.250       SSDP     NOTIFY * HTTP/1.1

Frame 122 (294 bytes on wire, 294 bytes captured)
Ethernet II, Src: D-Link_ca:94:6a (00:32:48:ca:94:6a), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Internet Protocol, Src: 192.168.0.1 (192.168.0.1), Dst: 239.255.255.250 (239.255.255.250)
User Datagram Protocol, Src Port: 1900 (1900), Dst Port: 1900 (1900)
Hypertext Transfer Protocol

No.     Time        Source                Destination           Protocol Info
    123 148.566637  192.168.0.1           239.255.255.250       SSDP     NOTIFY * HTTP/1.1

Frame 123 (312 bytes on wire, 312 bytes captured)
Ethernet II, Src: D-Link_ca:94:6a (00:32:48:ca:94:6a), Dst: Broadcast (ff:ff:ff:ff:ff:ff)
Internet Protocol, Src: 192.168.0.1 (192.168.0.1), Dst: 239.255.255.250 (239.255.255.250)
User Datagram Protocol, Src Port: 1900 (1900), Dst Port: 1900 (1900)
Hypertext Transfer Protocol


Here is the bizarre part, I have the machine setup to dual boot with XP, and when I boot over to XP after the connection stops, it works fine, then when I boot back to Ubuntu after XP, the connection is up again, until it drops. Just restarting Ubuntu does not change anything, I have to boot XP, then boot back for the connection to return.

I confirmed that in /etc/resolv.conf I have:
nameserver 192.168.0.1

I have tried booting with pci=noacpi after the kernel, as I read in a similar thread, but it did not solve the issue.

Any help would be GREATLY appreciated. Thanks!

---

### Post by tturrisi on 2007-01-30
Try setting the AP to use a different channel, such as 11.  Some APs by default use channel 6, which is more prone to overlap w/ other wifi devices such as cordless phones, baby monitors, microwave ovens, etc.

---

### Post by oldestree on 2007-01-30
Thanks for the quick reply, though I am using channel 11, and this system only has this issue when running Ubuntu. When running XP on the same system, the connection has never had this issue. Also there is another XP laptop in the house which uses the wireless and has never had this issue. I am assuming this limits the problem to my Ubuntu installation on this machine.

---

### Post by eggdeng on 2007-01-30
I spent about 6 weeks doing my head in with similar issues, with wireless working on and off,  with ndiswrapper, without ndiswrapper, with this or that configuration. Lots of people on the forums seem to have been through the same rigmarole. In the end, I gave up and got hold of a wireless AP I can just plug into the ethernet card.
Even so, Edgy still sems to have a lot of issues. USB sound seems to be another grey area and the updates to the nvidia driver spell trouble. So my advice would be save yourself a lot of hassle and stick Dapper on your system unless you have a shitload of free time you don't know what to do with.

---

### Post by oldestree on 2007-01-30
Thanks for your suggestion. I will certainly consider switching to Dapper if I cannot get this problem solved.

---

### Post by oldestree on 2007-01-31
No one has any other ideas?

---

### Post by saheer on 2008-01-26
Try these,
Before connecting to internet just disable your networking.
Then open the terminal and type   '  sudo pon dsl-provider '.
Now browse the internet.
I don't know is it helps you ,but it is working with my system.
Thank you.

---

