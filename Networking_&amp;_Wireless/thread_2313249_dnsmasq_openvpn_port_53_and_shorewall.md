---
title: "dnsmasq openvpn port 53 and shorewall"
date: 2016-02-10
forum: Networking &amp; Wireless
---

### Post by lister171254 on 2016-02-10
I'm running Ubuntu 15.10 and have the following issue.

I'm in the process of configuring shorewall to allow vpn traffic through. I've done thius previously on my laptop, so was reasonably confident of a 2 minute job.

openvpn uses udp port 1194, so after setting up the shorewall interface, policy and rule I expected this to work, but it didn't

Shorewall reported that it prevented access to port 53

```
Feb 11 12:09:39 LeosLinux kernel: [158260.045163] Shorewall:fw-vpn:REJECT:IN= OUT=tun0 SRC=172.20.35.138 DST=198.18.0.1 LEN=63 TOS=0x00 PREC=0x00 TTL=64 ID=53714 DF PROTO=UDP SPT=54824 DPT=53 LEN=43 
Feb 11 12:09:39 LeosLinux kernel: [158260.045173] Shorewall:fw-vpn:REJECT:IN= OUT=tun0 SRC=172.20.35.138 DST=198.18.0.2 LEN=63 TOS=0x00 PREC=0x00 TTL=64 ID=16199 DF PROTO=UDP SPT=54824 DPT=53 LEN=43 

```

I belive port 53 is for DNS related traffic, so I assume this comes from dnsmasq

```
llist@LeosLinux:~$ sudo netstat -tulpn

Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:1194          0.0.0.0:*               LISTEN      15612/openvpn   
tcp        0      0 127.0.1.1:53            0.0.0.0:*               LISTEN      1379/dnsmasq    
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      5622/cupsd      
tcp6       0      0 ::1:631                 :::*                    LISTEN      5622/cupsd      
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           1219/avahi-daemon: 
udp        0      0 0.0.0.0:49034           0.0.0.0:*                           1219/avahi-daemon: 
udp        0      0 0.0.0.0:57347           0.0.0.0:*                           15612/openvpn   
udp        0      0 127.0.1.1:53            0.0.0.0:*                           1379/dnsmasq    
udp        0      0 0.0.0.0:631             0.0.0.0:*                           1284/cups-browsed
udp6       0      0 :::54077                :::*                                1219/avahi-daemon: 
udp6       0      0 :::5353                 :::*                                1219/avahi-daemon: 

```

Weird thing is that after an update to my Laptop, it now behaves the same; shorewall rejects packets with a destination port of 53. Nothing changed on the laptop other than the update.

---

### Post by SeijiSensei on 2016-02-10
Do you have a rule that allows all traffic to the localhost interface?  With iptables the rule would be

```
/sbin/iptables -A INPUT -i lo -j ACCEPT
```

and should be at the top of the ruleset.

---

### Post by lister171254 on 2016-02-10
Sorry, I only know a bit about shorewall

Point is, though, that I'm trying to find out why Openvpn starts on port 1194, but the firewall error logs show connection to port 53. Don't know why this happens

---

### Post by SeijiSensei on 2016-02-10
Dnsmasq listens on 127.0.1.1:53, an address served by the localhost interface, so there needs to be a way for the machine to hand DNS queries to dnsmasq.  If you look at /etc/resolv.conf, you'll see that it has just one entry, "nameserver 127.0.1.1".

You could end-run dnsmasq and use a DNS server that's visible over the VPN instead.  You'd need to edit /etc/resolvconf/resolv.conf.d/head to add a line like
```
nameserver 8.8.8.8
```
which would send DNS queries out to Google's public server at 8.8.8.8.

---

### Post by lister171254 on 2016-02-10
I guess what I'm trying to figure out is where port 53 gets involved, and why this was working on my laptop prior to the latest update.

I'm using the package network-manager-openvpn and configure the vpn vie the applet. The gateway port is specified as 1194

---

### Post by lister171254 on 2016-02-15
ok. Can eliminate dnsmasq from the list of possible culprits as I disabled this via the NetworkManager config

So I guess that leaves openvpn (which uses 1194) and something else that uses 53

```
A 'netstat' shows that openvpn listens on 1194

Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:1194          0.0.0.0:*               LISTEN      3589/openvpn    
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               udp        0      0 0.0.0.0:40335           0.0.0.0:*                           3589/openvpn    
udp        0      0 0.0.0.0:631             0.0.0.0:*                           913/cups-browsed
udp6       0      0 :::5353                 :::*                                855/avahi-daemon: r
udp6       0      0 :::58539                :::*                                855/avahi-daemon: r

```

---

