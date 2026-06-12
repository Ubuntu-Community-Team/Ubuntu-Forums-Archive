---
title: "RPC Timeout with NFS"
date: 2006-12-19
forum: Networking &amp; Wireless
---

### Post by skewray on 2006-12-19
I have a CentOS 4 nfs server on a private network, serving various machines with no problems.  I did the same setup on a recent install of ubuntu and got some weird behaviour.
A command to mount the NFS partition gives "RPC: timeout" after a few seconds, and at exactly the same time, the server prints a mesage to its /var/log/messages stating that the mount has been authenticated.  nfsvers=2 and nfsvers=3 behave the same.

I also tried nfs4.  There I get "permission denied" and no authentication message on the server.

Since the server seems to be working fine, I suspect some sort of firewall issue on the Ubuntu machine.

Thanks for any suggestions.

Brian

---

### Post by skewray on 2007-01-06
After several weeks, I still have not figured out what the problem might be.  Any tips appreciated...

Brian

---

### Post by kj1h234lkj1234 on 2007-01-08
I had this problem a few minutes ago.

Portmap wasn't able to contact itself on a local port, because my iptables rules never allowed localhost to access itself.

```
iptables -A INPUT -s localhost -j ACCEPT
```fixed it for me.

Maybe post the out of:

```
iptables -L --line-numbers
```

so we can verify that you're not running into a similar firewall situation?

---

### Post by skewray on 2007-01-08
Typing your iptables command (along with the one for the local network) does fix the problem for nfs 2 & 3.  Thanks!  nfs4 still doesn't work, but I only need one to work.

Initially iptables is empty; INPUT, FORWARD, and ACCEPT all have (policy ACCEPT) and nothing listed below that.  I looked at iptables before as a source of the problem, but I was unable to find whatever file iptables is supposed to read on startup.  Do you know where it lives?  I assume that running an "iptables" command only lasts until the next reboot.  I suppose I can stick something in rc.local, which is a bit crude.  I would rather do it right.

Brian

---

### Post by kj1h234lkj1234 on 2007-01-08
I'm not sure where the file that holds the rules is (and I don't see anything in 'man iptables'), but my rules persist between reboots automatically.

I did, however, also write a script that installs my default rules:

(note: It's still a work in progress, and I haven't updated it for NFS. It only allows samba on my local class C network currently)

```
#!/bin/bash

# variables

INTERNET="eth0"

LOOPBACK="127.0.0.0/8"
CLASS_A="10.0.0.0/8"
CLASS_B="172.16.0.0/12"
CLASS_C="192.168.0.0/16"
CLASS_D="224.0.0.0/4"
CLASS_E="240.0.0.0/5"

######## sysctl.conf crap

# stop broadcast echoing
echo 1 > /proc/sys/net/ipv4/icmp_echo_ignore_broadcasts

# disable source-routing
for f in /proc/sys/net/ipv4/conf/*/accept_source_route; do
        echo 0 > $f
done

# enable syncookie protection
echo 1 > /proc/sys/net/ipv4/tcp_syncookies

# no icmp redirects
for f in /proc/sys/net/ipv4/conf/*/accept_redirects; do
        echo 0 > $f
done

# no sending redirects
for f in /proc/sys/net/ipv4/conf/*/send_redirects; do
        echo 0 > $f
done

# no spoofed packets
for f in /proc/sys/net/ipv4/conf/*/rp_filter; do
        echo 1 > $f
done

# log packets with illegal addresses
for f in /proc/sys/net/ipv4/conf/*/log_martians; do
        echo 1 > $f
done

######## flush iptables

iptables -F
iptables -t nat -F
iptables -t mangle -F

######## loopback

iptables -A INPUT -i lo -j ACCEPT
iptables -A OUTPUT -o lo -j ACCEPT

######## policies

iptables -P INPUT DROP
iptables -P OUTPUT ACCEPT
iptables -P FORWARD DROP

iptables -t nat -P PREROUTING ACCEPT
iptables -t nat -P OUTPUT ACCEPT
iptables -t nat -P POSTROUTING ACCEPT

iptables -t mangle -P PREROUTING ACCEPT
iptables -t mangle -P OUTPUT ACCEPT

######## clear chains

iptables -X
iptables -t nat -X
iptables -t mangle -X

######## allow pinging

iptables -A INPUT -s $CLASS_C -p icmp -j ACCEPT

######## allow related incoming

iptables -I INPUT 1 -m state --state ESTABLISHED,RELATED -j ACCEPT

######## user-stuff

# SSH locally
iptables -A INPUT -s $CLASS_C -p tcp --destination-port 22 -j ACCEPT

# apache
iptables -A INPUT -p tcp --destination-port 80 -j ACCEPT

# samba + network share crap
iptables -A INPUT -s $CLASS_C -p tcp --destination-port 137 -j ACCEPT
iptables -A INPUT -s $CLASS_C -p udp --destination-port 137 -j ACCEPT
iptables -A INPUT -s $CLASS_C -p tcp --destination-port 138 -j ACCEPT
iptables -A INPUT -s $CLASS_C -p udp --destination-port 138 -j ACCEPT
iptables -A INPUT -s $CLASS_C -p tcp --destination-port 139 -j ACCEPT
iptables -A INPUT -s $CLASS_C -p udp --destination-port 139 -j ACCEPT
iptables -A INPUT -s $CLASS_C -p tcp --destination-port 445 -j ACCEPT
iptables -A INPUT -s $CLASS_C -p udp --destination-port 445 -j ACCEPT

```

(I actually think I can combine those last 8 rules into 4 rules... I'll have to read my itpables book a bit more later)

This is my setup for a server on my simple home network. It allows incoming connections on only certain ports, but output is not checked at all (it assumes my box is not sending any illegtimate traffic).

I'm by no means an expert at iptables, but I can get it to do what I want for the most part. :)

---

### Post by skewray on 2007-01-11
The machine does appear to remember after a reboot.  I can find no file that appears to contain the saved table, though.  Odd, that.  Anyway, problem fixed.

---

