---
title: "Redirecting traffic sent to a specific IP to a different IP"
date: 2015-04-09
forum: Networking &amp; Wireless
---

### Post by andre-o on 2015-04-09
Hello all, I'm trying to redirect port 80 traffic from a virtual machine running on a host box with Ubuntu 12.04 to a different IP.  Essentially, the host box is acting as the router in this situation, and is for all intents and purposes I'm trying to do exactly what was done in this thread:  [http://ubuntuforums.org/showthread.php?t=1786334](http://ubuntuforums.org/showthread.php?t=1786334)

I've followed this guide [http://www.debuntu.org/how-to-redirecting-network-traffic-to-a-new-ip-using-iptables/](http://www.debuntu.org/how-to-redirecting-network-traffic-to-a-new-ip-using-iptables/), which is exactly what is given in the aforementioned thread, however I'm able to see via tcpdump that my packets are still being sent to the original IP, rather than the IP I've specified that it be redirected to.

Here is my nat table:
```
~# iptables -t nat -L
Chain PREROUTING (policy ACCEPT)
target     prot opt source               destination         
DNAT       tcp  --  anywhere             69.28.95.246         tcp dpt:http to:104.219.53.230:80


Chain INPUT (policy ACCEPT)
target     prot opt source               destination         


Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         


Chain POSTROUTING (policy ACCEPT)
target     prot opt source               destination         
MASQUERADE  all  --  anywhere             anywhere
```

also:
```
~# sysctl net.ipv4.ip_forward
net.ipv4.ip_forward = 1
```

You can see, I'm trying to redirect connections going to port 80 on 69.28.95.246 to port 80 on 104.219.53.230...everything I've read tells me that I've set this up correctly, yet tcpdump shows me that this is not the case.  Wanted to bounce this off you guys to see if anyone had any ideas.

---

### Post by andre-o on 2015-04-09
Hmmm, I [believe I] have added iptables logging to the situation, and the packets seemingly do not even hit the 'nat' table -- that is unless I've setup logging incorrectly.

1) Should I receive at least something within syslog with the given logging rules shown below?
```
~# iptables -t nat -L LOGGING
Chain LOGGING (0 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere             limit: avg 10/min burst 5 LOG level debug prefix "NAT:"
```

2) Is there any reason why the packets might not necessarily hit the 'nat' table?  I.e., could something with the 'filter' table preclude the packet hitting the 'nat' table?



EDIT:  Figured out what I had wrong with the logging, though it still seems that the nat table isn't being hit by the packets from my vm.  At least the logging allows me to confirm that, now to determine why that's the case.  Perhaps something with UFW.  I think I'm at least pointed in the right direction now.

---

### Post by Doug S on 2015-04-09
Hi and welcome to Ubuntu forums,

Sorry, but I need to see your logging rule in the context of your overall rules set. I would also like to observe the packet counters, as I find them very useful in helping to figure out the packet flow through the tables. Could you post the output for these two commands:```
sudo iptables -v -x -n -L
sudo iptables -t nat -v -x -n -L
```And yes with tcpdump you will still observe packets flowing to the original IP address, but you should also observe them being re-transmitted to the new IP address.

Edit: I hadn't seen your edit when I replied.

Edit 2: I set this scenario up on my LAN and it worked as expected.
I had 192.168.111.140 forward to 192.168.111.1 and then used 192.168.111.101 to try to access the web pages on 192.168.111.140. Observe the packets being re-transmitted in both directions:```
2015-04-09 14:19:51.230972 IP 192.168.111.101.62101 > 192.168.111.140.80: Flags [S], seq 380327346, win 8192, options [mss 1460,nop,wscale 8,nop,nop,sackOK], length 0
2015-04-09 14:19:51.231710 IP 192.168.111.140.62101 > 192.168.111.1.80: Flags [S], seq 380327346, win 8192, options [mss 1460,nop,wscale 8,nop,nop,sackOK], length 0
2015-04-09 14:19:51.231947 IP 192.168.111.1.80 > 192.168.111.140.62101: Flags [S.], seq 650578643, ack 380327347, win 14600, options [mss 1460,nop,nop,sackOK,nop,wscale 6], length 0
2015-04-09 14:19:51.232171 IP 192.168.111.140.80 > 192.168.111.101.62101: Flags [S.], seq 650578643, ack 380327347, win 14600, options [mss 1460,nop,nop,sackOK,nop,wscale 6], length 0
2015-04-09 14:19:51.232653 IP 192.168.111.101.62101 > 192.168.111.140.80: Flags [.], ack 1, win 256, length 0
2015-04-09 14:19:51.232814 IP 192.168.111.140.62101 > 192.168.111.1.80: Flags [.], ack 1, win 256, length 0
2015-04-09 14:19:51.234947 IP 192.168.111.101.62101 > 192.168.111.140.80: Flags [P.], seq 1:339, ack 1, win 256, length 338
2015-04-09 14:19:51.235103 IP 192.168.111.140.62101 > 192.168.111.1.80: Flags [P.], seq 1:339, ack 1, win 256, length 338
2015-04-09 14:19:51.235371 IP 192.168.111.1.80 > 192.168.111.140.62101: Flags [.], ack 339, win 245, length 0
2015-04-09 14:19:51.235525 IP 192.168.111.140.80 > 192.168.111.101.62101: Flags [.], ack 339, win 245, length 0
```Edit 3: This is what I did for a rule set:```
#!/bin/sh
FWVER=0.01
#
# test redirection rule set 2015.04.09 Ver:0.01
#     see also: http://ubuntuforums.org/showthread.php?t=2272938
#
#     run as sudo
#

echo "Loading test rule set version $FWVER..\n"

# The location of the iptables program
#
IPTABLES=/sbin/iptables

#Setting the EXTERNAL and INTERNAL interfaces and addresses for the network
#
EXTIF="eth0"
EXTIP="192.168.111.140"
NEWIP="192.168.111.1"
UNIVERSE="0.0.0.0/0"

#CRITICAL:  Enable IP forwarding since it is disabled by default
#
#echo Enabling forwarding...
echo "1" > /proc/sys/net/ipv4/ip_forward

#Clearing any previous configuration
#
echo "  Clearing any existing rules and setting default policy to ACCEPT.."
$IPTABLES -P INPUT ACCEPT
$IPTABLES -F INPUT
$IPTABLES -P OUTPUT ACCEPT
$IPTABLES -F OUTPUT
$IPTABLES -P FORWARD ACCEPT
$IPTABLES -F FORWARD
$IPTABLES -t nat -F
# Delete user defined chains
$IPTABLES -X
# Reset all IPTABLES counters
$IPTABLES -Z
# While my references do not have it, I think this is needed.
$IPTABLES -t nat -Z

$IPTABLES -t nat -A PREROUTING -p tcp -i $EXTIF --dport 80 -j DNAT --to-destination $NEWIP:80

#
# FORWARD rules would only be if the default policy is not ACCEPT
#

#$IPTABLES -t nat -A POSTROUTING -o $EXTIF -j SNAT --to $EXTIP
$IPTABLES -t nat -A POSTROUTING -j SNAT --to $EXTIP

echo Test rule set version $FWVER done.
```

---

### Post by andre-o on 2015-04-10
So awesome, thank you for your response Doug.  This should certainly help me narrow the issue down a bit.  I'm certain the issue lies within my current ufw/iptables rules, as I've not flushed those (I have other vm's running on this machine that I did not want to disrupt).  I'll certainly post here what the resolution is/was if/when I figure this out.  Thanks again!

---

### Post by andre-o on 2015-04-13
Haven't been able to get this working so far, even with UFW disabled and all iptables chains flushed.

```
~# iptables -t nat -nvL
Chain PREROUTING (policy ACCEPT 38 packets, 3287 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 DNAT       tcp  --  *      *       0.0.0.0/0            69.28.95.246         tcp dpt:80 to:104.219.53.230:80


Chain INPUT (policy ACCEPT 8 packets, 729 bytes)
 pkts bytes target     prot opt in     out     source               destination         


Chain OUTPUT (policy ACCEPT 1 packets, 71 bytes)
 pkts bytes target     prot opt in     out     source               destination         


Chain POSTROUTING (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
   37  2751 SNAT       all  --  *      *       0.0.0.0/0            0.0.0.0/0            to:69.28.95.246
~# iptables -nvL
Chain INPUT (policy ACCEPT 12050 packets, 2609K bytes)
 pkts bytes target     prot opt in     out     source               destination         


Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         


Chain OUTPUT (policy ACCEPT 6650 packets, 982K bytes)
 pkts bytes target     prot opt in     out     source               destination
```


I thought that maybe this is because the traffic is being produced by a local process, and thus needs to use the "OUTPUT" chain in the 'nat' table, however, that didn't seem to make a difference.  In the examples above, I used ```
iptables -t nat -A PREROUTING -p tcp -d 69.28.95.246 --dport 80 -j DNAT --to-destination 104.219.53.230:80
``` to specify traffic going to a specific IP, vs. all traffic coming from a specific interface, as in the example given by Doug S.  I did, however, try the interface method as well, to no avail :(  I'm at a loss for why this could be, unless of course I'm just not understanding exactly how traffic is being moved from vm to the net on this host.

---

### Post by Doug S on 2015-04-13
> **andre-o said:**
>   I'm at a loss for why this could be, unless of course I'm just not understanding exactly how traffic is being moved from vm to the net on this host.That seems possible, even likely. After a fresh boot, and with your VM running, but before making any changes to your iptables rules set, post the results from the two commands I initially posted. i.e. we want to see what your iptables rule set starts as, before you make any changes. Also post the output from```
ifconfig
```

Oh, by the way, I just tend to use SNAT instead if MASQUERADE, but either should work. The other day I did go back and also tested "MASQUERADE", I just forgot to come back here and edit my reply to say so.

---

### Post by andre-o on 2015-04-14
Thanks so much Doug S.  I did try the "MASQUERADE" rule as well after reading your post, though, to no avail.

At this time, I've rebooted, started up the vm, and here is the output from the requested commands:
```
~# iptables -nvxL
Chain INPUT (policy ACCEPT 1579 packets, 271928 bytes)
    pkts      bytes target     prot opt in     out     source               destination         


Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         


Chain OUTPUT (policy ACCEPT 1244 packets, 146596 bytes)
    pkts      bytes target     prot opt in     out     source               destination


~# iptables -t nat -nvxL
Chain PREROUTING (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         


Chain INPUT (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         


Chain OUTPUT (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         


Chain POSTROUTING (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination
```

Note: This host is running in an environment where it has both interfaces for both internal traffic and external traffic (hence, you'll see VLAN tagging, an Infiniband interface, and other network awesomeness employed).  I've also obfuscated the public IP, for obvious reasons ;)  Traffic from the VM is on the "32635-1627" interface, which aliases to "br0" which in turn aliases to "bond0".

```
~# ifconfig
32635-1627 Link encap:Ethernet  HWaddr fe:00:d1:1a:30:90  
          inet6 addr: fe80::fc00:d1ff:fe1a:3090/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11 errors:0 dropped:0 overruns:0 frame:0
          TX packets:708 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:812 (812.0 B)  TX bytes:50778 (50.7 KB)


32635-1627-P Link encap:Ethernet  HWaddr fe:00:0a:1a:30:90  
          inet6 addr: fe80::fc00:aff:fe1a:3090/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:256 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:0 (0.0 B)  TX bytes:18649 (18.6 KB)


bond0     Link encap:Ethernet  HWaddr 00:30:48:f7:21:a9  
          inet6 addr: fe80::230:48ff:fef7:21a9/64 Scope:Link
          UP BROADCAST RUNNING MASTER MULTICAST  MTU:1500  Metric:1
          RX packets:22458 errors:0 dropped:3961 overruns:0 frame:0
          TX packets:1640 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:11902166 (11.9 MB)  TX bytes:212307 (212.3 KB)


bond0.228 Link encap:Ethernet  HWaddr 00:30:48:f7:21:a9  
          inet6 addr: fe80::230:48ff:fef7:21a9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:129 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6450 (6.4 KB)  TX bytes:1296 (1.2 KB)


bond0.229 Link encap:Ethernet  HWaddr 00:30:48:f7:21:a9  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2769 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1605 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:209313 (209.3 KB)  TX bytes:209517 (209.5 KB)


br0       Link encap:Ethernet  HWaddr 00:30:48:f7:21:a9  
          inet addr:###.###.###.###  Bcast:209.26.51.255  Mask:255.255.252.0
          inet6 addr: fe80::230:48ff:fef7:21a9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2604 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1594 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:194428 (194.4 KB)  TX bytes:208705 (208.7 KB)


br1       Link encap:Ethernet  HWaddr 00:30:48:f7:21:a9  
          inet6 addr: fe80::230:48ff:fef7:21a9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:129 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6450 (6.4 KB)  TX bytes:648 (648.0 B)


eth0      Link encap:Ethernet  HWaddr 00:30:48:f7:21:a9  
          UP BROADCAST RUNNING SLAVE MULTICAST  MTU:1500  Metric:1
          RX packets:3961 errors:0 dropped:3961 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:508504 (508.5 KB)  TX bytes:0 (0.0 B)
          Memory:c0000000-c0020000 


eth1      Link encap:Ethernet  HWaddr 00:30:48:f7:21:a9  
          UP BROADCAST RUNNING SLAVE MULTICAST  MTU:1500  Metric:1
          RX packets:18497 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1640 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11393662 (11.3 MB)  TX bytes:212307 (212.3 KB)
          Memory:c0040000-c0060000

ib0       Link encap:UNSPEC  HWaddr 80-00-00-48-FE-80-00-00-00-00-00-00-00-00-00-00  
          inet addr:192.168.1.6  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::230:48ff:fff4:e1c9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:65520  Metric:1
          RX packets:45 errors:0 dropped:0 overruns:0 frame:0
          TX packets:56 errors:0 dropped:7 overruns:0 carrier:0
          collisions:0 txqueuelen:256 
          RX bytes:4448 (4.4 KB)  TX bytes:5600 (5.6 KB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:153 errors:0 dropped:0 overruns:0 frame:0
          TX packets:153 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:13709 (13.7 KB)  TX bytes:13709 (13.7 KB)


managementbr0 Link encap:Ethernet  HWaddr 00:30:48:f7:21:a9  
          inet addr:10.10.227.166  Bcast:10.10.227.255  Mask:255.255.252.0
          inet6 addr: fe80::230:48ff:fef7:21a9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6436 errors:0 dropped:4 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:679733 (679.7 KB)  TX bytes:648 (648.0 B)


```

Just for clarity, when I insert the rules mentioned by you and the article I linked before, I do see traffic leaving the vm, but going directly to IP I telnet to (EXTIP in your script), instead of going to the IP given in the DNAT rule.

---

### Post by Doug S on 2015-04-14
Well, your setup is different than anything I have ever seen before. I also do not see 69.28.95.246 anywhere on any interface.
Oh, ... Is 69.28.95.246 nothing to do with you? Are you just trying to re-direct traffic originally destined for somewhere else on the internet, but that must flow through your host to get there? If yes, I'll have to think about it. I had assumed 69.28.95.246 was your host.

> **andre-o said:**
> Just for clarity, when I insert the rules mentioned by you and the article I linked before, I do see traffic leaving the vm, but going directly to IP I telnet to (EXTIP in your script), instead of going to the IP given in the DNAT rule.Yes, that is correct and what we expect. If it were working properly, the redirection would occur later.

---

### Post by andre-o on 2015-04-14
Yes, the vm's IP is 209.26.48.144 (and is for the most part transparent to the host system -- there isn't an IP set on the vm's interface as seen by the host, as you've alluded to).  From that vm, trying to reach (i.e., be redirected to) 104.219.53.230:80 when initializing connections to 69.28.95.246:80.  Sorry for the confusion.  I'd imagine this has something to do with our elaborate networking configured on the host system.  Thanks for taking the time to drill down through all this mess with me, it's very much appreciated.

---

### Post by Doug S on 2015-04-14
I'm stumped. It is not clear to me how packets from your VM are traversing through your host, but it seems to be via some method I am not familiar with. I'm hoping someone else will chime in and help.

---

### Post by andre-o on 2015-04-15
Yeah, I'm thinking this is through the libvirt library.  I've left out some important info -- the vm is provisioned via qemu/kvm+libvirt.  Thanks in any case, Doug S.  You've helped me rule out some stupidity on my part in my understandings of the iptables rules I was trying to mimic, heh.  Thankful for that :)

---

### Post by Doug S on 2015-04-15
> **andre-o said:**
> I've left out some important info -- the vm is provisioned via qemu/kvm+libvirt. Well, qemu/kvm+livirt is all I ever use for VM's, and I can follow any network packets to/from the VM with the host iptables (not that I have actually had to that often).

---

