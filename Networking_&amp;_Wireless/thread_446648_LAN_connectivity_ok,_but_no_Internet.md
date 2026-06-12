---
title: "LAN connectivity ok, but no Internet"
date: 2007-05-17
forum: Networking &amp; Wireless
---

### Post by brawny on 2007-05-17
Hi All,

I'm a bit of a n00b here, and have just installed Ubuntu for the first time.  I'm running Feisty, with Samba working to a second WinXP pc on my home LAN.  LAN consists of a DLink DI-624 router and the two pcs.

While at work the other day, my wife mentioned that the Ubuntu pc went down - black screen, blinking cursor.  What it looks like is that the pc was rebooted (possible power outage?), but the CMOS boot drive settings were incorrect (trying to boot from secondary drive with no OS installed).  I corrected the CMOS settings, and rebooted.  Ubuntu came back up without any problems, except...

It looks like somehow I've lost internet connectivity, but my LAN connectivity appears fine.  I have Samba configured on the Ubuntu box, and the network drive appears in My Computer on the XP box, and the files are reachable (they're mostly audio files, and they're playable from the XP box.  I can ping the Ubuntu box from the XP box, but not the other way around, however, I have a feeling that this has more to do with the configuration of the XP box than with lack of connectivity (I don't know if XP boxes are configured to respond to ping requests by default).

The XP box can see the internet (I'm posting this using it), but Firefox on the Ubuntu box gives "unable to connect" for anything besides the router.

Router is configured with Ubuntu box as static IP (suggested by Samba documentation), and the XP box is DHCP.  Nothing fishy in any of the router logs or configuration...

So...  where to start debugging?  If I were to guess, perhaps there's a stopped process on the Ubuntu box, or something is misconfigured?  It doesn't have much in the way of reboot history - I installed Ubuntu last week, added Samba, changed the IP address to static, and had everything running without any hitches.  I don't recall any reboots required anywhere along the line, so perhaps this is the first one since everything was brought up successfully.

I have a bit of *NIX background, but mostly as a user, (I have enough sysadmin knowledge to be dangerous) but I'm not sure exactly where to begin looking for configuration issues, error logs, etc.  Any help would be appreciated.

Thanks in advance to everyone for your assistance with this.  Its greatly appreciated, and hopefully will be of benefit to others besides myself.  One last note - I apologize if this is already documented somewhere within the forums.  I did some preliminary searching, but didn't see any threads that dealt with the same issue.

Brawny
(sorry, no fancy .sig)

---

### Post by lloyd_b on 2007-05-17
If you have LAN connectivity, but no internet access, there are two general possibilities:
1.  The Ubuntu box doesn't have a proper gateway defined.
2.  The Ubuntu box has lost it's DNS info, and can't resolve host names

Some experiments to try and diagnose the problem.  In a terminal window:
```
ping -c 1 216.239.51.99
```
(this is one of google.com's IP addresses).
If this fails, then you probably don't have a proper gateway (default route) set up.  In this case, please post the contents of the file "/etc/network/interfaces" (since your using a static IP, the relevant gateway info should be in this file).  Also, it would help if you could post the output from the terminal command "route -n", which shows what routes are defined.

If it succeeds, then try this:
```
nslookup www.google.com
```
If this fails, then you don't have a good DNS server defined.  Most likely this can be fixed by adding a line into the file "/etc/resolv.conf":
```
nameserver xxx.xxx.xxx.xxx
```
(where xxx.xxx.xxx.xxx is the IP address of the DNS server).

Lloyd B.

---

### Post by captevo on 2007-05-17
I have the same problem.
I can ping by IP, but doesn't resolve DNS.
My ISP DNS servers are in etc/resolv.conf
How do you force it to use DNS in /etc/resolv.conf ?

---

### Post by brawny on 2007-05-17
Thanks Lloyd B!

I won't be able to do any diagnostics until I get home this evening, but my guess is the problem is DNS related. 

When I first installed Ubuntu, it self-configured to use DHCP, and everything worked fine.  I changed to a static ip with the install of Samba, which worked without requiring a reboot.  When I did reboot, the cached DNS server IPs (from DHCP) would have been lost, and Ubuntu would not have known where to look. 

If that's the case, then why couldn't it retrieve the IP addresses for my ISP's DNS servers from my router, which  (I believe) uses DHCP to get them my ISP?  Perhaps I need to add my router as a nameserver in /etc/resolv.conf so that the DNS server info remains dynamic (in case my ISP renumbers at some point).

I'll contact my ISP to get the IP address(es) if their servers just in case.

I'll provide an update once I've tried your suggestions, Lloyd.

Thanks again!
Brawny

---

### Post by lloyd_b on 2007-05-17
> If that's the case, then why couldn't it retrieve the IP addresses for my ISP's DNS servers from my router, which (I believe) uses DHCP to get them my ISP? Perhaps I need to add my router as a nameserver in /etc/resolv.conf so that the DNS server info remains dynamic (in case my ISP renumbers at some point).

The problem is that by switching to a static IP, you are no longer running the DHCP client, and the DHCP client is what fetches the DNS settings from the router.  It *is* possible to run a DHCP client with a static IP, but it requires configuring the "/etc/dhcp3/dhclient.conf" file, rather than modifying the system's "/etc/network/interfaces" file.  

I'm not aware of any GUI tools that properly handle configuring "dhclient.conf" (doesn't mean that there aren't any, just that I don't know about them :-))

I do agree with the idea of adding your router as the primary DNS server (if it supports DNS) - I have my home network configured that way as well, for the reason you listed - it means I don't have to do anything if my ISP changes their configuration, except possibly reboot the router.

Lloyd B.

---

### Post by lloyd_b on 2007-05-17
> **captevo said:**
> I have the same problem.
I can ping by IP, but doesn't resolve DNS.
My ISP DNS servers are in etc/resolv.conf
How do you force it to use DNS in /etc/resolv.conf ?

If the DNS servers are defined in resolv.conf, then the system will attempt to use them.

First off, have you tried pinging those DNS server IP's? 

If they respond to pings, could you post the contents of your "/etc/resolv.conf" file?  

Lloyd B.

---

### Post by brawny on 2007-05-17
Ok...  so my internet access is working now, but I'm not sure its the result of anything I've done...

By way of background, here's the debugging info that was requested:

The ping output was as follows:
```
brawny@brawny-server:~$ ping -c 1 216.239.51.99
connect: Network is unreachable
```

nslookup for Google worked, however:
```
brawny@brawny-server:~$ nslookup google.com
Server:         192.168.0.1
Address:        192.168.0.1#53

Non-authoritative answer:
Name:   google.com
Address: 72.14.207.99
Name:   google.com
Address: 64.233.167.99
Name:   google.com
Address: 64.233.187.99

```

My /etc/resolve.conf file already had my router configured as nameserver:
```
# generated by NetworkManager, do not edit!

nameserver 192.168.0.1


```

I did make a change to /etc/network/interfaces:
```
auto lo
iface lo inet loopback

#auto eth0
#iface eth0 inet dhcp
#changed to accommodate static ip

iface eth0 inet static
        address 192.168.0.3
        netmask 255.255.255.0
        gateway 192.168.0.1

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


auto eth0

```
I added in the gateway line in the iface eth0 stanza, because after reading the man pages for interfaces, it looked like it was needed.

I edited the interfaces file using "gksudo gedit /etc/network/interfaces, but had some error messages generated from the command:
```
brawny@brawny-server:~$ gksudo gedit /etc/network/interfaces
(gedit:5671): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

```
I'm not sure of the cause of these messages, but I was still able to edit the file to add the gateway to eth0 however.

When I installed Samba, the instructions mentioned using ifdown -a and ifup -a to take down the network interfaces and restart them.  When I tried that this time, things were a bit wonky.

When bringing the interfaces down:

```
brawny@brawny-server:~$ sudo ifdown -a
SIOCDELRT: No such process

```
which was unexpected...

So when I brought them up:
```
brawny@brawny-server:~$ man ifup
Reformatting ifup(8), please wait...
brawny@brawny-server:~$ sudo ifup -a
eth1: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth1.
eth2: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.eth2.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
eth2: ERROR while getting interface flags: No such device
eth2: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth2.
ath0: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.ath0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
ath0: ERROR while getting interface flags: No such device
ath0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up ath0.
wlan0: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.

```

So the long and short of it is that my internet access is resolved, and it appears that my router is set as my nameserver and gateway, but I'm not quite sure what was changed that fixed it.  I'm also a bit confused about why ifup and ifdown are barfing now...

Thanks Lloyd for your assistance.  I'm sure I'd still be struggling without your suggestions!
Brawny

---

### Post by lloyd_b on 2007-05-18
What fixed things was adding that "gateway" line into the interfaces file.  Without that line, your computer knew how to reach addresses on the local network (the address and netmask entries combine to add a route for that network), but not how to reach any address outside of the local network.  The "gateway" command causes a "default" route to be added, which is used for any address the the computer doesn't know how to reach directly.  

The ping and nslookup results are exactly what I would have expected in that situation ("Network is unreachable" means that the computer doesn't know how to reach that machine - if the machine is simply down, it will give you "Host is unreachable" instead).  Since DNS was referencing your local router, name resolution still worked.

> I edited the interfaces file using "gksudo gedit /etc/network/interfaces, but had some error messages generated from the command:

Sorry, I have no clue on this one (I normally use the "vi" editor in a terminal window).

As for those errors when doing ifup/ifdown, they are a result of having those "iface eth1", "iface eth2", etc, lines in the interfaces file - comment them (and the corresponding "auto" lines) and those errors should disappear.

Finally - while the samba instructions may refer to ifup and ifdown, I would suggest doing the following instead.  In a terminal window:
```
sudo /etc/init.d/networking restart
```
This runs the same script that the system uses to start and stop networking.  Note that the "restart" command is equivalent to:
```
sudo /etc/init.d/networking stop
sudo /etc/init.d/networking start
```


Lloyd B.

---

### Post by brawny on 2007-05-18
Thanks Lloyd!

Your explanation makes sense.  Thanks for making it clear.

I've commented out all of the other interface info except for lo (loopback, I would guess?) and eth0 from the /etc/network/interfaces, and done done a restart as you suggested.  Everything worked fine:
```
brawny@brawny-server:/etc/network$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                   [ OK ] 
brawny@brawny-server:/etc/network$ 

```

The networking script was helpful - much more straightforward than ifup and ifdown.  It looks like I need to invest some time getting familiar with system administration tasks if I'm to keep this thing up and running smoothly.

I appreciate your assistance with this, Lloyd.  Hopefully others will find it useful as well.

Thanks!
Brawny

---

### Post by captevo on 2007-05-18
It's getting interesting for me.

Here's the tracepath when I'm on dhcp (which it works fine):
```
@ubuntustudio:~$ tracepath 205.152.37.23
 1:  192.168.1.103 (192.168.1.103)                          0.099ms pmtu 1500
 1:  192.168.1.1 (192.168.1.1)                              1.087ms 
 2:  192.168.1.1 (192.168.1.1)                            asymm  1   1.024ms pmtu 1492
 3:  65.14.251.41 (65.14.251.41)                          asymm  4  44.358ms 
 4:  205.152.208.29 (205.152.208.29)                       79.363ms 
 5:  ixc00aep-ge-0-3-0.bellsouth.net (205.152.105.65)     149.872ms 
 6:  205.152.208.158 (205.152.208.158)                    asymm  7  58.460ms 
 7:  ixc01asm-pos-3-1.bellsouth.net (205.152.99.153)       45.317ms 
 8:  205.152.99.166 (205.152.99.166)                       45.911ms 
 9:  dns.asm.bellsouth.net (205.152.37.23)                1008.818ms !H
     Resume: pmtu 1492 

```

This is what I get when I'm on static:
```
@ubuntustudio:~$ tracepath 205.152.37.23
 1:  192.168.1.6 (192.168.1.6)                              0.100ms pmtu 1500
 1:  192.168.1.1 (192.168.1.1)                              1.131ms 
 2:  192.168.1.1 (192.168.1.1)                            asymm  1   1.060ms pmtu 1492
 3:  65.14.251.41 (65.14.251.41)                          asymm  4  44.518ms 
 4:  205.152.208.29 (205.152.208.29)                       44.012ms 
 5:  205.152.105.65 (205.152.105.65)                       43.437ms 
 6:  205.152.208.158 (205.152.208.158)                    asymm  7  44.654ms 
 7:  205.152.99.153 (205.152.99.153)                       45.116ms 
 8:  205.152.99.166 (205.152.99.166)                       49.039ms 
 9:  no reply
10:  no reply
11:  no reply
12:  no reply
13:  no reply
14:  no reply
15:  no reply
16:  no reply
17:  no reply

```

```
@ubuntustudio:~$ netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 eth0

```

```
@ubuntustudio:~$ nslookup google.com
;; connection timed out; no servers could be reached

```

---

### Post by lloyd_b on 2007-05-18
captivo - So your are only getting partway to the DNS servers.  I saw something in the info you posted that might explain this:
```
9:  dns.asm.bellsouth.net (205.152.37.23)                1008.818ms !H
     Resume: **pmtu 1492**
```

That "pmtu" stands for "path max transmission unit", which *could* potentially cause some problems if your settings are wrong.  "MTU" (Max Transmission Unit) is the maximum size of a packet that a given network section will allow.  I've seen several cases where an ISP has their network configured to arbitrarily drop packets that exceed this size.  I *suspect* this is what's happening to you - your packets are reaching a certain point in the network, and then being discarded because they are too big.

An experiment - in a terminal window:
```
sudo ifconfig eth0 mtu 1400
```

And see if "nslookup" works correctly.

If this fixes the problem, you can add a "mtu 1400" line under the eth0 section of "/etc/network/interfaces" to permanently set this value.

Lloyd B.

---

