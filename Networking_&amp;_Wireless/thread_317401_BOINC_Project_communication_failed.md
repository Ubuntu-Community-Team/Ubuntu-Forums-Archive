---
title: "BOINC: Project communication failed"
date: 2006-12-12
forum: Networking &amp; Wireless
---

### Post by janm on 2006-12-12
Hi,
Boinc is telling me that I have no internet connection, but all other applications work just fine with: http, ftp, ssh, rdp, exchange, aim/icq, etc.

Here are the messages from within boinc...
```
Tue 12 Dec 2006 03:42:57 PM CET||Starting BOINC client version 5.4.11 for i686-pc-linux-gnu
Tue 12 Dec 2006 03:42:57 PM CET||libcurl/7.15.4 OpenSSL/0.9.8b zlib/1.2.3 libidn/0.6.3
Tue 12 Dec 2006 03:42:57 PM CET||Data directory: /var/lib/boinc-client
Tue 12 Dec 2006 03:42:57 PM CET||Processor: 2 GenuineIntel Intel(R) Pentium(R) D CPU 3.20GHz
Tue 12 Dec 2006 03:42:57 PM CET||Memory: 1.97 GB physical, 980.52 MB virtual
Tue 12 Dec 2006 03:42:57 PM CET||Disk: 18.78 GB total, 4.07 GB free
Tue 12 Dec 2006 03:42:57 PM CET||No general preferences found - using BOINC defaults
Tue 12 Dec 2006 03:42:57 PM CET||Reading preferences override file
Tue 12 Dec 2006 03:42:57 PM CET||Local control only allowed
Tue 12 Dec 2006 03:42:57 PM CET||Listening on port 31416
Tue 12 Dec 2006 03:42:57 PM CET||Platform changed from  to i686-pc-linux-gnu - resetting projects
Tue 12 Dec 2006 03:42:57 PM CET||This computer is not attached to any projects
Tue 12 Dec 2006 03:42:57 PM CET||Visit http://boinc.berkeley.edu for instructions
Tue 12 Dec 2006 03:43:52 PM CET||Fetching configuration file from http://bbc.cpdn.org/get_project_config.php
Tue 12 Dec 2006 03:43:52 PM CET||Project communication failed: attempting access to reference site
Tue 12 Dec 2006 03:43:52 PM CET||Access to reference web site failed - check network connection or proxy configuration.
```

I'm running Edgy with kernel...
```
$ cat /proc/version
Linux version 2.6.17-10-generic (root@vernadsky) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Fri Oct 13 18:45:35 UTC 2006 (Ubuntu 2.6.17-10.33-generic)
```

Networking outside the program works just fine...
```
$ ping bbc.cpdn.org
PING climatedbs3.oucs.ox.ac.uk (163.1.13.135) 56(84) bytes of data.
64 bytes from climatedbs3.oucs.ox.ac.uk (163.1.13.135): icmp_seq=1 ttl=47 time=41.6 ms
64 bytes from climatedbs3.oucs.ox.ac.uk (163.1.13.135): icmp_seq=2 ttl=47 time=49.6 ms
64 bytes from climatedbs3.oucs.ox.ac.uk (163.1.13.135): icmp_seq=3 ttl=47 time=40.4 ms

--- climatedbs3.oucs.ox.ac.uk ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2007ms
rtt min/avg/max/mdev = 40.434/43.911/49.694/4.123 ms
```

```
$ wget -S http://bbc.cpdn.org/get_project_config.php
--16:56:24--  http://bbc.cpdn.org/get_project_config.php
           => `get_project_config.php.1'
Resolving bbc.cpdn.org... 163.1.13.135
Connecting to bbc.cpdn.org|163.1.13.135|:80... connected.
HTTP request sent, awaiting response... 
  HTTP/1.1 200 OK
  Date: Tue, 12 Dec 2006 15:53:33 GMT
  Server: Apache/2.2.0 (Unix) PHP/5.1.4
  X-Powered-By: PHP/5.1.4
  Content-Length: 221
  Keep-Alive: timeout=5, max=100
  Connection: Keep-Alive
  Content-Type: text/xml
Length: 221 [text/xml]

100%[====================================>] 221           --.--K/s             

16:56:24 (21.08 MB/s) - `get_project_config.php' saved [221/221]

```

I have no idea what the problem could be...I tried both apt-get (5.4.11-1) and downloading the bbc installation (5.3.16)..same exact problem on both.

I do have vmware-player installed, but I don't think that's the problem since no other apps are having network problems...
```
$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:35:AB:F4:D2  
          inet addr:10.36.1.30  Bcast:10.36.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:35ff:feab:f4d2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:359808 errors:0 dropped:0 overruns:0 frame:0
          TX packets:158904 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:126331676 (120.4 MiB)  TX bytes:29213792 (27.8 MiB)
          Interrupt:169 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:9867 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9867 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3055452 (2.9 MiB)  TX bytes:3055452 (2.9 MiB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:C0:00:01  
          inet addr:172.16.159.1  Bcast:172.16.159.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:133 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:C0:00:08  
          inet addr:172.16.193.1  Bcast:172.16.193.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:133 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
```

```
$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
172.16.193.0    *               255.255.255.0   U     0      0        0 vmnet8
10.36.1.0       *               255.255.255.0   U     0      0        0 eth0
172.16.159.0    *               255.255.255.0   U     0      0        0 vmnet1
default         10.36.1.254     0.0.0.0         UG    0      0        0 eth0
```

I'm able to connect through a SOCKS proxy, however.
any ideas?
-jan

---

### Post by janm on 2006-12-15
bump. anyone?

---

### Post by janm on 2007-01-11
2nd bump

---

### Post by OsakaWilson on 2007-02-23
Third...

---

