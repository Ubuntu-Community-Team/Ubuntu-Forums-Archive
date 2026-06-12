---
title: "cant find my router page"
date: 2007-05-06
forum: Networking &amp; Wireless
---

### Post by mills on 2007-05-06
i used to be able to get to my router page by typing 192.168.1.254 in my url bar

but this isn't working now that i have a wireless connection.

internet connection and everything else is fine, i can ping the router.

my netstat is showing 192.168.1.254 as my gateway still.

so why cant i connect to it via my browser?

it tries to connect but eventually times out.

any help on this is appreciated as i need to forward some ports and stuff

---

### Post by mills on 2007-05-06
maybe this information can help you help me

```
alex@alex-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra1       RT61 Wireless  ESSID:"SpeedTouchC78D2E"  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:14:7F:64:62:09   
          Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=87/100  Signal level:-50 dBm  Noise level:-79 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

alex@alex-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0D:61:E3:B9:8B  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:22 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:181 errors:0 dropped:0 overruns:0 frame:0
          TX packets:181 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:13560 (13.2 KiB)  TX bytes:13560 (13.2 KiB)

ra1       Link encap:Ethernet  HWaddr 00:19:5B:8A:4C:FB  
          inet addr:192.168.1.64  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::219:5bff:fe8a:4cfb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:265760 errors:0 dropped:0 overruns:0 frame:0
          TX packets:240937 errors:0 dropped:0 overruns:0 carrier:0
          collisions:1297 txqueuelen:1000 
          RX bytes:174111395 (166.0 MiB)  TX bytes:196480417 (187.3 MiB)
          Interrupt:22 

alex@alex-desktop:~$ route
Kernel IP routeing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 ra1
link-local      *               255.255.0.0     U     1000   0        0 ra1
default         speedtouch.lan  0.0.0.0         UG    0      0        0 ra1
alex@alex-desktop:~$ dig

; <<>> DiG 9.3.4 <<>>
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 7131
;; flags: qr rd ra; QUERY: 1, ANSWER: 13, AUTHORITY: 0, ADDITIONAL: 13

;; QUESTION SECTION:
;.                              IN      NS

;; ANSWER SECTION:
.                       1498870 IN      NS      a.root-servers.net.
.                       1498870 IN      NS      j.root-servers.net.
.                       1498870 IN      NS      g.root-servers.net.
.                       1498870 IN      NS      c.root-servers.net.
.                       1498870 IN      NS      f.root-servers.net.
.                       1498870 IN      NS      b.root-servers.net.
.                       1498870 IN      NS      h.root-servers.net.
.                       1498870 IN      NS      k.root-servers.net.
.                       1498870 IN      NS      d.root-servers.net.
.                       1498870 IN      NS      m.root-servers.net.
.                       1498870 IN      NS      i.root-servers.net.
.                       1498870 IN      NS      e.root-servers.net.
.                       1498870 IN      NS      l.root-servers.net.

;; ADDITIONAL SECTION:
d.root-servers.net.     3599981 IN      A       128.8.10.90
f.root-servers.net.     3599981 IN      A       192.5.5.241
b.root-servers.net.     3599981 IN      A       192.228.79.201
c.root-servers.net.     3599981 IN      A       192.33.4.12
h.root-servers.net.     3599981 IN      A       128.63.2.53
g.root-servers.net.     3599981 IN      A       192.112.36.4
m.root-servers.net.     3599981 IN      A       202.12.27.33
i.root-servers.net.     3599981 IN      A       192.36.148.17
e.root-servers.net.     3599981 IN      A       192.203.230.10
k.root-servers.net.     3599981 IN      A       193.0.14.129
j.root-servers.net.     3599981 IN      A       192.58.128.30
l.root-servers.net.     3599981 IN      A       198.32.64.12
a.root-servers.net.     3599981 IN      A       198.41.0.4

;; Query time: 56 msec
;; SERVER: 192.168.1.254#53(192.168.1.254)
;; WHEN: Sun May  6 15:08:59 2007
;; MSG SIZE  rcvd: 436
```

---

### Post by jrusso2 on 2007-05-06
Try to connect to this for your router

192.168.1.0

---

### Post by mills on 2007-05-06
> **jrusso2 said:**
> Try to connect to this for your router

192.168.1.0

unable to connect:confused:

---

