---
title: "No Internet after upgrading to Hardy"
date: 2008-06-22
forum: Networking &amp; Wireless
---

### Post by abinash on 2008-06-22
I have upgraded to Hardy by my update manager but after that i am not able to use the internet. I have gone through different posts but nothing helped. 

I have two Ethernet interfaces, on board NVIDIA nForce Networking Controller(etho) and Realtek RTl8139 Family PCI Fast ethernet(eth1). I have connected the Lan to eth1. I have configured them with static ip. Still I am not able to use the internet. When I tried to configure any of the interfaces at Network Tools it gave   following message.
> The interface does not exist
Check that it is correctly typed and that it is correctly supported by your system.

My ifconfig results as follows
```
routed@MyWorld:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:e0:18:99:**:**  
          inet addr:192.168.*.*  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Base address:0xe000 

eth1      Link encap:Ethernet  HWaddr 00:e0:20:6b:**:**  
          inet addr:192.168.*.*  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:128 errors:0 dropped:0 overruns:0 frame:0
          TX packets:45 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7680 (7.5 KB)  TX bytes:4469 (4.3 KB)
          Interrupt:19 Memory:feaffc00-feaffcff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:52 errors:0 dropped:0 overruns:0 frame:0
          TX packets:52 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3752 (3.6 KB)  TX bytes:3752 (3.6 KB)

routed@MyWorld:~$ sudo ifconfig etho up
etho: ERROR while getting interface flags: No such device

```
I have added last two line,if any one can point out faults.
My /etc/network/interfaces: shows the following
```
auto lo
iface lo inet loopback






iface eth1 inet static
address 192.168.1.7
netmask 255.255.255.0
gateway 192.168.1.1

auto eth1

iface eth0 inet static
address 192.168.1.3
netmask 255.255.255.0
gateway 192.168.1.1

auto eth0


```
I have attached the /var/log/syslog  file.
I have adsl router to connect to internet with gateway address 192.168.1.1. I am able to connect to internet with same static ip as given in ubuntu on different OS. **I am also able to ping to the gateway in ubuntu.**:confused:

Without internet it's very difficult to work on Ubuntu.](*,)
Please help me out.:cry:

---

### Post by akkiraju on 2008-06-22
Hi Abinash,

     Network tools in Hardy seems to have a problem. My network conenction working fine but when I use network tools and click on configure to reconfigure my settings, I get the same message you are getting.

 try doing 
 
            sudo ifconfig eth0 up

may be ur interface is down.

---

### Post by wapper on 2008-06-22
Hey,
Same here, use the RT61PCI. Can`t resolve the problem anywhere on the internet, nothing works for me. Have try Windows driver and so on.... .
Has given op, and going back to Gutsy Gibbon where everything works :-)

Jan Jensen, Denmark

---

