---
title: "how to discover device address on the LAN?"
date: 2007-05-26
forum: Networking &amp; Wireless
---

### Post by evaldas on 2007-05-26
Hi,

I have a device (router, possibly bricked) on the LAN, and I don't know it's ip or mac address. I don't know it's default ip address (reset button as described in the manual doesn't help). I guess there should be some way to do arp broadcast or ping broadcast or something like this to find out the address. I did some googling, but didn't find working solution. For example 'ping -b 255.255.255.255' doesn't give any reply :(
please help.

**UPDATE**:
So to summary, I have an unknown device on the network (lets pretend we don't it's a router). I know its MAC address, but not IP address. I also don't know on what IP subnet the IP address is. Device doesn't act as a DHCP server or as a DHCP client. It doesn't have any reset buttons, or manuals. So with this information (only MAC address), is there a way to find out the IP address of the device? I believe it has somehow respond to broadcasted packets/frames, but I don't know what exact tools/commands to use.

Thank you

---

### Post by dbott67 on 2007-05-26
What's the make & model of router?

If you haven't restarted your computer since the last time the router worked, you can probably get the IP address using the route command:
```
dbott@feisty:~$ [COLOR=Red]**route -n**[/COLOR]
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         [COLOR=Purple]192.168.1.1[/COLOR]     0.0.0.0         UG    0      0        0 eth0

```

The router will be listed as the 'Gateway' and will (more than likely) have an IP address like:

- 192.168.x.y
- 10.x.y.z

-Dave

---

### Post by evaldas on 2007-05-26
I don't know even on what subnet it is. It's not working.
It tries to power up, then the LAN led lights up for about 5 seconds. And then it starts all over again. I guess the bootloader of the device gives me the window of 5 seconds to upload firmware or configuration file via tftp. But I don't know the address of the device.
It's zyxel router. I uploaded corrupted backup config file (not firmware) to it and now it doesn't boot. As I said reset button doesn't reset it's ip address to 192.168.1.1. I guess the bootloader of the device has another ip address.

---

### Post by dbott67 on 2007-05-26
What is the exact model of the zyxel router?

Can you post the output of the following 3 commands from your computer?
```
dbott@feisty:~$ **route -n**
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
```
```
dbott@feisty:~$ [COLOR=Red]**ifconfig -a**[/COLOR]
eth0      Link encap:Ethernet  HWaddr 00:50:BA:C0:A7:55  
          inet addr:192.168.1.106  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::250:baff:fec0:a755/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:790121 errors:0 dropped:0 overruns:0 frame:0
          TX packets:759977 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:605380958 (577.3 MiB)  TX bytes:270911800 (258.3 MiB)
          Interrupt:17 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:719197 errors:0 dropped:0 overruns:0 frame:0
          TX packets:719197 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:70668010 (67.3 MiB)  TX bytes:70668010 (67.3 MiB)
```


```
dbott@feisty:~$[COLOR=Red]** cat /etc/network/interfaces**[/COLOR] 
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

```

Thanks,
Dave

---

### Post by dbott67 on 2007-05-26
Note: if you can't get online with your system & you have a USB thumb drive (or floppy or some other removable media you can write to) you can use the 'redirect' function to write the output of the commands to a file and then copy them to the USB. Start in your home directory (cd ~):

```
cat /etc/network/interfaces > interfaces.txt
```
```
ifconfig -a > ifconfig.txt
```
```
route -n > route.txt
```
Copy all 3 files to floppy/USB, bring them over to Windows and then post them here. All five files should be in your home directory.

-Dave

---

### Post by evaldas on 2007-05-26
I'm sorry but the router was long time ago disconnected, and right now I'm using other modem/router, so these commands (route, ifconfig, etc) won't help at all. sorry.

BTW, I discovered MAC address for that device (Zyxel Prestige 645R) by searching the firefox browser cache (I did router management through the firefox some time ago).

So now, maybe I can perform arp or rarp (or other mumbo jumbo :) ) broadcast request to find the IP address? but how?

---

### Post by dbott67 on 2007-05-26
In order to manage the router via a web browser, your computer must be on the same subnet as the Zyxel router.  So, what you have to do is connect a computer to the Zyxel router and then try to obtain an IP address:
```
dbott@feisty:~$ sudo dhclient
Password:
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:50:ba:c0:a7:55
Sending on   LPF/eth0/00:50:ba:c0:a7:55
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPOFFER from 192.168.1.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.106 -- renewal in 286663 seconds.

```**If you get an IP address assigned** ([COLOR=Purple]*other than 169.254.x.y, which is part of the Automatic Private IP Address space [aka APIPA]*[/COLOR]), then your router's DHCP service is functioning.  It should be in the 192.168.1.100 range if you did successfully reset the router to factory settings.

You should be able to obtain the actual router IP by using:
```
route -n
```Open Firefox and type in the gateway address listed (i.e. 192.168.1.1).

** If you do not get an IP address **(or you get a 169.254.x.y address) then your router's DHCP service is not functioning.  From here, you need to set a static IP address on your computer.

The address you choose should be on the same subnet as the manufacturer's default setting (i.e. if the router is 192.168.1.1, you should set your network card to:

IP Address: 192.168.1.50
Subnet mask: 255.255.255.0
Gateway: 192.168.1.1

Then try to connect again by typing 192.168.1.1 in your browser.

If that fails, the router may be a brick.  Does it have a serial port that you can telnet into?

-Dave

---

### Post by evaldas on 2007-05-27
dbott67, I'm not that dumb, I know (to some extent) how networks work. All of the solutions posted above, were the first thing I tried when the problem arose. And no, the router doesn't have a serial port, if it would have it I wouldn't ask for help here.

So to summary, I have an unknown device on the network (lets pretend we don't it's a router). I know its MAC address, but not IP address. I also don't know on what IP subnet the IP address is. Device doesn't act as a DHCP server or as a DHCP client. It doesn't have any reset buttons, or manuals. So with this information (only MAC address), is there a way to find out the IP address of the device? I believe it has somehow respond to broadcasted packets/frames, but I don't know what exact tools/commands to use.

Thank you

---

### Post by Austin_KW on 2007-05-27
Have a look in your apr cache after you connect the router; You may get luck and it might broadcast its arp.
"arp -n"

You might try  arping for likely addresses ;
arping 192.168.x.1  -I eth0 (for x = 0,1,2 and assuming it is connected to eth0)

Otherwise google for an arping script that tests the entire private address space, but these can take a while (as it is a large space)

---

### Post by chili555 on 2007-05-27
If you have an idea of what range its IP might be in, *fping* might help:```
chili@LAPTOP:~$ fping -g 192.168.1.98 192.168.1.120
192.168.1.99 is alive
192.168.1.100 is alive
192.168.1.102 is alive
192.168.1.101 is alive
192.168.1.103 is alive
192.168.1.111 is alive
192.168.1.116 is alive
192.168.1.118 is alive
```I know the machine I am on is .102, my wife's is .118, my server is .101, etc., so I can, by process of elimination, figure out who the mystery guest is.

Since your mystery guest may be a x.1.1 or x.0.1, you may have to fping the whole range:```
fping -g 192.168.0.1 192.168.0.254
```It will take some time.

---

### Post by Austin_KW on 2007-05-27
One other thing, Some router when brick'ed enter a tftp server from the boot loader. If you a lucky it will brodcast a packet (with its address and instructions) when it does so. You might install wireshark and capture the packets on the eth interface when you power the router on.

BTW one other default address I have seen on bootloaders is 192.168.11.1
arping 192.168.11.1 -I eth0

---

### Post by dbott67 on 2007-05-27
> **evaldas said:**
> dbott67, I'm not that dumb, I know (to some extent) how networks work. All of the solutions posted above, were the first thing I tried when the problem arose. And no, the router doesn't have a serial port, if it would have it I wouldn't ask for help here.

I never said or implied that you were (or even thought it, for that matter).  Unfortunately, forum posts do not permit us to know the skill level of those involved.  I was only offering explicit instructions to:

a) make it easy for you in case you did not know how to perform the requested actions.
b) provide explicit instructions for those that might come across this thread in the future.
c) make sure you didn't overlook something.

I've been a network admin / IT manager for over 12 years and I've previously taught post-graduate courses in networking for 5 years; sometimes I overlook the simplest things when troubleshooting --- the bottom line is we always start with the least-drastic step and use a process of elimination to figure out where the problem lies.  You never specified what you did or did not do; I only requested that you perform the above steps so that I can eliminate those as the source of the problem.

> **evaldas said:**
> 
I believe it has somehow respond to broadcasted packets/frames, but I don't know what exact tools/commands to use.

Thank you

There are only a few limited situations where you can [determine the IP from the MAC address]("http://compnetworking.about.com/od/networkprotocolsip/f/convertipmacadd.htm"), but it would be dependent upon the device having SNMP software installed and functioning properly.

Generally speaking, broadcasts are sent to the subnet not directly to the MAC address.  If the device is not on the subnet, it won't respond to the request.  So, we really need to know which subnet it is.

All of the steps below may be for naught, as the old saying goes: "If it looks like a duck, walks like a duck and quacks like a duck, it's probably a duck" (or in your case, bricked).

As chili555 suggests, using **fping** on a number of different subnets is a good method.  You can re-direct the output to a file to see the hosts that are alive using the command below:
```
dbott@feisty:~$ [COLOR=Red]**fping -s -g -c 1 192.168.1.0/24 > ip.txt**[/COLOR]
ICMP Host Unreachable from 192.168.1.106 for ICMP Echo sent to 192.168.1.3
ICMP Host Unreachable from 192.168.1.106 for ICMP Echo sent to 192.168.1.4
ICMP Host Unreachable from 192.168.1.106 for ICMP Echo sent to 192.168.1.5
ICMP Host Unreachable from 192.168.1.106 for ICMP Echo sent to 192.168.1.6
<snipped for brevity>
192.168.1.245 : xmt/rcv/%loss = 1/0/100%
192.168.1.246 : xmt/rcv/%loss = 1/0/100%
192.168.1.247 : xmt/rcv/%loss = 1/0/100%
192.168.1.248 : xmt/rcv/%loss = 1/0/100%
192.168.1.249 : xmt/rcv/%loss = 1/0/100%
192.168.1.250 : xmt/rcv/%loss = 1/0/100%
192.168.1.251 : xmt/rcv/%loss = 1/0/100%
192.168.1.252 : xmt/rcv/%loss = 1/0/100%
192.168.1.253 : xmt/rcv/%loss = 1/0/100%
192.168.1.254 : xmt/rcv/%loss = 1/0/100%
192.168.1.255 : xmt/rcv/%loss = 0/0/0%

     256 targets
       8 alive
     250 unreachable
       0 unknown addresses

       0 timeouts (waiting for response)
     254 ICMP Echos sent
       8 ICMP Echo Replies received
     246 other ICMP received

 0.10 ms (min round trip time)
 104 ms (avg round trip time)
 636 ms (max round trip time)
       12.979 sec (elapsed real time)

```Then, look at the resultant file (ip.txt in the above example):
```
dbott@feisty:~$ cat ip.txt 
192.168.1.2   : [0], 84 bytes, 0.28 ms (0.28 avg, 0% loss)
192.168.1.10  : [0], 84 bytes, 14.1 ms (14.1 avg, 0% loss)
192.168.1.102 : [0], 84 bytes, 4.36 ms (4.36 avg, 0% loss)
192.168.1.106 : [0], 84 bytes, 0.12 ms (0.12 avg, 0% loss)
192.168.1.109 : [0], 84 bytes, 9.88 ms (9.88 avg, 0% loss)
192.168.1.101 : [0], 84 bytes, 2007 ms (2007 avg, 0% loss)
192.168.1.1   : [0], 84 bytes, 5.55 ms (5.55 avg, 0% loss)

```Repeat this for all possible subnets.  There are a few other discovery tools that can perform similar scans, such as nmap:
```
dbott@feisty:~$ [COLOR=Red]**nmap -sP 192.168.1.0/24**[/COLOR]

Starting Nmap 4.20 ( http://insecure.org ) at 2007-05-27 14:13 EDT
Host 192.168.1.1 appears to be up.
Host 192.168.1.2 appears to be up.
Host 192.168.1.10 appears to be up.
Host 192.168.1.102 appears to be up.
Host 192.168.1.106 appears to be up.
Host 192.168.1.109 appears to be up.
Nmap finished: 256 IP addresses (6 hosts up) scanned in 9.404 seconds

```There's also icmpenum, hping and gping (although I don't think they're in the repositories).

Good luck.

-Dave

---

### Post by evaldas on 2007-05-28
Thank you all for your replies, but it's a "duck" (brick) :)

Wireshark doesn't capture any packet on router startup. Just to make sure that I used Wireshark properly, plugged the other router and was able to see ARP broadcasts on startup.

Scanned with nmap all 192.168.x.x range - nothing. Tried to scan whole 10.x.x.x address space, but after 12 hours and 2 000 000 captured packets I gave up.

once again, thanks

---

