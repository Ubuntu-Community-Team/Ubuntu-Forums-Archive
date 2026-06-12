---
title: "Cannot access Local Network with Wifi, but can access the net"
date: 2008-06-16
forum: Networking &amp; Wireless
---

### Post by Jordanwb on 2008-06-16
In my laptop I have an onboard ethernet card. I can access local and internet. However with my Linksys WPC54G (installed with ndisgtk), I can access the net (like right now), but I can't access the local network. I can get an IP from the router though. If I try to ssh into my server with PuTTY, I get "No route to host".

---

### Post by pytheas22 on 2008-06-16
Can you ping the machines on your local network?  When you try to putty in, are you connecting to a hostname that needs to be resolved or an IP address?  Did you try using the built-in ssh client (just type something like "ssh username@192.168.1.2" on a command line) instead of putty?

---

### Post by imneo on 2008-06-16
please do:

```
sudo /sbin/ifconfig -a
sudo netstat -rn
```

and post the results :popcorn:

---

### Post by Jordanwb on 2008-06-16
I can ping.

```

jordanwb@Laptop:~$ sudo /sbin/ifconfig -a
[sudo] password for jordanwb: 
eth0      Link encap:Ethernet  HWaddr 00:10:a4:86:6b:b7  
          inet addr:192.168.1.133  Bcast:192.168.1.255  Mask:255.255.255.128
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

irda0     Link encap:IrLAP  HWaddr 00:00:00:00  
          NOARP  MTU:2048  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:8 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:75 errors:0 dropped:0 overruns:0 frame:0
          TX packets:75 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8809 (8.6 KB)  TX bytes:8809 (8.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:16:b6:c9:9c:9c  
          inet addr:192.168.1.14  Bcast:192.168.1.127  Mask:255.255.255.128
          inet6 addr: fe80::216:b6ff:fec9:9c9c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:126 errors:0 dropped:0 overruns:0 frame:0
          TX packets:213 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:54671 (53.3 KB)  TX bytes:26853 (26.2 KB)
          Interrupt:11 Memory:24000000-24010000 

jordanwb@Laptop:~$ sudo netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.0     0.0.0.0         255.255.255.128 U         0 0          0 wlan0
192.168.1.128   0.0.0.0         255.255.255.128 U         0 0          0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 wlan0
0.0.0.0         192.168.1.129   0.0.0.0         UG        0 0          0 eth0
jordanwb@Laptop:~$ 


```

For eth0 it's a static IP and it's not connected. I don't know where the 169.254.0.0 network came from. :confused:

---

