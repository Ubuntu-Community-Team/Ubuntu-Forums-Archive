---
title: "Wireless doesn't work on ubuntu 14.04, wlan0 gone"
date: 2016-03-17
forum: Networking &amp; Wireless
---

### Post by Jose_L on 2016-03-17
Hello,

I have somehow removed the wlan0 interface on my ubuntu. I was playing around with making a network adapter with kvm and somehow this removed my wlan0 interface. It is still there under ifconfig -a but it seems like the adapter is turned off or something. I have tried pressing fn + f2 but this doesn't work. When I boot into my windows (i have a dual boot setup) I the wifi works. 

Here is the output of ifconfig:

```
ifconfig
br0       Link encap:Ethernet  HWaddr 3e:db:94:75:78:de  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

br0:avahi Link encap:Ethernet  HWaddr 3e:db:94:75:78:de  
          inet addr:169.254.10.153  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

eth0      Link encap:Ethernet  HWaddr 54:04:a6:18:25:66  
          inet addr:10.0.0.10  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::5604:a6ff:fe18:2566/64 Scope:Link
          inet6 addr: 2601:182:c902:65c0:5604:a6ff:fe18:2566/64 Scope:Global
          inet6 addr: 2601:182:c902:65c0:35:6afe:8846:84a3/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3887 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3785 errors:0 dropped:0 overruns:0 carrier:3
          collisions:0 txqueuelen:1000 
          RX bytes:1651901 (1.6 MB)  TX bytes:896061 (896.0 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:2235 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2235 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:187268 (187.2 KB)  TX bytes:187268 (187.2 KB)

virbr1    Link encap:Ethernet  HWaddr 52:54:00:93:2b:a5  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmx0      Link encap:Ethernet  HWaddr 64:d4:da:62:4c:8f  
          UP NOARP  MTU:1400  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:20 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```


and here is the output of ifconfig -a:

```

ifconfig -a
br0       Link encap:Ethernet  HWaddr 3e:db:94:75:78:de  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

br0:avahi Link encap:Ethernet  HWaddr 3e:db:94:75:78:de  
          inet addr:169.254.10.153  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

eth0      Link encap:Ethernet  HWaddr 54:04:a6:18:25:66  
          inet addr:10.0.0.10  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::5604:a6ff:fe18:2566/64 Scope:Link
          inet6 addr: 2601:182:c902:65c0:5604:a6ff:fe18:2566/64 Scope:Global
          inet6 addr: 2601:182:c902:65c0:35:6afe:8846:84a3/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3937 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3817 errors:0 dropped:0 overruns:0 carrier:3
          collisions:0 txqueuelen:1000 
          RX bytes:1656243 (1.6 MB)  TX bytes:915012 (915.0 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:2243 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2243 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:187924 (187.9 KB)  TX bytes:187924 (187.9 KB)

virbr1    Link encap:Ethernet  HWaddr 52:54:00:93:2b:a5  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

virbr1-nic Link encap:Ethernet  HWaddr 52:54:00:93:2b:a5  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 40:25:c2:71:f0:24  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmx0      Link encap:Ethernet  HWaddr 64:d4:da:62:4c:8f  
          UP NOARP  MTU:1400  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:20 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

I am not sure what to do. Please help!


EDIT:

After running 

```

sudo ifconfig wlan0 up

```

wlan0 shows up when I do ifconfig, but there is no inet addr assigned to it.

---

### Post by Jose_L on 2016-03-19
I ran the suggested script in the stickied post and attaching it here. [ATTACH]267890[/ATTACH]

Any help would be really appreciated!

---

### Post by Jose_L on 2016-03-20
Bump! I really need help with this :).

---

