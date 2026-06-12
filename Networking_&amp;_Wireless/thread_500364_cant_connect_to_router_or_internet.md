---
title: "cant connect to router or internet"
date: 2007-07-13
forum: Networking &amp; Wireless
---

### Post by rushbrad on 2007-07-13
Hey

So i have tried finding a solution to this problem but have come up empty.  I have ubuntu going to my router (wired) and it can't connect to the router or the internet through the router.  It can however connect to the internet via a direct link to my dsl modem.  I also have a windows xp laptop running into the router (wired) but that gets internet fine through the router.  What could be the problem here, i have tried both static and dhcp.  Please help!

---

### Post by Mr. C. on 2007-07-13
Lets see the output from the command line from:

```
lspci
lspci -n
ifconfig -a
```

MrC

---

### Post by rushbrad on 2007-07-14
Sorry it took me so long to respond, here is the output from each of those commands:

lspci:
00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a2)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:08.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
01:08.1 Input device controller: Creative Labs SB Audigy Game Port (rev 04)
01:08.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04)
02:00.0 VGA compatible controller: nVidia Corporation GeForce 7300 GS (rev a1)

lspci -n:
00:00.0 0500: 10de:03ea (rev a1)
00:01.0 0601: 10de:03e0 (rev a2)
00:01.1 0c05: 10de:03eb (rev a2)
00:01.2 0500: 10de:03f5 (rev a2)
00:02.0 0c03: 10de:03f1 (rev a2)
00:02.1 0c03: 10de:03f2 (rev a2)
00:04.0 0604: 10de:03f3 (rev a1)
00:05.0 0403: 10de:03f0 (rev a2)
00:06.0 0101: 10de:03ec (rev a2)
00:07.0 0680: 10de:03ef (rev a2)
00:08.0 0101: 10de:03f6 (rev a2)
00:09.0 0604: 10de:03e8 (rev a2)
00:0b.0 0604: 10de:03e9 (rev a2)
00:0c.0 0604: 10de:03e9 (rev a2)
00:18.0 0600: 1022:1100
00:18.1 0600: 1022:1101
00:18.2 0600: 1022:1102
00:18.3 0600: 1022:1103
01:08.0 0401: 1102:0004 (rev 04)
01:08.1 0980: 1102:7003 (rev 04)
01:08.2 0c00: 1102:4001 (rev 04)
02:00.0 0300: 10de:01df (rev a1)

ifconfig -a:
eth0      Link encap:Ethernet  HWaddr 00:E0:4D:24:94:C1  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:4dff:fe24:94c1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:70 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1666 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9332 (9.1 KiB)  TX bytes:135110 (131.9 KiB)
          Interrupt:17 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:649 errors:0 dropped:0 overruns:0 frame:0
          TX packets:649 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:58328 (56.9 KiB)  TX bytes:58328 (56.9 KiB)

Let me know if you can see anything messed up, I am still new to Linux and Ubuntu.  Thanks!

---

### Post by Mr. C. on 2007-07-14
Your eth0 device appears configured and working.

What is the IP information of your router (ip address, netmask, broadcast)?

MrC

---

### Post by rushbrad on 2007-07-14
ip address: 192.168.1.1
Subnet: 255.255.255.0

I don't know how to find my broadcast, if you could let me know?

---

### Post by Mr. C. on 2007-07-14
I'm sure your broadcast is fine.

You should be able to ping each other's IP address.  From Ubuntu:

```
ping 192.168.1.1
```

If that succeeds, the two devices are communicating.  Then show the output from 
```

netstat -rn
cat /etc/resolv.conf

```
MrC

---

### Post by rushbrad on 2007-07-14
When I ping my router it just gives me "host unreachable".

---

### Post by Mr. C. on 2007-07-14
Please show actual commands and output.  Still need output from previously mentioned commands as well.

MrC

---

### Post by rushbrad on 2007-07-14
Sorry bout that, here ya go:

ping 192.168.1.1:
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 192.168.1.2 icmp_seq=1 Destination Host Unreachable
From 192.168.1.2 icmp_seq=2 Destination Host Unreachable
From 192.168.1.2 icmp_seq=3 Destination Host Unreachable
From 192.168.1.2 icmp_seq=4 Destination Host Unreachable

--- 192.168.1.1 ping statistics ---
4 packets transmitted, 0 received, +4 errors, 100% packet loss, time 3009ms
, pipe 3


netstat -rn:
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 eth0


cat /etc/resolv.conf:
search Belkin
nameserver 192.168.2.1

---

### Post by Mr. C. on 2007-07-14
Something is not making sense here:

a) your system's your routing table is missing a loopback route
b) you have your name server listed as IP address 192.168.2.1, which is not on your configured network (at least, as far as you've told us).  Your network is configured to be 192.168.1.0/24, not 192.168.2.0/24.
c) Destination Host Unreachable typically means a routing problem.  Your Ubuntu station was able to deliver the packet to the network, but your router did not reply to an ARP packet.  This may indicate a cable problem.  Verify that your link lights are on on the back of your router and your ethernet card.  In addition, make sure your router is not configured to block ping requests, and that no firewall is blocking your connection.
d) remove the search Belkin line from your /etc/resolv.conf line - it serves no purpose and is incorrect.

I presume you have your Ethernet cable from the Ubuntu station cable plugged into the LAN port on your router.

MrC

---

### Post by rushbrad on 2007-07-14
Ok, so I fixed/verified everything except the loopback route.

now my cat /etc/resolv.conf reads:

nameserver 192.168.1.1


I checked the lights on my router, and the back of my ethernet card and they are all good.  I even swapped the cable i was using with one that I had working with this laptop to make sure that wasn't it.  Still nothing though, the ping remains the same.  Thanks for the help so far, I am at a loss still though:confused:

---

### Post by Mr. C. on 2007-07-14
What is the ip information from your Windows station?  From windows, start a command shell, and type:

```
ipconfig /all

```
MrC

---

### Post by rushbrad on 2007-07-14
i didnt know how to get the  text out so I snagged a picture of it.  Should be attached.

---

### Post by rushbrad on 2007-07-14
Ok I fixed it now.  I had to reset my router.  Thenset the router and ubuntu to DHCP and it for some reason worked, although I am almost certain I had it like that before.  In any event, thanks for the help!

---

### Post by Mr. C. on 2007-07-14
That's good news.

For the future, you can right click on the Windows command window, select Mark, and then select the text you want. Hit Enter when completed, and you will have a copy of that text to paste elsewhere.

MrC

---

### Post by unisol on 2007-07-30
i am having a similar problem with feisty. only i am using a wireless connection.i have  a linlsys WMP54GR  wireless pci card. iwconfig rao. using feisty's rt61 driver. it will detect my home network when in roaming mode, but not with DHCP. and even when it says it connects toe network, there is still no internet access. myrouter is a WRT54G wireless router connected to ethernet port on pc1. the setup is internet-cable modem-wireless router -pc. all three of my windows pcs connect and work with no problem. also the winxp partition on my linux box connects with no problem. i just cant get ubuntu to connect to the router. any help would be greatly appreciated.

---

### Post by SpiritIsReality on 2007-09-29
howdy
unisol...I think you need to use ndiswrapper to get your wireless card to work.
please see the following links and look for instructions that apply to your card in particular
when it comes to finding a driver from ndiswrapper.sourceforge.net/
check your wireless card manual, or linksys.com for correct version of card.
looks like the instructions for a bcm-43xx chip will work. I would suggest to not use the bcm-fwcutter method,
use the ndiswrapper method, install from synaptic, if it works good, if not then install from source. and don't
forget to blacklist the open source bcm43xx driver. check in the links for the instructions on how to do it.
if you are using amd64 follow that page, if not then
[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM43xx_%28all,_ndiswrapper/firmware%29?highlight=%28ndiswrapper%29](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM43xx_%28all,_ndiswrapper/firmware%29?highlight=%28ndiswrapper%29)
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?highlight=%28ndiswrapper%29](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?highlight=%28ndiswrapper%29)

[https://help.ubuntu.com/community/?action=fullsearch&context=180&value=ndiswrapper&titlesearch=Titles](https://help.ubuntu.com/community/?action=fullsearch&context=180&value=ndiswrapper&titlesearch=Titles)
[https://help.ubuntu.com/community/WifiDocs](https://help.ubuntu.com/community/WifiDocs)
[http://www.google.ca/search?hl=en&q=site%3Andiswrapper.sourceforge.net+WMP54G&btnG=Search&meta=](http://www.google.ca/search?hl=en&q=site%3Andiswrapper.sourceforge.net+WMP54G&btnG=Search&meta=)
trails

---

