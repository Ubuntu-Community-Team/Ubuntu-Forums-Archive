---
title: "Internet Issue - no data through connections. Can ping and use local network ok."
date: 2005-11-23
forum: Networking &amp; Wireless
---

### Post by Rcomian on 2005-11-23
I'm having a little trouble setting up my network on a new installation of Ubuntu 5.10.

I didn't configure networking during install, but configured it afterwards. It it plugged straight into my firewall.

The weird thing is that I can ping the internet fine (by both name and IP). However I can't get any data down any pipes. So I can connect to google, but the browser just sits there waiting for data, never getting any.

I'm really not sure what's doing this. I have tried both DHCP & Static IP's, DHCP is my preferred, but neither work.

Bizarely, I can do pretty much anything I like on any other machine on my local network (there's quite a few, never seen a problem like this). In fact I can take the cable out of the machine having trouble, attach it to any other machine and it just works, no it's not a cabling or firewall issue.

As for debugging, I've placed the output of the troubleshooting below.

In anticipation of someone being able to help me - thanks :) 

[FONT="Courier New"]
pom@boots:~$ sudo mii-tool eth0
eth0: negotiated 100baseTx-FD, link ok
pom@boots:~$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:D0:59:4A:F6:7D
          inet addr:192.168.0.129  Bcast:192.168.255.255  Mask:255.255.0.0
          inet6 addr: fe80::2d0:59ff:fe4a:f67d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1320  Metric:1
          RX packets:193 errors:0 dropped:78 overruns:0 frame:53429
          TX packets:145 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:24392 (23.8 KiB)  TX bytes:16713 (16.3 KiB)

pom@boots:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eth0
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
pom@boots:~$ ping 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
64 bytes from 192.168.0.1: icmp_seq=1 ttl=30 time=0.411 ms
64 bytes from 192.168.0.1: icmp_seq=2 ttl=30 time=0.477 ms
64 bytes from 192.168.0.1: icmp_seq=3 ttl=30 time=0.433 ms
c64 bytes from 192.168.0.1: icmp_seq=4 ttl=30 time=0.471 ms

--- 192.168.0.1 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3000ms
rtt min/avg/max/mdev = 0.411/0.448/0.477/0.027 ms
pom@boots:~$ ping 209.98.65.1
PING 209.98.65.1 (209.98.65.1) 56(84) bytes of data.
From 209.98.65.1 icmp_seq=1 Packet filtered
From 209.98.65.1 icmp_seq=2 Packet filtered

--- 209.98.65.1 ping statistics ---
3 packets transmitted, 0 received, +2 errors, 100% packet loss, time 2001ms

pom@boots:~$ ping [www.mpr.org](www.mpr.org)
PING [www.mpr.org](www.mpr.org) (209.98.65.80) 56(84) bytes of data.

64 bytes from 1400inc.com (209.98.65.80): icmp_seq=1 ttl=109 time=120 ms
64 bytes from 1400inc.com (209.98.65.80): icmp_seq=2 ttl=109 time=120 ms
64 bytes from 1400inc.com (209.98.65.80): icmp_seq=3 ttl=109 time=119 ms
64 bytes from 1400inc.com (209.98.65.80): icmp_seq=4 ttl=109 time=119 ms
c64 bytes from 1400inc.com (209.98.65.80): icmp_seq=5 ttl=109 time=122 ms
64 bytes from 1400inc.com (209.98.65.80): icmp_seq=6 ttl=109 time=119 ms

--- [www.mpr.org](www.mpr.org) ping statistics ---
6 packets transmitted, 6 received, 0% packet loss, time 5004ms
rtt min/avg/max/mdev = 119.012/120.261/122.374/1.090 ms
pom@boots:~$ cat /etc/resolv.conf
nameserver 192.168.0.1
pom@boots:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

iface eth0 inet dhcp

auto eth0
pom@boots:~$ telnet [www.google.co.uk](www.google.co.uk) 80
Trying 66.102.9.104...
Connected to [www.l.google.com](www.l.google.com).
Escape character is '^]'.
GET /

Connection closed by foreign host.
pom@boots:~$
[/FONT]

---

### Post by darth_vector on 2005-11-23
hi,

does your firewall netmask match that of your inteface (255.255.0.0)? i dont think 192.168.0.0 is a protected ip network name.

thats all i can think of for the moment.

---

### Post by mlomker on 2005-11-23
Are you using firefox?  You probably need to [disable the ipv6 settings]("http://www.ubuntuguide.org/#loadwebsitefasterfirefox") under about:config

---

### Post by Rcomian on 2005-11-23
Thanks for your replies. Not found anything just yet.

darth_vector:
Yes, the netmask 255.255.0.0 does match the firewall (this was configured via DHCP) but even if I statically assign an IP and netmask of 255.255.255.0 it's the same deal.

192.168.0.0 is the class C network reserved for internal use (see [http://www.faqs.org/docs/linux_network/x-087-2-issues.ip-addresses.html)](http://www.faqs.org/docs/linux_network/x-087-2-issues.ip-addresses.html)).

mlomker:
It's not just a firefox issue, it even happens if I telnet or do any other kind of internet activity (ie, trying to download security updates). However I disabled IPV6 in about:config just to be sure - no dice tho :(

---

### Post by mlomker on 2005-11-23
[QUOTE=Rcomian]mlomker:
It's not just a firefox issue, it even happens if I telnet or do any other kind of internet activity (ie, trying to download security updates). However I disabled IPV6 in about:config just to be sure - no dice tho :([/QUOTE]

Well, the **ping** command confirms that the card works in general.  Perhaps TCP isn't passing for some reason but if that's the case then the first thing I'd look for is a firewall configuration problem.  If you have other machines on the local LAN then can you telnet/ssh/browse to the local machines?

---

### Post by Rcomian on 2005-11-24
[QUOTE=mlomker]Well, the **ping** command confirms that the card works in general.  Perhaps TCP isn't passing for some reason but if that's the case then the first thing I'd look for is a firewall configuration problem.  If you have other machines on the local LAN then can you telnet/ssh/browse to the local machines?[/QUOTE]

Yep, all local network access is absolutely fine. I've just ssh'd into the machine I'm posting from without a hitch. I'm behind a NAT router which plugs into my cable modem - but there's no port or any fancy filtering on it - just the NAT.

I've got about 5 machines on my local Lan, no problem accessing any of them either way. I can take cable from the machine that's got problems, plug it in to the machine I'm posting from now, and browse away quite happily - so I'd say it's not a problem external to the machine with problems.

Does Ubuntu come with any sort of packet filtering/firewall as standard that could be causing the issue?

---

### Post by mips on 2005-11-24
Does your other PC's use the same network and mask ?

Try this and see if it helps:
Open a terminal and enter:
**sudo gedit /etc/modprobe.d/aliases**

Look for the line that reads:
**alias net-pf-10 ipv6**

Change it to:
**alias net-pf-10 off #ipv6**

Save and reboot your PC.

---

### Post by mlomker on 2005-11-24
[QUOTE=Rcomian]Does Ubuntu come with any sort of packet filtering/firewall as standard that could be causing the issue?[/QUOTE]

No, you have to manually install Firestarter.

---

### Post by mlomker on 2005-11-24
[QUOTE=mips]Does your other PC's use the same network and mask ?
Change it to:
**alias net-pf-10 off #ipv6**
[/QUOTE]

Good idea.  I actually put a # in front of that entire line.

---

### Post by Rcomian on 2005-11-24
[QUOTE=mips]Does your other PC's use the same network and mask ?

Try this and see if it helps:
Open a terminal and enter:
**sudo gedit /etc/modprobe.d/aliases**

Look for the line that reads:
**alias net-pf-10 ipv6**

Change it to:
**alias net-pf-10 off #ipv6**

Save and reboot your PC.[/QUOTE]

That's the one, that's got it. I now have google in all its glory :)
Thank you very much all of you!

Out of interest - this can't be an uncommon problem, is it worth making this sticky?

Any idea what the actual issue was - is it just that my firewall thingy doesn't support IPV6 at all?

---

### Post by mlomker on 2005-11-24
[QUOTE=Rcomian]Out of interest - this can't be an uncommon problem, is it worth making this sticky?

Any idea what the actual issue was - is it just that my firewall thingy doesn't support IPV6 at all?[/QUOTE]

Yeah, your router was confused.  I've already added it to the troubleshooting sticky.

---

### Post by mips on 2005-11-24
It is not an uncommen problem. The weird thing is it only seemed to surface since Breezy....???

It is amazing how many networking problems are IPv6 related, it's like the flu ;)

---

### Post by agiledata on 2005-12-24
I have a similar problem, but all the above solutions haven't helped.

I'm new to Linux. Recently, I've started moving my PCs over to Ubuntu, and things have gone very well, apart from modems. I'm trying to set up two Ubuntu PCs for a friend, and a retired aunt. They don't have broadband, so I need to get a modem working. After two weeks, I eventually realised that WinModems were a bad idea, so I dug out my old US Robotics 56k Voice FaxModem.

Ubuntu detects the modem with no problem:
```
System --> Administration --> Networking --> Modem connection --> Properties --> Modem --> Autodetect
```
finding /dev/ttyS1.

On activating the modem, it dials and establishes a connection, which it holds.

Netstat gives me an IP address from the ISP I'm dialling. 
```
Applications --> System Tools --> Network Tools --> Netstat
```
Traceroute gives me two IP addresses, one local (0.33ms) and one remote (249ms), both of which I can ping.

But that's as far as I can get. I can't get web pages, or ping other addresses, by numbers or domain. I've tried explicitly setting the DNSs to server-provided, or to those of the ISP. I've tried every suggestion I can find on the newsgroups, and I'm a bit stuck. Without internet access from Linux, my aunt and friend will have to go back to Windows! What else can I try? I must be missing something obvious.

---

### Post by mlomker on 2005-12-26
[QUOTE=agiledata]What else can I try? I must be missing something obvious.[/QUOTE]

Is the route getting set when connected?  **route -n**

---

