---
title: "ping works, nslookup works but I can only acces few sites"
date: 2007-05-04
forum: Networking &amp; Wireless
---

### Post by froggy70 on 2007-05-04
Hi everybody.
I have been running Feisty Fawn for about a week now and I am mainly satisfied. But one bug i almost killing me. I can't access the internet and then not update  :(
Strangely ping,nslookup,gaim and pages like google.com and my own page adrup.dk works :confused:

Here is some info:

**cat /etc/host.conf**
# The "order" line is only used by old versions of the C library.
order hosts,bind
multi on

**cat /etc/hosts**
80.161.134.1 net
127.0.0.1 localhost
127.0.1.1 adrup-desktop

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

**cat /etc/resolv.conf**
nameserver 192.168.1.1

**cat /etc/nsswitch.conf**
# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis

**netstat -rn**
Kernel IP routeing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 eth0

**netstat -r**
Kernel IP routeing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.0     *               255.255.255.0   U         0 0          0 eth0
link-local      *               255.255.0.0     U         0 0          0 eth0
default         192.168.1.1     0.0.0.0         UG        0 0          0 eth0

**ifconfig**
eth0      Link encap:Ethernet  HWaddr 00:13:8F:53:93:01  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:8fff:fe53:9301/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2141 errors:197 dropped:0 overruns:0 frame:197
          TX packets:1832 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2047944 (1.9 MiB)  TX bytes:172334 (168.2 KiB)
          Interrupt:22 Base address:0xdead 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:288 (288.0 b)  TX bytes:288 (288.0 b)

**ip route show**
192.168.1.0/24 dev eth0  proto kernel  scope link  src 192.168.1.4 
169.254.0.0/16 dev eth0  scope link  metric 1000 
default via 192.168.1.1 dev eth0

Sorry for bad spelling. I am Danish ;)

I hope someone can help!!!!

Regards
Mark Petersen

---

### Post by lloyd_b on 2007-05-04
You may have an "MTU issue".  Here's an experiment to try that may (or may not) help.  In a terminal window:
```
sudo ifconfig eth0 mtu 1400
```
Then attempt accessing an internet site that you're having problems with.  If it still fails, try again using 1300, 1200, etc, until you reach 500.

If your internet connection starts working at any point, then we've identified the problem.  If you get down to 500 and it's still not working, then my guess is wrong.

Lloyd B.

---

### Post by froggy70 on 2007-05-04
It worked with
```
 sudo ifconfig eth0 mtu 1400
```

I owe one ;)

What does this script exactly do???

---

### Post by lloyd_b on 2007-05-04
> **froggy70 said:**
> It worked with
```
 sudo ifconfig eth0 mtu 1400
```

I owe one ;)

What does this script exactly do???

"MTU" stands for "Max Transmission Unit".  This is the maximum size of a packet that a given  network will allow.  The standard value for Ethernet networks is 1500 (which was what your computer was defaulting to), but there have been a number of posts recently with issues where certain ISP's simply drop packets that exceed a certain size.  What the "ifconfig" command I gave you does is tell your computer to limit it's maximum packet size to the specified value (1400), so that the ISP won't drop your packets anymore.

Now for the fun part - as it stands, you'll have to rerun that "ifconfig" command every time you restart your computer.  What I suggest doing is adding that command into the file "/etc/init.d/rc.local", so that it runs every time you reboot.  Add it at the second line in the file (immediately following the "#!/bin/sh" line).  Note that you need "root" permissions to edit that file, so something like "sudo nano /etc/init.d/rc.local" is required to edit it.

Edit: Note: if you put that command in rc.local, you do not need (or want) the "sudo" - just "ifconfig eth0 mtu 1400"
Lloyd B.

---

### Post by froggy70 on 2007-05-04
I did run
```
sudo gedit /etc/init.d/rc.local
```
and added:

 ifconfig eth0 mtu 1400

immediately after "#!/bin/sh"

and then i did a restart and it worked.

Thanks a lot!!!

---

