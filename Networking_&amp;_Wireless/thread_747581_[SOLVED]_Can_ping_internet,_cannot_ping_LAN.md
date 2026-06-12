---
title: "[SOLVED] Can ping internet, cannot ping LAN"
date: 2008-04-06
forum: Networking &amp; Wireless
---

### Post by jrssystemsnet on 2008-04-06
I am at a complete loss as to what happened here.  As of last night when I went to bed, everything was working fine.  When I got up this morning, I found that my router was the only device on my local network that I could reach - although, bizarrely, anything ELSE on my local network can ping ME fine.

In addition, I can get to the internet fine - the affected computer is the one I am posting this message from.

Here is my routing table:

```
g# route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.100.0   *               255.255.255.0   U     0      0        0 eth2
default         192.168.100.1   0.0.0.0         UG    0      0        0 eth2
```

I do not have a firewall running:

```
# iptables --list
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination   
```

Here you can see that my machine thinks addresses on my local lan are "unreachable" by route:

```
# traceroute 192.168.100.10
traceroute to 192.168.100.10 (192.168.100.10), 30 hops max, 40 byte packets
 1  banshee.local (192.168.100.50)  3006.054 ms !H  3006.051 ms !H  3006.040 ms !H
```

But bizarrely, the machine at 192.168.100.10 can ping THIS machine (192.168.100.50) just fine, or access any services on it, and this machine can access the router (192.168.100.1) just fine, including getting out to the internet!

I've tried replacing the switch the machines are plugged into (D-Link 8-port gigabit with the 4-port gigabit built into my router), power cycled both switches, replaced the network card in the affected machine, all to no avail.  I'm at my wits' end here.  Help?! =)

---

### Post by mrsteveman1 on 2008-04-06
Thats a confusing one for sure. I'm sure the switch is fine, they just keep records of what source port certain MAC addresses were seen, so im sure those tables are fine if youve been sending packets.

I'm also assuming theres no duplicate mac addresses or malicious traffic (spoofing etc).

What's in the ARP table on the machines in question?

You might want to run wireshark on one of these machines while you are pinging so you can see what layers of the IP stack are responding, and any error messages. Also check the kernel dmesg log for anything weird.

You might also want to check the ethernet nic for frame errors with ethtool.

---

### Post by jrssystemsnet on 2008-04-06
```
# arp
Address                  HWtype  HWaddress           Flags Mask            Iface
192.168.100.1            ether   00:11:95:CC:D1:29   C                     eth2
```

192.168.100.10 has a (valid) entry for this machine in its arp table, unsurprisingly (since it communicates successfully with this machine).

No, no malicious traffic on the LAN.  Other machines on the LAN can see each other just fine - and, for that matter, see this machine just fine (and it RESPONDS to them fine).  The problem is apparently that it's refusing to do a MAC lookup for local IPs?  I'm a little shaky on the technicalities of local subnet IP workings, because they generally "just work", but it's pretty obvious that if this box is addressed by its MAC address it responds fine, just for some reason it can't resolve a local IP to a MAC.

I am completely clueless about wireshark, but I'm installing it now.  If there's something in particular you want me to do with it, please be explicit.  (FWIW, I'm a FreeBSD professional of about six years' standing; but I'm fairly new to Ubuntu.)

---

### Post by jrssystemsnet on 2008-04-06
I am an idiot.  I had manually reconfigured the IP address to a static on 192.168.100.10 and I had fixed the entry in /etc/network/interfaces, but I had *****NOT***** killed off the dhclient process that had already been fired up the first time I booted that machine.

There was never anything wrong with 192.168.100.50 in the first place.  Sorry for the false alarm.  ::facepalm::

---

### Post by mrsteveman1 on 2008-04-06
:D thats a classic haha

---

### Post by jrssystemsnet on 2008-04-07
You know, in retrospect a lot of my confusion on this one stemmed from Ubuntu's response to an attempt to ping a local IP address which does not arp - "Destination Host Unreachable".  Or in the case of an attempt to ssh to a local IP which does not arp, "no route to host".  What's up with that?  There's nothing wrong with the *route*, there's just no host there!

FreeBSD's response in a situation like this - "ping: sendto: Host is down" seems to make far more sense.  Is there something I'm not seeing here?

---

