---
title: "Ubuntu Server 12.04 Gateway SLOW Upload"
date: 2013-11-23
forum: Networking &amp; Wireless
---

### Post by brandon-bilbo on 2013-11-23
I have a 120/25mbit connection that goes to my ubuntu server which acts as a gateway/router and goes to a switch to the rest of my network (2 NIC setup, obviously). All computers get the 120 download but everything behind the ubuntu server doesnt get anymore than 5mbit upload. All of them seem to flatline at 5mbit like the ubuntu server is "capping" them. The server itself will get 25 upload though. 

I tried hooking up the cable modem to each individual computer. All get correct speeds. I've swapped cables, ports, NICS, anything I can think of. I set up a samba share on the server and tested file transfer between all the computers and the server. Over 100MB down/up. 

I think it has something to do with the firewall but that doesn't make any sense to me. I am standing by to post any requested additional information for you guys to help me troubleshoot this. 

Thank you

---

### Post by brandon-bilbo on 2013-11-23
At least some suggestions on some diagnostics I can post that will be helpful in troubleshooting this

---

### Post by Doug S on 2013-11-23
Hi and welcome to Ubuntu forums.

My setup is very similar to yours. However, I have much more pathetic ISP limits. As a test, I moved a computer over to my other external static IP address, and fetched a large file from a port forwarded web server behind my 12.04 server which is the main router/gateway to my LAN. I was able to exclude my ISP from this, because I have a switch between my 2 static IP addresses, upstream from my server, but downstream from my DSL modem.

I got approximately 6,000,000 bytes per second upload speed for the test. Load on my server (observed using "top") during the transfer was very low. I suspect, but have no proof, the data rate limit for my test was the pathetic very very old linksys firewall/router that I have over on my other static IP address.

For your case: Can you get the 5 Mbit rate on two client computers at the same time? Meaning that 10 Mbits/sec are uploading through your server. Can you observe CPU loading during file transfer using "top" and it is a limiting factor? Perhaps list your firewall rule set here:```
sudo iptables -v -x -n -L
sudo iptables -t nat -v -x -n -L
```

---

### Post by brandon-bilbo on 2013-11-23
I sat 2 of the computers side by side and did the test concurrently 3 or 4 times to make sure.. they shared total download bandwidth each getting ~60mbit down while going at the same time, and as I expected, they both got the ~5-6 during upload.. This is freaking me out...

output of the 2 commands
```

iptables -v -x -n -L

Chain INPUT (policy ACCEPT 16181 packets, 1619801 bytes)
    pkts      bytes target     prot opt in     out     source               destination
   20005  2720551 LOG        all  --  WAN    *       0.0.0.0/0            0.0.0.0/0            LOG flags 0 level 7 prefix "BANDWIDTH_IN:"
     863    90345 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0
      52     2978 ACCEPT     all  --  lo     *       0.0.0.0/0            0.0.0.0/0
  439143 23465762 ACCEPT     all  --  LAN    *       0.0.0.0/0            0.0.0.0/0
    3034  1023949 ACCEPT     all  --  WAN    *       0.0.0.0/0            0.0.0.0/0            state RELATED,ESTABLISHED
       0        0 ACCEPT     tcp  --  WAN    *       0.0.0.0/0            0.0.0.0/0            tcp dpt:22
    1689   206863 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0            limit: avg 15/min burst 5 LOG flags 0 level 7 prefix "Dropped by firewall: "


Chain FORWARD (policy DROP 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination
  684309 157947905 LOG        all  --  *      WAN     0.0.0.0/0            0.0.0.0/0            LOG flags 0 level 7 prefix "BANDWIDTH_OUT:"
  608098 400552222 LOG        all  --  WAN    *       0.0.0.0/0            0.0.0.0/0            LOG flags 0 level 7 prefix "BANDWIDTH_IN:"
  684309 157947905 ACCEPT     all  --  LAN    WAN     0.0.0.0/0            0.0.0.0/0
  605819 400289592 ACCEPT     all  --  WAN    LAN     0.0.0.0/0            0.0.0.0/0            state RELATED,ESTABLISHED
      42     2352 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:8000
     396    21392 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:56666
    1886   241631 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:56666


Chain OUTPUT (policy ACCEPT 197980 packets, 3691960450 bytes)
    pkts      bytes target     prot opt in     out     source               destination
   19102  1918189 LOG        all  --  *      WAN     0.0.0.0/0            0.0.0.0/0            LOG flags 0 level 7 prefix "BANDWIDTH_OUT:"
    1698  3883484 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0            limit: avg 15/min burst 5 LOG flags 0 level 7 prefix "Dropped by firewall: "

```


```

sudo iptables -t nat -v -x -n -L

Chain PREROUTING (policy ACCEPT 20089 packets, 1562843 bytes)
    pkts      bytes target     prot opt in     out     source               destination
      10      552 DNAT       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:8000 to:192.168.0.30:8000
     351    19060 DNAT       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:56666 to:192.168.0.30:56666
    1713   222726 DNAT       udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:56666 to:192.168.0.30:56666


Chain INPUT (policy ACCEPT 2403 packets, 194607 bytes)
    pkts      bytes target     prot opt in     out     source               destination


Chain OUTPUT (policy ACCEPT 3023 packets, 240449 bytes)
    pkts      bytes target     prot opt in     out     source               destination


Chain POSTROUTING (policy ACCEPT 2122 packets, 250419 bytes)
    pkts      bytes target     prot opt in     out     source               destination
   20362  1571223 MASQUERADE  all  --  *      WAN     0.0.0.0/0            0.0.0.0/0

```

---

### Post by Doug S on 2013-11-24
You are doing a staggering amount of logging with your firewall rule set. I wonder if that is causing you some issues, but if so I wouldn't have expected to you get double the overall upload speed using two computers. Did you observe significant CPU usage using "top"?. Perhaps try to eliminate some of that logging, just as a test.

By the way, your "Dropped by firewall" logging rules do not actually indicate Dropped packets, as the defaults are ACCEPT for those chains.

Are you using "tc" (traffic control)? (I don't know how to check).

---

### Post by brandon-bilbo on 2013-11-24
the logging is high because of another issue on a different thread i have on here with counter strike not being able to connect to competitive matchmaking [http://ubuntuforums.org/showthread.php?t=2189754](http://ubuntuforums.org/showthread.php?t=2189754) . Thats also why its defaulted to accept, i was just trying some stuff. Its normally defaulted to drop like its supposed too.

yes some significant usage from syslog during speedtesting but not over 50% cpu load. upload speeds still dont exceed 5-6mbit with logging disabled. 

no i dont use tc i edit the firewall rules with webmin.. (not sure what tc is, but assume its for editing iptables?? too tired to google at the moment)

---

### Post by brandon-bilbo on 2013-11-26
Thanks to Doug S this issue has been resolved. 

The culprit was the MTU setting on my WAN adapter. the WAN adapter was set to auto while connected to my cable modem and the mtu setting was somewhere in the 400-500 range. Manually it to 1500 and fixed my problems. Thanks Doug S.

---

