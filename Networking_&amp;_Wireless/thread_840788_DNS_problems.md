---
title: "DNS problems"
date: 2008-06-25
forum: Networking &amp; Wireless
---

### Post by rothbert on 2008-06-25
I have a problem with internet connectivity. I am a complete newbie :-) there is another person in the house who has had a crack at this and posted a thread with no joy ([http://ubuntuforums.org/showthread.php?t=839166](http://ubuntuforums.org/showthread.php?t=839166)) I need a patient person to give me a simple step by step approach to tackling this. I can use terminal and have a basic understanding of how things work, but not much idea of how the networking set up really works.  

I noticed the issue a day or so ago, the machine had been running for several days and Firefox open and running fine during that time. Then out of the blue, no other applications could access the net. There were some updates during that period but apart from that I can't see what might have triggered this. No new software installed that I can think of. After a reboot, Firefox could no longer connect normally. 

It is an AMD64x2 box running ubuntu 8.04. Its networked (wired D-Link router which has been rebooted) with this laptop on XP and another box running Xbuntu. The other machines have no connectivity issues.

I can ping the other machines no problem, I can ping by IP but not by name. Firefox konqueror or wget will connect to sites using  IP address (depending on the site - at least google) but not by name. We can resolve an address with nslookup or dig, ipv4 or ipv6

We have changed the DNS server settings in Network manager (using applet) to the openDNS servers  208.67.222.222
208.67.220.220, to no effect.

From what I've read on similar problems, here's some hopefully relevant info:

```
$ ifconfig 

eth0      Link encap:Ethernet  HWaddr 00:1d:7d:93:32:e9  
          inet addr:10.1.1.4  Bcast:10.255.255.255  Mask:255.0.0.0 
          inet6 addr: fe80::21d:7dff:fe93:32e9/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:894 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:5582 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:119501 (116.7 KB)  TX bytes:539627 (526.9 KB) 
          Interrupt:23 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:1605 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:1605 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:112121 (109.4 KB)  TX bytes:112121 (109.4 KB) 


```

```
$ cat /etc/network/interfaces 

# This file describes the network interfaces available on your system 
# and how to activate them. For more information, see interfaces(5). 

# The loopback network interface 
auto lo 
iface lo inet loopback 

# The primary network interface 
auto eth0 
#iface eth0 inet dhcp 

iface eth0 inet static 
address 10.1.1.4 
netmask 255.0.0.0 
gateway 10.1.1.1 
```

```
$ route -n 

Kernel IP routing table 
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface 
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0 
10.0.0.0        0.0.0.0         255.0.0.0       U     0      0        0 eth0 
0.0.0.0         10.1.1.1        0.0.0.0         UG    100    0        0 eth0 
```

```
$ cat /etc/resolv.conf 
nameserver 208.67.222.222 
nameserver 208.67.220.220 
nameserver 10.1.1.1 
```

```
$ sudo iptables -L -vnx 
[sudo] password for rob: 
Chain INPUT (policy DROP 0 packets, 0 bytes) 
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 ACCEPT     tcp  --  *      *       208.67.222.222       0.0.0.0/0           tcp flags:!0x17/0x02 
     109     7703 ACCEPT     udp  --  *      *       208.67.222.222       0.0.0.0/0           
       0        0 ACCEPT     tcp  --  *      *       208.67.220.220       0.0.0.0/0           tcp flags:!0x17/0x02 
       0        0 ACCEPT     udp  --  *      *       208.67.220.220       0.0.0.0/0           
      25     2220 ACCEPT     tcp  --  *      *       10.1.1.1             0.0.0.0/0           tcp flags:!0x17/0x02 
       0        0 ACCEPT     udp  --  *      *       10.1.1.1             0.0.0.0/0           
    1605   112121 ACCEPT     all  --  lo     *       0.0.0.0/0            0.0.0.0/0           
       0        0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 10/sec burst 5 
       0        0 DROP       all  --  eth0   *       0.0.0.0/0            255.255.255.255     
    5845   499482 DROP       all  --  *      *       0.0.0.0/0            10.255.255.255      
       0        0 DROP       all  --  *      *       224.0.0.0/8          0.0.0.0/0           
       0        0 DROP       all  --  *      *       0.0.0.0/0            224.0.0.0/8         
       0        0 DROP       all  --  *      *       255.255.255.255      0.0.0.0/0           
       0        0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0             
       0        0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           state INVALID 
       0        0 LSI        all  -f  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 10/min burst 5 
      42    32182 INBOUND    all  --  eth0   *       0.0.0.0/0            0.0.0.0/0           
       0        0 LOG_FILTER  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
       0        0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Unknown Input' 

Chain FORWARD (policy DROP 0 packets, 0 bytes) 
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 10/sec burst 5 
       0        0 LOG_FILTER  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
       0        0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Unknown Forward' 

Chain OUTPUT (policy DROP 1 packets, 140 bytes) 
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 ACCEPT     tcp  --  *      *       10.1.1.4             208.67.222.222      tcp dpt:53 
     109     7217 ACCEPT     udp  --  *      *       10.1.1.4             208.67.222.222      udp dpt:53 
       0        0 ACCEPT     tcp  --  *      *       10.1.1.4             208.67.220.220      tcp dpt:53 
       0        0 ACCEPT     udp  --  *      *       10.1.1.4             208.67.220.220      udp dpt:53 
       0        0 ACCEPT     tcp  --  *      *       10.1.1.4             10.1.1.1            tcp dpt:53 
       0        0 ACCEPT     udp  --  *      *       10.1.1.4             10.1.1.1            udp dpt:53 
    1605   112121 ACCEPT     all  --  *      lo      0.0.0.0/0            0.0.0.0/0           
       0        0 DROP       all  --  *      *       224.0.0.0/8          0.0.0.0/0           
      35     3209 DROP       all  --  *      *       0.0.0.0/0            224.0.0.0/8         
       0        0 DROP       all  --  *      *       255.255.255.255      0.0.0.0/0           
       0        0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0             
       0        0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           state INVALID 
    5492   455646 OUTBOUND   all  --  *      eth0    0.0.0.0/0            0.0.0.0/0           
       0        0 LOG_FILTER  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
       0        0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Unknown Output' 

Chain INBOUND (1 references) 
    pkts      bytes target     prot opt in     out     source               destination         
      42    32182 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
       0        0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
       0        0 ACCEPT     all  --  *      *       10.1.1.2             0.0.0.0/0           
       0        0 ACCEPT     all  --  *      *       10.1.1.4             0.0.0.0/0           
       0        0 LSI        all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain LOG_FILTER (5 references) 
    pkts      bytes target     prot opt in     out     source               destination         

Chain LSI (2 references) 
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 LOG_FILTER  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
       0        0 LOG        tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x02 limit: avg 1/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
       0        0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x02 
       0        0 LOG        tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x04 limit: avg 1/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
       0        0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x04 
       0        0 LOG        icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 8 limit: avg 1/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
       0        0 DROP       icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 8 
       0        0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 5/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
       0        0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain LSO (0 references) 
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 LOG_FILTER  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
       0        0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 5/sec burst 5 LOG flags 0 level 6 prefix `Outbound ' 
       0        0 REJECT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           reject-with icmp-port-unreachable 

Chain OUTBOUND (1 references) 
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           
      65     7184 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
       0        0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
    5427   448462 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0 
```

Would really appreciate some help with this. Pretty much stuck in the mud here :-)

---

### Post by dmizer on 2008-06-25
have you tried rebooting the router?  sounds basic, but it could fix this problem.

---

### Post by rothbert on 2008-06-25
> **dmizer said:**
> have you tried rebooting the router?  sounds basic, but it could fix this problem.

Hi and thanks for the quick reply.
Yep, I've tried rebooting the router, no joy.

---

### Post by dmizer on 2008-06-25
only other thing i can suggest trying would be to disable ipv6.

just add
```
blacklist ipv6
```
to /etc/modprobe.d/blacklist

reboot and test.  if you are able to browse after that, then you may have a problem with how your router handles ipv6 addressing.  if this does not fix the problem, just remove the "blacklist ipv6" line from /etc/modprobe.d/blacklist and reboot.

---

### Post by rothbert on 2008-06-25
> only other thing i can suggest trying would be to disable ipv6.

OK, did that - no change :-(

---

### Post by dmizer on 2008-06-25
do you have a spare router? is there a firmware update available for your router?  are you running third party firmware?

---

### Post by wdaniels on 2008-06-26
Check also this file:

```
cat /etc/nsswitch.conf
```

I'm not exactly a networking expert, but iptables seems to show packets being exchanged via udp in both directions with the OpenDNS server 208.67.222.222 on port 53, which is precisely as expected, so I guess the problem must lie somewhere after the reply is received.

What exactly do you get if you do:

```
nslookup ubuntu.com
```

---

### Post by rothbert on 2008-06-26
Think I may have another router will have a look shortly and give a whirl. Seem to be locked out of the current router at the moment. Will need to check password with the other user when he arrives.

Other info -
 
```
$ cat /etc/nsswitch.conf 
# /etc/nsswitch.conf 
# 
# Example configuration of GNU Name Service Switch functionality. 
# If you have the `glibc-doc-reference' and `info' packages installed, try: 
# `info libc "Name Service Switch"' for information about this file. 

passwd:         compat 
group:          compat 
shadow:         compat 

hosts:          files mdns4_minimal wins [NOTFOUND=return] dns mdns4 
networks:       files 

protocols:      db files 
services:       db files 
ethers:         db files 
rpc:            db files 

netgroup:       nis 
```


```
~$ nslookup ubuntu.com 
Server:		208.67.222.222 
Address:	208.67.222.222#53 

Non-authoritative answer: 
Name:	ubuntu.com 
Address: 91.189.94.249 
```

thanks for your help on this :-)

---

### Post by wdaniels on 2008-06-26
> **rothbert said:**
> We can resolve an address with nslookup or dig, ipv4 or ipv6

OK, I missed that bit on first reading :D  So, DNS is not the problem.

Just as an experiment, try moving dns higher up the order in nsswitch.conf:

```
hosts:          files dns mdns4_minimal wins [NOTFOUND=return] mdns4
```

---

### Post by dmizer on 2008-06-26
> **wdaniels said:**
> OK, I missed that bit on first reading :D  So, DNS is not the problem.

Just as an experiment, try moving dns higher up the order in nsswitch.conf:

```
hosts:          files dns mdns4_minimal wins [NOTFOUND=return] mdns4
```

if you do this, then you will break local name resolution.  i assume you have winbind installed?

this really looks like a router problem.

---

### Post by wdaniels on 2008-06-26
> **dmizer said:**
> if you do this, then you will break local name resolution.  i assume you have winbind installed?

That's why I said "just as an experiment". It will also tell you if there is something broken with mdns/wins causing one of them to return not found or similar problem.

> **dmizer said:**
> this really looks like a router problem.

I don't know why you would think that, if there are other machines working fine off the same router...but that's just my opinion.

---

### Post by rothbert on 2008-06-26
> Just as an experiment, try moving dns higher up the order in nsswitch.conf:

Code:
hosts:          files dns mdns4_minimal wins [NOTFOUND=return] mdns4

I've done this and functionality has returned to everything I've tested so far. This is looking good - is there more to do here?

yes -winbind is installed

---

### Post by wdaniels on 2008-06-26
> **rothbert said:**
> is there more to do here?

Yes, put it back then find the actual problem :D

Actually, first let's see which one breaks it - mdns or wins?

Try taking wins out completely:

```
hosts: files mdns4_minimal [NOTFOUND=return] dns mdns4
```

Also, check to see if this file exists:

```
cat /etc/mdns.allow
```

Normally it doesn't, but if it did, potentially it could have something in there telling mdns that it has authority for domains other than .local which might cause this behaviour.

---

### Post by rothbert on 2008-06-26
OK, /etc/mdns.allow doesn't exist.

I took wins out and put dns back to original spot and all was functioning.

The other user (now here) has noticed that both this box and the XP box thought they were the master browser on the network (apparently this has happened before) and he has stopped the XP box trying to be the master browser. 

We then put wins back in to nsswitch.conf (so original configuration) and things seem to be working again. Looks like that may have been the issue. 
But unclear as to how that caused this problem and why at this time.

---

### Post by dmizer on 2008-06-26
> **wdaniels said:**
> I don't know why you would think that, if there are other machines working fine off the same router...but that's just my opinion.

just for the record, lots and lots of past experience tells me that even though other computers are working fine, the problem is still often the router.  here's a very recent case in point: [http://ubuntuforums.org/showpost.php?p=5188719&postcount=39](http://ubuntuforums.org/showpost.php?p=5188719&postcount=39)

looks like you're well on your way to solving this though.

---

### Post by rothbert on 2008-06-26
Still have a few network issues to sort, but things seem to be checking out OK. Thanks to you both for your time on this. Some pointers to get us thinking and looking in the right places was exactly what was needed.
Cheers :-)

---

### Post by ColJep on 2008-06-26
I seem to be struggling with a very similar problem. I used to use a Vigor2600G Router with Telefinica in Spain. I have a mixed Win / Linux network and used to have no problems.

I recently upgraded from a 3Mb connection to a 10Mb connection. Telefonica supplied a new router (Amper X7868r) and as soon as I connected it at the 3Mb speed web surfing on Linux became unbearable because DNS lookups took forever. Windows was slower than before but just usable.
Re installing the Vigor (not Telefonica supplied) and using the new DNS servers restored full speed.
I then found out that the Vigor only works up to 8Mb/s so as soon as my 10 Mb connection was made all web use had to be done with the Amper. Hence frustration. The Amper tends to stop it's wireless as soon as it gets hot so I do not trust it anyway.

Turning off all Win machines does not improve things. So I am looking for an alternate router. Any suggestions?

Colin

---

### Post by rothbert on 2008-06-26
Update: with this configuration - 
```
hosts:          files mdns4_minimal wins [NOTFOUND=return] dns mdns4 
```
We have internet functioning only now.

reverting to this -

```
hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4 
```
everything seems to work normally again.

Is leaving 'wins' out going to cause problems?

---

### Post by wdaniels on 2008-06-26
I can see that broken WINS might cause the browsing functions to screw up, but what you're reporting suggests the reverse if anything and I'm not sure how having two machines thinking they're the LMB would cause any interference to WINS functions. Unless WINS managed to break all by itself and then simply forcing a new browser election from the XP box happened to correct some bad cached info somewhere or kick something into life to fix it...?

I'm afraid I don't know enough about Samba or Windows networking in general to come up with a proper theory about this, but I'm glad that your problem is resolved for now :D

---

### Post by wdaniels on 2008-06-26
Sorry, just missed your post when I replied.

> **rothbert said:**
> Is leaving 'wins' out going to cause problems?

It will mean that the Ubuntu box can't resolve NETBIOS names, that's all. So you would not be able to connect to the XP machine by name, for example.

But I'm getting a little confused. Are you saying that WINS broke the whole name resolution process again on the Ubuntu box?

---

### Post by rothbert on 2008-06-26
I'm mystified as well, I thought we had everything functioning normally after tweaking the Xp box, but a while later i tried an update on the Ubuntu machine to find that only browsers were working.

Removing WINS seems to have brought everything else back.

---

