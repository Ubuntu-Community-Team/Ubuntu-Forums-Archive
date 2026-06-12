---
title: "Problem getting Ubuntu 7.10 connected to the Internet from Acer laptop"
date: 2008-04-12
forum: Networking &amp; Wireless
---

### Post by AnAmateurDeveloper on 2008-04-12
Hi,

I have a problem connecting from Ubuntu to the internet. I am trying to run Ubuntu 7.10 within a virtual Pc (for a step by step tutorial on this look at [http://arcanecode.wordpress.com/2007/10/18/installing-ubuntu-710-under-virtual-pc-2007/](http://arcanecode.wordpress.com/2007/10/18/installing-ubuntu-710-under-virtual-pc-2007/)) on my Acer TravelMate 2700 laptop. I have a Virgin Media Broadband connection which works great from my Windows machine. My laptop has a "Realtek RTL8139/810x Family Fast Ethernet NIC" network card and I have a wired connection to the internet 

I have looked through the forums and am attaching the outputs of some common commands to help troubleshoot the problem. The outputs have been manually copied...there is a chance that they might contain a typo

ifconfig> 

eth0  	  Link encap:Ethernet HWaddr 00:03:FF:0A:E3:9D
	  inet6 addr: fe80::203:ffff:fe0a:e39d/64 Scope:Link
	  UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
	  RX packets:2497 errors:0 dropped:0 overruns:0 frame:0
	  TX packets:33 errors:0 dropped:0 overruns:0 carrier:0
	  collisions:0 txqueuelen:1000
	  RX bytes:205713 (200.8 KB) TX bytes:5219 (5.0 KB)
	  Interrupt:11 Base address:0xec00

eth0:avah Link encap:Ethernet  HWaddr 00:03:FF:0A:E3:9D
	  inet addr:169.254.8.189 Bcast:169.254.255.255 Mask:255.255.0.0
	  UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
	  Interrupt:11 Base address:0xec00

lo	  Link encap:Local Loopback
	  inet addr:127.0.0.1 Mast:255.0.0.0
	  inet6 addr: ::1/128 Scope:Host
	  UP LOOPBACK RUNNING MTU:16436 Metric:1
	  RX packets:16 errors:0 dropped:0 overruns:0 frame:0
	  TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
	  collisions:0 txqueuelen:0
	  RX bytes:1184 (1.1 KB) TX bytes:1184 (1.1 KB)		


lspci
> 
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (
AGP disabled) (rev 03)
00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 01)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
00:08.0 VGA compatible controller: S3 Inc. 86c764/765 [Trio32/64/64V+]
00:0a.0 Ethernet controller: Digital Equipment Corporation DECchip 21140 [Faster
Net] (rev 20)

dhclient eth0
> 
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:03:ff:0a:e3:9d
Sending on   LPF/eth0/00:03:ff:0a:e3:9d
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.25 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.25 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.25 port 67 interval 11
No DHCPOFFERS received.
No working leases in persistent database - sleeping

ping localhost> 

PING localhost (127.0.0.1) 56(84) bytes of data.
64 bytes from localhost (127.0.0.1): icmp_seq=1 ttl=64 time=7.62 ms
64 bytes from localhost (127.0.0.1): icmp_seq=2 ttl=64 time=0.389 ms
64 bytes from localhost (127.0.0.1): icmp_seq=3 ttl=64 time=0.708 ms
64 bytes from localhost (127.0.0.1): icmp_seq=4 ttl=64 time=0.377 ms
64 bytes from localhost (127.0.0.1): icmp_seq=5 ttl=64 time=0.359 ms

--- localhost ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4026ms
rtt min/avg/max/mdev = 0.359/1.891/7.625/2.870 ms

ipconfig -all (from my windows machine)> 

Windows IP Configuration

        Host Name . . . . . . . . . . . . : SHIRE
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Unknown
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No

Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : Realtek RTL8139/810x Family Fast Ethernet NIC
        Physical Address. . . . . . . . . : 00-02-3F-09-E3-9D
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        IP Address. . . . . . . . . . . . : 77.99.89.240
        Subnet Mask . . . . . . . . . . . : 255.255.254.0
        Default Gateway . . . . . . . . . : 77.99.88.1
        DHCP Server . . . . . . . . . . . : 62.31.32.125
        DNS Servers . . . . . . . . . . . : 194.168.4.100
                                            194.168.8.100
        Lease Obtained. . . . . . . . . . : 10 April 2008 22:19:26
        Lease Expires . . . . . . . . . . : 17 April 2008 12:25:10


Observations (I am not a Networking expert...these observations could be wrong)
[LIST=1]
[*]It seems that I do not get an IP address from the DHCP server
[*]My network manager in Ubuntu is configured for Wired DHCP connection
[*]The Ethernet controller shown in Windows is different to the one shown in Ubuntu
[/LIST]

---

### Post by zackf on 2008-04-13
Your observations seem correct to me. Does your Virtual PC have a setting to "bridge" your network connection from Windows?

It is not too concerning that Ubuntu is picking up a different network card. Sometimes is just sees the chipset, not necessarily the manufacturer.

---

### Post by AnAmateurDeveloper on 2008-04-13
Hi zackf,

Yes the Virtual PC does have a setting to bridge the network connection....I have installed Windows as Virtual operating systems before and it just works...this is the first time I am trying Ubuntu or any flavor of Linux though.

---

### Post by superprash2003 on 2008-04-13
in the ubuntu machine go to system->administratoin->network choose your network card(wired network connection(eth0)) then change from roaming mode to DHCP mdoe

---

### Post by AnAmateurDeveloper on 2008-04-13
Hi superprash2003

My network configuration is in DHCP...that was the first configuration I changed....I have also tried out manual IP but that does not work either....

---

### Post by superprash2003 on 2008-04-13
you are using ipv4 right? your eth0 output shows that you are not getting any ipv4 ip.. whereas your windows pc is getting 77.x.x.x

---

### Post by AnAmateurDeveloper on 2008-04-13
Hi superprash2003

Yes, you are right I am using ipv4....do you think I need to disable ipv6...also any ideas on how to do this.

---

### Post by superprash2003 on 2008-04-13
i dont think so..it should get an ip automatically.. when you manually enter an ip.. are you able to ping your router and the windows machine?

---

### Post by AnAmateurDeveloper on 2008-04-13
Hi,

No I couldn't the only thing I could ping was localhost and the ip address I had set.

---

### Post by zackf on 2008-04-13
super might be on to something, it did pull and ipv6 address, but I don't know it well enough that it may just be a default such as 169.154 ipv4 address.

What happens if you disable v6?

---

### Post by AnAmateurDeveloper on 2008-04-14
Hi,

I shall try this when I get home....will keep you guys posted.

Regards

---

### Post by AnAmateurDeveloper on 2008-04-16
Hi Guys,

Apologies it took so much time...but I was snowed under....

Anyways I did try to disable ipv6....I used the following method

> 
1. sudo gedit /etc/modprobe.d/aliases (or your preferred text editor)
2. Find the line: alias net-pf-10 ipv6
3. Edit this to: alias net-pf-10 off
4. Save the file and reboot


However it did not help too much....the ifconfig command now returns

> 
eth0	           Link encap:Ethernet HWaddr 00:03:FF:0A:E3:9D
	           UP BROADCAST RUNNING MULTICAST MTUL:1500 Metric:1
	            RX packets:6390 errors:0 dropped:0 overruns:0 frame:0
	            TX packets:55 errors:0 dropped:0 overruns:0 carrier:0
	            collisions:0 txqueuelen:100
	            RX bytes:488803 (477.3 KB) TX bytes:9262 (9.0 KB)
	            Interrupt:11 Base address:0xec00

eth0:avah   Link encap:Ethernet HWaddr 00:03:FF:0A:E3:9D
	            inet addr 169.254.8.189 Bcase:169.254.255.255 Mask:255.255.0.0
	            UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
	            Interrupt:11 Base address:0xec00

lo	            Link encap:Local Loopback
	            inet addr:127.0.0.1 Mask:255.0.0.0
	            UP LOOPBACK RUNNING MTU:16436 Metric:1
	            RX packets:28 errors:0 dropped:0 overruns:0 frame:0
	            TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
	            collisions:0 txqueuelen:0
	            RX bytes:2440 (2.3 KB) TX bytes:2440 (2.3 KB)	


Any other ideas???

---

