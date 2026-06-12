---
title: "Ethernet connection"
date: 2008-04-29
forum: Networking &amp; Wireless
---

### Post by Red Moose on 2008-04-29
I did a fresh install of 8.04 and got no internet.  I'm using an onboard/integrated controller.  I was able to ping my router (192.168.1.1) successfully.  It worked for a bit because I managed to install the nvidia restricted driver.  I haven't been able to get it to work again though.  I checked the cable, etc. and it's good. I also tried changing the connection from free roaming to dhcp.  I'm not sure what commands to post the output of so just let me know.  Just don't try a "sudo rm -rf /" on me. :-)

I know that there's lots of posts on this already but I couldn't find the solution.

Thanks a lot!!

Matt

---

### Post by jtrindle on 2008-04-29
Can you still ping 192.168.1.1?

what do 

  ifconfig 
and 
  route 

commands tell you?

Does 
  sudo dhclient
work, and does it change the output of the previous two commands?

---

### Post by Red Moose on 2008-04-29
Thank you!  I can't give the output of those commands because the text file got scrambled after a usb transfer from ubuntu to windows.  However, it doesn't matter because I was able to ping the router after I ran sudo dhclient and then I tried firefox and I'm connected.  Thank you very much!  Oh, ifconfig did not change after dhclient but route did.
It's amazing how simple it can be when someone knows what they're doing!  I appreciate it!

---

### Post by Red Moose on 2008-04-30
Actually, it doesn't work upon reboot.  I'll get the output of those commands to you.

---

### Post by Red Moose on 2008-04-30
ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 00:03:47:c1:cc:f3  
          inet6 addr: fe80::203:47ff:fec1:ccf3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2216 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:137242 (134.0 KB)  TX bytes:468 (468.0 B)


lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:818 errors:0 dropped:0 overruns:0 frame:0
          TX packets:818 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:40900 (39.9 KB)  TX bytes:40900 (39.9 KB)

```

route:
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
```

dhclient:
```
Listening on LPF/eth0/00:03:47:c1:cc:f3
Sending on   LPF/eth0/00:03:47:c1:cc:f3
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPOFFER of 192.168.1.103 from 192.168.1.1
DHCPREQUEST of 192.168.1.103 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.103 from 192.168.1.1
bound to 192.168.1.103 -- renewal in 32601 seconds.
```


ifconfig: (after dhclient)
```
eth0      Link encap:Ethernet  HWaddr 00:03:47:c1:cc:f3
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::203:47ff:fec1:ccf3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2314 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:144256 (140.8 KB)  TX bytes:4594 (4.4 KB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:818 errors:0 dropped:0 overruns:0 frame:0
          TX packets:818 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:40900 (39.9 KB)  TX bytes:40900 (39.9 KB)

```

route: (after dhclient)
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref   Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
default         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
```

It does work after running those commands but after I restart it stops working.

---

### Post by Red Moose on 2008-04-30
**Bump**

---

