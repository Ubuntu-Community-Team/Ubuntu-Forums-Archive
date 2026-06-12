---
title: "Can't ping localhost??"
date: 2005-10-22
forum: Networking &amp; Wireless
---

### Post by mwnovak on 2005-10-22
Following my Hoary-to-Breezy upgrade, I can't ping localhost (by name or ip):

```

mwnovak@myserver:~$ ping -c 5 localhost
PING myserver.net (127.0.0.1) 56(84) bytes of data.

--- myserver.net ping statistics ---
5 packets transmitted, 0 received, 100% packet loss, time 3998ms

```

Same result if I ping 127.0.0.1.  

I'm not sure where to begin posting troubleshooting information, but the following bits might let someone more savvy lend a hand...

Output from "ifconfig":

```

mwnovak@myserver:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:30:65:C1:8D:72  
          inet addr:192.168.0.10  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::230:65ff:fec1:8d72/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:3848 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2738 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:406784 (397.2 KiB)  TX bytes:416702 (406.9 KiB)
          Interrupt:41 Base address:0xf800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:33 errors:0 dropped:0 overruns:0 frame:0
          TX packets:33 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2772 (2.7 KiB)  TX bytes:2772 (2.7 KiB)

```

Output from "netstat -rv && netstat -iv":

```

mwnovak@myserver:~$ netstat -rv && netstat -iv
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.0.0     *               255.255.255.0   U         0 0          0 eth0
default         192.168.0.1     0.0.0.0         UG        0 0          0 eth0
Kernel Interface table
Iface   MTU Met   RX-OK RX-ERR RX-DRP RX-OVR    TX-OK TX-ERR TX-DRP TX-OVR Flg
eth0   1492 0      4114      0      0      0     2943      0      0      0 BMRU
lo    16436 0        33      0      0      0       33      0      0      0 LRU

```

Loopback doesn't show up in the routing table--is that normal?  If I try adding it manually, I get:

```

mwnovak@myserver:~$ sudo route add -net 127.0.0.1
sudo: unable to lookup myserver via gethostbyname()
SIOCADDRT: Invalid argument

```

Not sure what that means, exactly.  What is SIOCADDRT?  gethostbyname()?  I'm starting to wonder if my install isn't completely hosed.
 
Other associated information...

My /etc/hostname:
```

myserver.net

```

My /etc/hosts:

```

127.0.0.1 myserver.net localhost.localdomain localhost

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

My /etc/host.conf:

```

order hosts,bind
multi on

```

My /etc/network/interfaces:

```

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface
iface eth0 inet dhcp
        hostname www.myserver.net

```

Does anyone have any ideas?  Suggestions?  I can post more information ... I just have no idea what's going on here and I'm not sure where to start.  Searching through the Ubuntu forums, hitting the Debian lists, googling around ... I'm not getting much traction on this problem.  Any input is appreciated.

--MW

---

### Post by jasmuz on 2005-10-22
I bet that if you remove the .net from your hostname, you would be able to ping it.

---

### Post by mwnovak on 2005-10-22
I read somewhere that /etc/hostname or /etc/hosts needed a FQDN for certain mail services to work correctly, so I had it setup with myserver.net.


I just removed the ".net" portion from /etc/hosts and /etc/hostname (leaving only "myserver") and restarted the machine.  No joy: I still can't ping localhost or 127.0.0.1.

--MW

---

### Post by mwnovak on 2005-10-23
I'm sitting here with a fresh Breezy installation that I threw onto an old office machine: I can't ping localhost or 127.0.0.1 from this machine, either.

I'm kind of new to *nix, but... is this normal or desirable behavior?  I thought a functioning loopback interface was required by several applications?

Can any Breezy users out there successfully ping localhost?

--MW

---

### Post by MAZDA on 2005-10-23
The Local Host yes but not my ADSL-Router.

[http://ubuntuforums.org/showthread.php?p=438081#post438081](http://ubuntuforums.org/showthread.php?p=438081#post438081)

---

### Post by mwnovak on 2005-10-25
Okay, I'm an idiot.  

I have the following line in a firewall script that I use on my machines, meant to disable ping responses:

```
/bin/echo "1" > /proc/sys/net/ipv4/icmp_echo_ignore_all
```

I'd put the same script on the fresh Breezy installation before hooking it up to the network.  

So, duh: no wonder I haven't been getting ping responses on my Ubuntu installations.

Back to the problem of mySQL not working after my Breezy upgrade (see [http://www.ubuntuforums.org/showthread.php?t=78614](http://www.ubuntuforums.org/showthread.php?t=78614) if anyone want to lend an idea)...

--MW

---

### Post by bonewhat on 2005-10-26
what does

ip addr ls

and

ip route ls 

say?

---

### Post by mwnovak on 2005-10-26
Like I said, the "ping localhost" problem was caused by my own firewall script... kind of embarassing, really. :)

For kicks, the commands output the following:

```

mwnovak@myserver:~$ ip addr ls && echo"" && ip route ls
1: lo: <LOOPBACK,UP> mtu 16436 qdisc noqueue
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP> mtu 1492 qdisc pfifo_fast qlen 1000
    link/ether 00:30:65:c1:8d:72 brd ff:ff:ff:ff:ff:ff
    inet 192.168.0.10/24 brd 192.168.0.255 scope global eth0
    inet6 fe80::230:65ff:fec1:8d72/64 scope link
       valid_lft forever preferred_lft forever
3: sit0: <NOARP> mtu 1480 qdisc noop
    link/sit 0.0.0.0 brd 0.0.0.0

192.168.0.0/24 dev eth0  proto kernel  scope link  src 192.168.0.10
default via 192.168.0.1 dev eth0

```

How's that look?

The larger problem remains getting mysql back after the Breezy upgrade: [http://www.ubuntuforums.org/showthread.php?t=78614](http://www.ubuntuforums.org/showthread.php?t=78614)

--MW

---

