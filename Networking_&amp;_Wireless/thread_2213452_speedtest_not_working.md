---
title: "speedtest not working"
date: 2014-03-26
forum: Networking &amp; Wireless
---

### Post by xeidy on 2014-03-26
I tried downloading the speedtest_cli.py and tried running it by
# python speedtest_cli.py

and installed pip and install speedtest-cli

# speedtest

both have same result:

Retrieving speedtest.net configuration...
Retrieving speedtest.net server list...
Testing from HostName, LC (63.xx.xx.243)...
Selecting best server based on ping...

and it is stuck here.. won't go ahead.

any ideas?

thanks

```
# netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
0.0.0.0         63.xx.xx.241  0.0.0.0         UG        0 0          0 eth0
63.xx.xx.240  0.0.0.0         255.255.255.248 U         0 0          0 eth0

```


```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 63.xx.xx.243
        netmask 255.255.255.248
        gateway 63.xx.xx.241
        dns-search xxxxxx

```

---

### Post by gifford on 2014-03-26
How long did you wait for the results?
It takes anywhere from 5 to 20 minutes when I use it. Really slow...
Here is a link with some info on configuration of speedtest: [http://binarynature.blogspot.com/2013/03/measure-internet-connection-speed-from-linux-command-line.html](http://binarynature.blogspot.com/2013/03/measure-internet-connection-speed-from-linux-command-line.html)

Please post if you get good results.

---

