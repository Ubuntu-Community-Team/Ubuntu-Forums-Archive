---
title: "eth0 fails on startup"
date: 2005-08-18
forum: Networking &amp; Wireless
---

### Post by janit on 2005-08-18
I wanted to get HandBrake working and I got it working by adding "deb [http://demudi.agnula.org/packages/demudi](http://demudi.agnula.org/packages/demudi) testing main" to my sources. Now I messed up my eth0 by getting some other updates from there as well.

It does not seem to be able to load the module at boot and /sbin does not seem to be in the path... It works after I load the module. I'm no pro, but I got it working with some tips from this forum:

```

janit@queso:~$ ifconfig
bash: ifconfig: command not found
janit@queso:~$ /sbin/ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7625 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7625 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:474941 (463.8 KiB)  TX bytes:474941 (463.8 KiB)

janit@queso:~$ sudo /sbin/ifup eth0
SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
SIOCSIFNETMASK: No such device
eth0: ERROR while getting interface flags: No such device
Failed to bring up eth0.
janit@queso:~$ sudo /sbin/modprobe
modprobe           modprobe.modutils
janit@queso:~$ sudo /sbin/modprobe e100
janit@queso:~$ /sbin/ifconfig
eth0      Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx
          inet addr:xxx.xxx.xxx.xxx  Bcast:xxx.xxx.xxx.xxx  Mask:xxx.xxx.xxx.xxx
          inet6 addr: xxxx::xxxx:xxxx:xxxx:xxxx Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:34 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:17461 (17.0 KiB)  TX bytes:1534 (1.4 KiB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7832 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7832 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:493751 (482.1 KiB)  TX bytes:493751 (482.1 KiB)

janit@queso:~$ 

``` 

It's good to have it working manually, but I've no idea how to solve the boot time problem... It just tells me "failed to bring up eth0".

Any ideas?

---

### Post by jrev on 2005-08-18
If you get those xxx.xxx.xxx from your query, you better reconfigure your eth0 card
apparently the configuration went off ...

---

