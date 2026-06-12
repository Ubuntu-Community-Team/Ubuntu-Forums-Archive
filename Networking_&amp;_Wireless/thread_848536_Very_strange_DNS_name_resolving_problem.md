---
title: "Very strange DNS name resolving problem"
date: 2008-07-03
forum: Networking &amp; Wireless
---

### Post by Jarre on 2008-07-03
First of all, if You're interested enough then scroll down to bottom of this post for the "not-so-important-background-information".

My problem seems to be some sort of "application layer name resolving problem". I can ping and connect (eg. using Firefox) to hosts using IP numbers, but all connection attempts using domain names end up with timeout.

Although ping and FF fail to resolve domain names, host and nslookup commands work just fine. And as I said, pinging hosts with IP numbers work.

At the moment I'm running Ubuntu 8.04 Desktop Live from CD.

EDIT: I've also tried installing Windows XP on the same computer and it works just fine, no problems at all.

My configuration with some comments:

```
ubuntu@ubuntu:~$ lspci | grep Ethernet
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
00:09.0 Ethernet controller: 3Com Corporation 3c905B 100BaseTX [Cyclone] (rev 30)

```

I'm using SiS as eth0, I've also tried 3Com and that made no difference.

```
ubuntu@ubuntu:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:0b:6a:b0:35:16  
          inet addr:192.168.0.108  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20b:6aff:feb0:3516/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:189 errors:0 dropped:0 overruns:0 frame:0
          TX packets:225 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:215034 (209.9 KB)  TX bytes:33416 (32.6 KB)
          Interrupt:16 Base address:0xd400 

eth1      Link encap:Ethernet  HWaddr 00:50:da:5c:12:eb  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Base address:0xf80 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7870 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7870 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:393500 (384.2 KB)  TX bytes:393500 (384.2 KB)


```

At the moment eth0 is connected to a D-Link switch, where it gets the 192.168.x.x address. I've also tried connecting eth0 straight to cable modem's interface, but problems were exactly the same.

```
ubuntu@ubuntu:~$ more /etc/resolv.conf 
### BEGIN INFO
#
# Modified_by:  NetworkManager
# Process:      /usr/bin/NetworkManager
# Process_id:   7804
#
### END INFO

search cable.inet.fi


nameserver 193.210.19.19
nameserver 192.168.0.1


ubuntu@ubuntu:~$ more /etc/nsswitch.conf 
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
ubuntu@ubuntu:~$ more /etc/hosts
127.0.0.1 localhost
127.0.1.1 ubuntu

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

And here are the results:

```
ubuntu@ubuntu:~$ host www.sonera.fi
www.sonera.fi has address 194.251.244.241
ubuntu@ubuntu:~$ nslookup www.sonera.fi
Server:		193.210.19.19
Address:	193.210.19.19#53

Non-authoritative answer:
Name:	www.sonera.fi
Address: 194.251.244.241

ubuntu@ubuntu:~$ ping www.sonera.fi

ubuntu@ubuntu:~$ 

```

Above, I interrupted the ping command with CTRL-C after about five minutes.

And the background information:

I upgraded my cable modem internet connection and I had to get a new modem. Old one was Thomson TCW710 and the new one is Linksys (Cisco) WCM300-EU (don't know if this makes any difference).

After the upgrade my Ubuntu 7.10 server couldn't resolve any domain names. I'd been planning to upgrade to 8.04 and decided to do that, hoping that I could get rid of the problems.

Well, that didn't work. I can't install 8.04 server (or desktop) because the installer hangs at "Configuring APT - Scanning the mirror". Same thing with 7.10 and 7.04.

---

### Post by nixscripter on 2008-07-03
I don't know if this will help, but I looked up the /etc/resolv.conf man page, and the search keyword says this:

> 
Search list for host-name lookup.

The search list is normally determined from the local domain name; by default, it contains only the local domain name. This may be changed by listing the desired domain search path following the search keyword with spaces or tabs separating the names.

...

Note that this process may be slow and will generate a lot of network traffic if the servers for the listed domains are not local, and that queries will time out if no server is available for one of the domains.


As an experiment, try removing the search line from your /etc/resolv.conf file, since you have an alternative nameserver (193.etc) to do resolutions.

Hope this helps.

---

### Post by Jarre on 2008-07-03
> As an experiment, try removing the search line from your /etc/resolv.conf file, since you have an alternative nameserver (193.etc) to do resolutions.

Hope this helps.

Thanks for the advice, I tried to remove the "search" line from /etc/resolv.conf but that didn't help.

---

### Post by Jarre on 2008-07-03
Just to add some confusion :), I just booted my laptop with the same Ubuntu 8.04 desktop CD and everything works just fine; no problems with name resolving or anything. It's an IBM T41 with Intel chipset. So, what the h*ll is wrong with my server hardware? I don't want to install Windows on it, although it works...

---

### Post by nixscripter on 2008-07-03
When you do boot from CD then what does that resolv.conf file say?

---

### Post by Jarre on 2008-07-04
> **nixscripter said:**
> When you do boot from CD then what does that resolv.conf file say?

After booting from CD:

```
ubuntu@ubuntu:~$ more /etc/resolv.conf 
### BEGIN INFO
#
# Modified_by:  NetworkManager
# Process:      /usr/bin/NetworkManager
# Process_id:   7804
#
### END INFO

search cable.inet.fi


nameserver 193.210.19.19
nameserver 192.168.0.1

```

---

### Post by nixscripter on 2008-07-05
Hmm, that looks okay.

What is your routing table (**route** command)? Is it the same on the CD versus the HD?

If that looks okay, I would then start seeing exactly what's being sent. Try the nslookup and the ping again with **tcpdump** running.

---

### Post by lswb on 2008-07-05
If you have ever run ufw or any other firewall on the laptop, make sure that port 53 (I think, you can check /etc/services) isn't blocked.

---

### Post by Jarre on 2008-07-07
> **nixscripter said:**
> Hmm, that looks okay.

What is your routing table (**route** command)? Is it the same on the CD versus the HD?

This is strange, **route** command does't finish at all, it hangs after link-local line:

```
ubuntu@ubuntu:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     0      0      0   eth0
link-local      *               255.255.0.0     U     1000   0      0   eth0

```

So that's not okay at all.

> If that looks okay, I would then start seeing exactly what's being sent. Try the nslookup and the ping again with **tcpdump** running.

**tcpdump** doesn't seem to work either. I started it with **sudo tcpdump -vv** and it doesn't output anything even if I'm performing **ping**, **host** and **nslookup** commands in another terminal window.

---

### Post by Jarre on 2008-07-07
> **lswb said:**
> If you have ever run ufw or any other firewall on the laptop, make sure that port 53 (I think, you can check /etc/services) isn't blocked.

There's no firewall running at all, all ports are open.

---

### Post by nixscripter on 2008-07-08
I don't see a default route in the routing table. Try adding one, and see if that works: ```
sudo route add default eth0
```

Also, **route** sometimes takes a while. Try waiting like 5 minutes (for network timeouts or something), and then see if it finishes.

---

### Post by Jarre on 2008-08-15
I added default route with

```
sudo route add default eth0
```

but that didn't seem to do anything. Route command stalls, I waited for like 15 minutes but nothing happened. And network isn't working at all, I get an IP address from ISP but that's it.

---

### Post by Jarre on 2008-10-18
> **Jarre said:**
> I added default route with

```
sudo route add default eth0
```

but that didn't seem to do anything. Route command stalls, I waited for like 15 minutes but nothing happened. And network isn't working at all, I get an IP address from ISP but that's it.

Well, I couldn't solve the original problem and bought a new hardware for my server which is working fine.

---

