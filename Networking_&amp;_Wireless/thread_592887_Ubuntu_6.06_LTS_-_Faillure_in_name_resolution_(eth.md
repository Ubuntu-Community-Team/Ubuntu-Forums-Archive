---
title: "Ubuntu 6.06 LTS - Faillure in name resolution (eth0)"
date: 2007-10-26
forum: Networking &amp; Wireless
---

### Post by AvWijk on 2007-10-26
Hello,

I installed 6.06 a while ago according this guide, [http://www.howtoforge.com/perfect_setup_ubuntu_6.06_p3](http://www.howtoforge.com/perfect_setup_ubuntu_6.06_p3) but today my server isn't reachable anymore. It suddenly stopped working, didn't do any changes.

 At startup the following errors appear:

* starting ftp server ProFTPD
- IPv6 getaddrinfo 'linuxserver' error: Temporary failure in name resolution
* Starting Apache2 webserver
apache2: could not determine the servers' fully qualified domain name, using 10.0.0.190 for ServerName


Even it I want to run apt-get update it says 'Temporary failure in name resolution'.

The strange thing is my machine has an Intel 10/100 combo network card (that means 2 network plugs) and the other one works well. :confused:

---

### Post by alastair on 2007-10-26
I guess you need to look and see what DNS is set in :

/etc/resolv.conf

e.g. If it says :

nameserver <IP ADDR>

Can you :

ping <IP ADDR> ?

---

### Post by AvWijk on 2007-10-27
resolv.conf says 

```
search lan
10.0.0.138 
```

which is the xDSL router. This file is not altered as this appears to be also the default setting in my Ubuntu LiveCD.
I cannot ping anything except for 10.0.0.190 (which is the box' fixed IP adress) and 10.0.0.127.

---

### Post by lH)4~mK0e on 2007-10-27
> **AvWijk said:**
> 

The strange thing is my machine has an Intel 10/100 combo network card (that means 2 network plugs) and the other one works well. :confused:

So if I understand this correctly, eth1 works properly, and eth0 does not.  Please post the results of these commands:

```
$ ifconfig
$ lspci | grep Intel Pro
```

---

### Post by AvWijk on 2007-10-27
```
$ ifconfig
```

eth0   Link encap:Ethernet  HWaddr XXXXXX (Mac Adress here)
          inet addr:10.0.0.190  Bcast:10.0.0.255 
          Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
         RX Bytes 0 TX Bytes 0


lo        Link encap:Local Loopback
          inet addr:127.0.0.1   Mask:255.0.0.0
         inet6 addr:
         UP BROADCAST LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0



```
lspci | grep Pro
```

0000:03:04 Ethernet Controller Intel Corporation .... Ethernet Pro 10/100
rev 05 (and so on)

0000:03:05 Ethernet Controller Intel Corporation .... Ethernet Pro 10/100
rev 05 (and so on)

---

### Post by AvWijk on 2007-11-01
Suddenly my connection is up again, but still the same errors. It has something to do with the domain name of the thing.

---

