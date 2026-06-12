---
title: "nmap more than 4096 hosts"
date: 2018-07-20
forum: Networking &amp; Wireless
---

### Post by kazakore on 2018-07-20
I'm trying to find out the ip address a piece of equipment with no documentation has been configured too (attempts to check over the serial connection didn't work.) I am connected point to point via an ethernet cable so doing a scan for active hosts it should be the only result (assuming it responds to Ping.)

```
nmap -v -e enp0s25 -sn 192.168.0.0/16

```

use nmap, verbose mode, select ethernet adapter and no port scan (ping only) on the 192.168.x.x range using the /16 CIDR block.

BUT 256*256 would give total number of hosts to be scanned as 65,536. nmap says:
```
Scanning 4096 hosts [2 ports/host]
```

So can I actually scan the whole range in one go? I'm not even certain it is on the 192.168 subnet (but it's most likely) it might also be in 10.x.x.x somewhere. I had seen an example ending with  "192.168.0.0.16 10.0.0.0/8" but that still says it's scanning 4096 hosts.

Will it just work despite what it reports or an I missing something?


EDIT: Patience is a virtue! Seems it doers it in 5096 blocks and then moves onto the next block once the previous is completed. Once the scan is done in full and I have thus confirmed this to myself I will mark as Solved.

---

### Post by TheFu on 2018-07-20
If it is on a physical network, I'd use arp to get the MAC to IP mapping.

---

### Post by kazakore on 2018-07-20
> **TheFu said:**
> If it is on a physical network, I'd use arp to get the MAC to IP mapping.


arp? Sorry I'm pretty new to this. Unfortunately didn't find anything in the 192.168.x.x range (unless I did something wrong) so some quick way to do a full network scan could still be useful. It's only directly connected, not even through a router or switch, so not going to adversely affect anything else while running.

---

### Post by kazakore on 2018-07-20
Hmmm I may have had the ethernet connector set up wrong before (I hadn't set it to Shared To Other Computers) so may have not even been visible....

Now I have done a point2point test between two laptops and shown that works so would like to run the scan again. However running against a slightly annoying issue! As soon as I enable the ethernet connection my Wi-Fi internet dies! How can I keep my internet working on wireless while scanning a separate network on the ethernet port??

---

### Post by TheFu on 2018-07-20
The easy answer for someone unfamiliar with networking concepts is to use different subnets.  
arp is a physical connection tool - layer 2, not layer 3.  If a computer "sees" the other device using a wired  ehternet connection, then you can run '**arp**' to see all the devices on the same ethernet physical network. Arp is used on all ethernet networks.

For devices that don't get an IP from either static settings or a DHCP, they usually default to a 169.x.x.x subnet.  There is a standard about it.

If you said what the equipment was, I bet someone could find the documentation which would clearly say how networking defaults.

---

### Post by kazakore on 2018-07-20
> **TheFu said:**
> The easy answer for someone unfamiliar with networking concepts is to use different subnets.  
arp is a physical connection tool - layer 2, not layer 3.

For devices that don't get an IP from either static settings or a DHCP, they usually default to a 169.x.x.x subnet.  There is a standard about it.

If you said what the equipment was, I bet someone could find the documentation which would clearly say how networking defaults.

It's a UPS, it will almost definitely have been set up on one of our 192.168 subnets at some point, most likely 192.168.100.x (although maybe on .30 or .40 and a few others are in use too.) This means it's within the subnet range of the connection I want my WiFi on for the external world too.

Guess  the easy answer would be run the scan on a VM and set the eth adapter to down on the host..... Thought there may be an easy way to just say "use this for internet/firefox" or something similar....

---

### Post by TheFu on 2018-07-20
My home UPSes use serial connections.  I have a few 1500VAs.

Model of UPS?  Documentation for those is pretty easy to find whether they are 250VA or whole data center models.

---

### Post by kazakore on 2018-07-20
My colleague spent most of yesterday trying to get Serial COMMS working and failed so thought I'd try and different attack vector (and learn something about a tool I should really know how to use in the process.) I might come back to attempting the serial port tomorrow. Another benefit of trying to get this working is I can sit in comfort and use ready CAT6 tielines without having to mess around finding adapters or sitting in a cold apps room ;)


Back to your arp suggestion. Just did a quick scan using both arp and nmap on the wifi. Seems strange to me that only the gateway at 192.168.100.1 shows on both scans!

```
$ nmap -T5   -sn 192.186.100.0/24

Starting Nmap 7.60 ( https://nmap.org ) at 2018-07-20 15:55 BST
Nmap scan report for d192-186-100-1.static.comm.cgocable.net (192.186.100.1)
Host is up (0.094s latency).
Nmap scan report for d192-186-100-2.static.comm.cgocable.net (192.186.100.2)
Host is up (0.10s latency).
Nmap scan report for d192-186-100-5.static.comm.cgocable.net (192.186.100.5)
Host is up (0.098s latency).
Nmap scan report for d192-186-100-6.static.comm.cgocable.net (192.186.100.6)
Host is up (0.096s latency).
Nmap scan report for d192-186-100-13.static.comm.cgocable.net (192.186.100.13)
Host is up (0.095s latency).
Nmap scan report for d192-186-100-21.static.comm.cgocable.net (192.186.100.21)
Host is up (0.098s latency).
Nmap scan report for d192-186-100-25.static.comm.cgocable.net (192.186.100.25)
Host is up (0.095s latency).
Nmap scan report for d192-186-100-29.static.comm.cgocable.net (192.186.100.29)
Host is up (0.095s latency).
Nmap scan report for d192-186-100-30.static.comm.cgocable.net (192.186.100.30)
Host is up (0.093s latency).
Nmap scan report for d192-186-100-37.static.comm.cgocable.net (192.186.100.37)
Host is up (0.095s latency).
Nmap scan report for d192-186-100-38.static.comm.cgocable.net (192.186.100.38)
Host is up (0.099s latency).
Nmap scan report for d192-186-100-41.static.comm.cgocable.net (192.186.100.41)
Host is up (0.094s latency).
Nmap scan report for d192-186-100-45.static.comm.cgocable.net (192.186.100.45)
Host is up (0.11s latency).
Nmap scan report for mail.mediaduo.com (192.186.100.46)
Host is up (0.10s latency).
Nmap scan report for d192-186-100-49.static.comm.cgocable.net (192.186.100.49)
Host is up (0.094s latency).
Nmap scan report for d192-186-100-53.static.comm.cgocable.net (192.186.100.53)
Host is up (0.10s latency).
Nmap scan report for d192-186-100-54.static.comm.cgocable.net (192.186.100.54)
Host is up (0.096s latency).
Nmap scan report for d192-186-100-57.static.comm.cgocable.net (192.186.100.57)
Host is up (0.11s latency).
Nmap scan report for d192-186-100-61.static.comm.cgocable.net (192.186.100.61)
Host is up (0.097s latency).
Nmap scan report for mail.gualtierimechanical.com (192.186.100.62)
Host is up (0.096s latency).
Nmap scan report for d192-186-100-65.static.comm.cgocable.net (192.186.100.65)
Host is up (0.095s latency).
Nmap scan report for server.prostaffworks.ca (192.186.100.66)
Host is up (0.098s latency).
Nmap scan report for d192-186-100-69.static.comm.cgocable.net (192.186.100.69)
Host is up (0.099s latency).
Nmap scan report for d192-186-100-77.static.comm.cgocable.net (192.186.100.77)
Host is up (0.10s latency).
Nmap scan report for mail.h-mlaw.ca (192.186.100.78)
Host is up (0.096s latency).
Nmap scan report for d192-186-100-81.static.comm.cgocable.net (192.186.100.81)
Host is up (0.095s latency).
Nmap scan report for d192-186-100-89.static.comm.cgocable.net (192.186.100.89)
Host is up (0.094s latency).
Nmap scan report for d192-186-100-97.static.comm.cgocable.net (192.186.100.97)
Host is up (0.094s latency).
Nmap scan report for d192-186-100-98.static.comm.cgocable.net (192.186.100.98)
Host is up (0.10s latency).
Nmap scan report for d192-186-100-121.static.comm.cgocable.net (192.186.100.121)
Host is up (0.100s latency).
Nmap scan report for vpn.erca.org (192.186.100.122)
Host is up (0.099s latency).
Nmap scan report for pdc.erca.org (192.186.100.123)
Host is up (0.097s latency).
Nmap scan report for d192-186-100-137.static.comm.cgocable.net (192.186.100.137)
Host is up (0.096s latency).
Nmap scan report for mail.caxtonmark.com (192.186.100.138)
Host is up (0.10s latency).
Nmap scan report for d192-186-100-153.static.comm.cgocable.net (192.186.100.153)
Host is up (0.096s latency).
Nmap scan report for d192-186-100-161.static.comm.cgocable.net (192.186.100.161)
Host is up (0.098s latency).
Nmap scan report for d192-186-100-162.static.comm.cgocable.net (192.186.100.162)
Host is up (0.093s latency).
Nmap scan report for d192-186-100-165.static.comm.cgocable.net (192.186.100.165)
Host is up (0.097s latency).
Nmap scan report for d192-186-100-166.static.comm.cgocable.net (192.186.100.166)
Host is up (0.11s latency).
Nmap scan report for d192-186-100-169.static.comm.cgocable.net (192.186.100.169)
Host is up (0.11s latency).
Nmap scan report for d192-186-100-170.static.comm.cgocable.net (192.186.100.170)
Host is up (0.098s latency).
Nmap scan report for d192-186-100-173.static.comm.cgocable.net (192.186.100.173)
Host is up (0.10s latency).
Nmap scan report for d192-186-100-174.static.comm.cgocable.net (192.186.100.174)
Host is up (0.10s latency).
Nmap scan report for d192-186-100-177.static.comm.cgocable.net (192.186.100.177)
Host is up (0.10s latency).
Nmap scan report for d192-186-100-181.static.comm.cgocable.net (192.186.100.181)
Host is up (0.095s latency).
Nmap scan report for d192-186-100-185.static.comm.cgocable.net (192.186.100.185)
Host is up (0.094s latency).
Nmap scan report for d192-186-100-189.static.comm.cgocable.net (192.186.100.189)
Host is up (0.094s latency).
Nmap scan report for d192-186-100-190.static.comm.cgocable.net (192.186.100.190)
Host is up (0.094s latency).
Nmap scan report for d192-186-100-193.static.comm.cgocable.net (192.186.100.193)
Host is up (0.094s latency).
Nmap scan report for d192-186-100-194.static.comm.cgocable.net (192.186.100.194)
Host is up (0.10s latency).
Nmap scan report for d192-186-100-197.static.comm.cgocable.net (192.186.100.197)
Host is up (0.10s latency).
Nmap scan report for d192-186-100-198.static.comm.cgocable.net (192.186.100.198)
Host is up (0.11s latency).
Nmap scan report for d192-186-100-201.static.comm.cgocable.net (192.186.100.201)
Host is up (0.098s latency).
Nmap scan report for mail.windsorchamber.org (192.186.100.202)
Host is up (0.10s latency).
Nmap scan report for d192-186-100-209.static.comm.cgocable.net (192.186.100.209)
Host is up (0.095s latency).
Nmap scan report for d192-186-100-210.static.comm.cgocable.net (192.186.100.210)
Host is up (0.097s latency).
Nmap scan report for d192-186-100-213.static.comm.cgocable.net (192.186.100.213)
Host is up (0.093s latency).
Nmap scan report for d192-186-100-229.static.comm.cgocable.net (192.186.100.229)
Host is up (0.10s latency).
Nmap scan report for d192-186-100-237.static.comm.cgocable.net (192.186.100.237)
Host is up (0.10s latency).
Nmap scan report for d192-186-100-241.static.comm.cgocable.net (192.186.100.241)
Host is up (0.098s latency).
Nmap scan report for d192-186-100-245.static.comm.cgocable.net (192.186.100.245)
Host is up (0.097s latency).
Nmap scan report for d192-186-100-246.static.comm.cgocable.net (192.186.100.246)
Host is up (0.10s latency).
Nmap scan report for d192-186-100-249.static.comm.cgocable.net (192.186.100.249)
Host is up (0.100s latency).
Nmap scan report for d192-186-100-253.static.comm.cgocable.net (192.186.100.253)
Host is up (0.094s latency).
Nmap done: 256 IP addresses (64 hosts up) scanned in 2.35 seconds


$ arp -a
_gateway (192.168.100.1) at 00:09:0f:09:00:01 [ether] on wlo1
laptop-a0top0qd.ruktv.local (192.168.100.125) at 30:e3:7a:73:02:21 [ether] on wlo1
ruktvdc02.ruktv.local (192.168.100.12) at d4:85:64:d5:0a:24 [ether] on wlo1
ruktvdc01.ruktv.local (192.168.100.11) at d4:85:64:d5:1b:5c [ether] on wlo1
? (192.168.100.23) at 00:1b:a9:33:c0:2b [ether] on wlo1
? (192.168.100.29) at 30:cd:a7:63:07:68 [ether] on wlo1
? (192.168.100.225) at <incomplete> on wlo1
```


And then nmap -PR (arp ping mode) finds absolutely zero!
Why would that be?

---

### Post by TheFu on 2018-07-20
You are assuming the device uses IP. It may not.  The documentation would be clear about that.
There are all sorts of devices that don't use IP but have ethernet ports. 

Ethernet != IP.

---

### Post by kazakore on 2018-07-20
Fair comment, although I assumed anything that is designed for sending emails via SNMP falls under the IP protocol but maybe I'm remembering my limited network knowledge incorrectly....

But for the record it does.

[https://www.riello-ups.de/fileadmin/redaktion/PDF-Handbuecher/Riello-UPS_Handbuch_Netman_10x_Plus_en_.pdf](https://www.riello-ups.de/fileadmin/redaktion/PDF-Handbuecher/Riello-UPS_Handbuch_Netman_10x_Plus_en_.pdf)


Think I'm going to have to try and get TelNet working tomorrow...... (Although that will need a USB-Serial adapter and probably nothing to confirm that is even working with so likely to cause even more headaches.....)

---

### Post by TheFu on 2018-07-20
From the manual:
> User-configured parameters are stored in the Network Adapter &#769;s nonvolatile memory.
Configuration can be updated via RS-232 port via a terminal.

Further down:
> II.1.1 Adapter configuration
Adapter must be configured before it is used. Adapter contains own configuration
software and it can be configured locally only.

That means that before the networking will work, you have to use a serial connection to configure the it. Period.

All the 10base-tx and CAT3/UTP stuff means this is really, really,old-school equipment.  100base-tx was possible in 1998 pretty much everywhere, so this pre-dates that.

Telnet won't work before the networking settings are made.  If you can, you should disabled telnet.  Huge security risk if that connection is on a LAN that is routed.  Huge.

---

### Post by kazakore on 2018-07-20
> **TheFu said:**
> From the manual:

Further down:


That means that before the networking will work, you have to use a serial connection to configure the it. Period.

Unit has been installed since at least 2012 and has a network cable going to the main router so we had hoped this had previously been done (I've only been with the company a year.) My colleague spent most of yesterday (I wasn't it as we work alternate shifts) trying to get the serial communication to work to check these things and failed, so I thought I'd try and see if it had been configured and on what address by using tool available to me (and not having a serial port on any easily available machines here makes that in some ways easier, if it had worked.) I suspect that you're correct and it never had been configured though.

> Telnet won't work before the networking settings are made.  If you can, you should disabled telnet.  Huge security risk if that connection is on a LAN that is routed.  Huge.

My mistake, I didn't mean Telnet, was thinking that was the RS232 protocol for some reason.... (Probably since I haven't really touched it since WinXP days with HyperTerminal and that often used the Telnet logo on links.)

---

### Post by TheFu on 2018-07-20
There are USB-to-serial adapters ($10).   Be certain you get either a null-modem version or an adapter to convert from a normal serial connection to null-modem ($6).  The pins are different.

minicom is the Linux tool.   The serial device will probably look like sttyS0 or something like that in /dev/.  I have one here somewhere for router configuration.   Let's see what happens when I connect it.  It is on /dev/ttyUSB0.
```
crw-rw----   1 root dialout 188,   0 Jul 20 12:58 ttyUSB0

```
Hope that helps.  You probably want 38,400 8-N-1 settings for the serial to work.   Newer devices will talk much faster, 115200.

---

### Post by kazakore on 2018-07-20
> **TheFu said:**
> There are USB-to-serial adapters ($10).   Be certain you get either a null-modem version or an adapter to convert from a normal serial connection to null-modem ($6).  The pins are different.

minicom is the Linux tool.   The serial device will probably look like sttyS0 or something like that in /dev/.  I have one here somewhere for router configuration.   Let's see what happens when I connect it.  It is on /dev/ttyUSB0.
```
crw-rw----   1 root dialout 188,   0 Jul 20 12:58 ttyUSB0

```
Hope that helps.  You probably want 38,400 8-N-1 settings for the serial to work.   Newer devices will talk much faster, 115200.

Definitely be able to find a null modem around here, the USB-Serial more questionable. Going to see what we have at work tomorrow morning, going to take a rest from it the rest of this evening (can't be expected to stress yourself for a full 12 hour shift when working support ;) )

But I will say you're being a little optimistic for how old the comms board is! :p
> Set the serial link to 9600 baud, No parity, 8 data bits, 1 stop bit, no control flow.

Managed to find the ip address with zencat on a Win laptop here (couldn't be bothered to run a VM to split my wifi from ethernet.) Not sure what I did wrong before, maybe I didn't make sure the set IP and SubNet was within range. It's around where I was expecting to find it though. But I get nothing when trying to navigate to the IP address in a browser so seems the http interface is not enabled anyway so will still need setting up via the serial port....

---

