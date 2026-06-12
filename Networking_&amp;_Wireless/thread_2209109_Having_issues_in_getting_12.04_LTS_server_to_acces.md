---
title: "Having issues in getting 12.04 LTS server to access past gateway"
date: 2014-03-04
forum: Networking &amp; Wireless
---

### Post by Priest Apostate on 2014-03-04
I am running into an issue in getting my Ubuntu 12.04 LTS server to access anything past the default gateway (pinging, tracepath/traceroute and dig fail). I am trying to use this server for studying on picking up my LPIC, and would like to be able to access the machine remotely. 

I have set up my static settings within /etc/network/interfaces:

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.1.7
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.68.1.1

**********************
**********************

and added the nameserver addresses from my ISP to /etc/resolv.conf:

nameserver 68.105.28.11
nameserver 68.105.29.11

**********************
**********************
- I've confirmed that the router has reserved the eth0 IP address: (192.168.1.7) 
- I've restarted the service multiple times, and tried dig, and ping -- to no avail: 

priestapostate@predator451:~$ sudo service networking start
networking stop/waiting
priestapostate@predator451:~$ ping [www.google.com](www.google.com)
ping: unknown host [www.google.com](www.google.com)
priestapostate@predator451:~$ dig [www.google.com](www.google.com)

; <<>> DiG 9.8.1-P1 <<>> [www.google.com](www.google.com)
;; global options: +cmd
;; connection timed out; no servers could be reached
priestapostate@predator451:~$
**********************
**********************
- I've also checked online to try to find out what have I missed. 
  I don't have Netfilter installed, so I don't think that I need to worry about iptables (if I am wrong, please let me know). 
  I don't have any blocked services activated on my Netgear router

I don't see anything wrong with my ifconfig: 
priestapostate@predator451:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:25:b3:a4:e9:ca
          inet addr:192.168.1.7  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::225:b3ff:fea4:e9ca/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7697 errors:0 dropped:132 overruns:0 frame:0
          TX packets:2770 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1021288 (1.0 MB)  TX bytes:401522 (401.5 KB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:680 (680.0 B)  TX bytes:680 (680.0 B)
**********************
**********************

If anyone could point me in the right direction, I'd be most appreciative, as I've been wracking my brain over the past few hours, trying to find out what I'm missing...

---

### Post by tomearp on 2014-03-04
> priestapostate@predator451:~$ ping [www.google.com](www.google.com)
ping: unknown host [www.google.com](www.google.com)

Try
```
host google.com
```
and check you are successfully resolving host names. If not then maybe try changing your name servers in /etc/resolv.conf to something else (e.g. 8.8.8.8 and 8.8.4.4) and try again.

---

### Post by Priest Apostate on 2014-03-04
> **tomearp said:**
> Try
```
host google.com
```
and check you are successfully resolving host names. If not then maybe try changing your name servers in /etc/resolv.conf to something else (e.g. 8.8.8.8 and 8.8.4.4) and try again.

Thanks for the quick response. 
I have tried as you asked: 

priestapostate@predator451:~$ sudo vi /etc/resolv.conf
[sudo] password for priestapostate:
priestapostate@predator451:~$ sudo service networking restart
stop: Unknown instance:
networking stop/waiting
priestapostate@predator451:~$ host google.com
;; connection timed out; no servers could be reached
******************
******************
nameserver listing in /etc/resolv.conf

nameserver 8.8.8.8
nameserver 8.8.4.4
******************
******************
I've also double-checked the router settings. Port forwarding and port triggering haven't been activated, just to make sure...

---

### Post by tomearp on 2014-03-04
Can you please paste the output of
```
route -n
```

---

### Post by xicarusx on 2014-03-04
Instead of using resolv.conf

add this to /etc/networking/interfaces
dns-nameservers 8.8.8.8 8.8.4.4

---

### Post by Iowan on 2014-03-04
Have you tried to **ping** an IP address (like 8.8.8.8)?
(reference post #4)

---

### Post by Priest Apostate on 2014-03-05
One workshift (with overtime) and one reboot later...
This is the routing table: 

routepriestapostate@predator451:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         192.168.1.1     0.0.0.0         UG    100    0        0 eth0
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
***********************
***********************
It seems that I am now able to access/ping outside sites. Rebooting the system was the only thing I did to the server. 
I am confused (which won't serve well to find out what I did to correct this): was the reboot responsible for the resolution? If so, I thought that simply restarting the networking service would have sufficed...

Another question: I think I may have this confused (if so, my apologies in advance, as I'm still learning), but will I suffer any adverse effects to add the server's static IP address to the routing table? I'm thinking that that might cause some type of self-referencing loop, that will just FUBAR the network, but I am not sure...

---

