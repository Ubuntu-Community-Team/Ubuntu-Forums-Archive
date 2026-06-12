---
title: "IP4 Networking Stops"
date: 2007-12-11
forum: Networking &amp; Wireless
---

### Post by bkendall on 2007-12-11
Hello, I'm new to Linux and this is my first installation. I have Ubuntu 7.10 installed on a custom built machine at home, dual booting with Windows XP Pro x64. None of the parts are fancy and I'm using a motherboard with a fairly common chipset (nForce 650i Ultra). Ubuntu installed with no problems and ran great for a few days, then I started getting networking issues. Randomly I'm kicked off of the internet and if I run ifconfig I see that I no longer have an IPv4 address, only IPv6. Rebooting the PC doesn't necessarily fix the problem, nor does disconnecting and reconnecting the network cable. If I boot into Windows on the exact same hardware, however, things work fine.

I'm using the integrated network adapter on the motherboard. This adapter is plugged straight into one of the LAN ports on a Sonicwall TZ150.

I've made sure that Ubuntu is up to date.

Can someone please help me? This is driving me crazy. I'm ready to make the switch to Linux but I can't do so without a reliable internet connection.

Thanks!

---

### Post by santosh_gr on 2007-12-11
this normally happens when there is an ip address conflict on your system.  are there any other workstations using the same ip? how are your ip addresses assigned is it by dhcp or static?

if you are sure that ip is unique to the system, then try disabling ipv6 from you ubuntu box.  You can do this by modifying the /etc/modprobe.d/aliases file.  You need to comment out the line shown below.

alias net-pf-10 ipv6

change it to 

# alias net-pf-10 ipv6

and reboot the box so that ipv6 is no longer loaded during startup.

---

### Post by santosh_gr on 2007-12-11
hopefully it should sort things out for you.

---

### Post by bkendall on 2007-12-12
Addresses are assigned via DHCP, and I have a reservation set for my PC. I guess I should have mentioned that, sorry. I've also tried configuring the network adapter for DHCP, Static IP, etc with no effect.

I'll try your suggestions and report back this afternoon.

Thanks!

---

### Post by bkendall on 2007-12-12
Alright, so this evening I came home and fired Ubuntu up. It came up and worked fine. I made the suggested changes and then booted into Windows to get some files copied over to my thumb drive. Everything worked. I booted back into Ubuntu and things were fine. I then had to boot back to Windows to get more files... and when I came back to Ubuntu it didn't detect the live network connection until I pulled the cable out of the PC and plugged it back in.

Here's an ifconfig:
user@user-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:04:4B:06:4E:36  
          inet addr:192.168.200.50  Bcast:192.168.200.255  Mask:255.255.255.0
          inet6 addr: fe80::204:4bff:fe06:4e36/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10607 errors:8 dropped:0 overruns:0 frame:2
          TX packets:7138 errors:14 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10339982 (9.8 MB)  TX bytes:1613017 (1.5 MB)
          Interrupt:16 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:112 (112.0 b)  TX bytes:112 (112.0 b)


I don't think that those transmit and receive errors are good.

 This is a brand new ethernet cable BTW (which infuriates me because I had to pay $14 at BestBuy for a $3 cable).

Thanks!



UPDATE:

Right after I made the above post it died again. Here's another ifconfig and some ping attempts to my gateway:

user@user-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:04:4B:06:4E:36  
inet addr:192.168.200.50  Bcast:192.168.200.255  Mask:255.255.255.0
inet6 addr: fe80::204:4bff:fe06:4e36/64 Scope:Link
UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
RX packets:37572 errors:30 dropped:0 overruns:0 frame:14
TX packets:22452 errors:18 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:47045723 (44.8 MB)  TX bytes:3121282 (2.9 MB)
Interrupt:16 Base address:0x4000

lo        Link encap:Local Loopback  
inet addr:127.0.0.1  Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING  MTU:16436  Metric:1
RX packets:8 errors:0 dropped:0 overruns:0 frame:0
TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0 
RX bytes:719 (719.0 b)  TX bytes:719 (719.0 b)

user@user-desktop:~$ ping 192.168.200.1
PING 192.168.200.1 (192.168.200.1) 56(84) bytes of data.
From 192.168.200.50 icmp_seq=2 Destination Host Unreachable
From 192.168.200.50 icmp_seq=3 Destination Host Unreachable
From 192.168.200.50 icmp_seq=4 Destination Host Unreachable
From 192.168.200.50 icmp_seq=6 Destination Host Unreachable
From 192.168.200.50 icmp_seq=7 Destination Host Unreachable
From 192.168.200.50 icmp_seq=8 Destination Host Unreachable

--- 192.168.200.1 ping statistics ---
8 packets transmitted, 0 received, +6 errors, 100% packet loss, time 6999ms, pipe 3

I shut down and booted right into Windows, which worked fine.

---

### Post by bkendall on 2007-12-13
I'm bumping this post.

Based on my Windows background it seems to me like this is a driver issue. I say this because I only experience the problems on one OS and not the other.

I tried Nvidia's web site and they state that the drivers for their chipsets are built into the kernel and there are no individual downloads. Is there any other way to get a different driver?

I may flatten the box and either try an older version of Ubuntu or a different distro altogether and see what my results are.

---

### Post by bkendall on 2007-12-14
Well, after hours of digging last night I believe I've resolved the issue.

It seems that my /etc/networking/interfaces file was not configured correctly; it's my understanding that it should list the interface followed by the configuration, and in my case it listed the configuration followed by the interface name. I'm not sure how this happened as I've been using the GUI to configure my NIC up until this point, but once I edited the file the problem seems to be resolved.

---

