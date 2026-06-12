---
title: "problem with bonding"
date: 2016-01-26
forum: Networking &amp; Wireless
---

### Post by voiceforhim82 on 2016-01-26
First thank you for looking this over. The problem I am having is that despite my best efforts I am getting some weird errors that I cannot get corrected nor can I figure out why they are doing what they are doing. What is happening is that a couple of my nics are deciding they are going to acquire an ip address instead of being a slave like they are supposed to. 

first is my network setup pulled from /etc/network/interfaces
                                                                                                                                                                 1,1           Top```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).


# The loopback network interface
auto lo p11p1 p11p2 p11p3 p11p4 bond0 p4p1 p4p2 p4p3 p4p4 bond1
iface lo inet loopback




#iface p11p1 inet dhcp


#p11p1 configuration
iface p11p1 inet manual
        bond-master bond0


#p11p2 configuration
iface p11p2 inet manual
        bond-master bond0


#p11p3 configuration
iface p11p3 inet manual
        bond-master bond0


#p11p4 configuration
iface p11p4 inet manual
        bond-master bond0


# Bonding p11p1-p11p4 to create bond0 NIC to server
iface bond0 inet manual
        bond-mode 4
        bond-miimon 100
        bond-updelay 0
        bond-downdelay 0
        lacp_rate 1
        slaves p11p1 p11p2 p11p3 p11p4
#       up ifconfig bond0 up     
#       address 192.168.1.40
#       netmask 255.255.255.0
#       broadcast 192.168.1.255
#       network 192.168.1.0
#       gateway 192.168.1.1


#p4p1 configuration
iface p4p1 inet manual
        bond-master bond1


#p4p2 configuration
iface p4p2 inet manual
 
#p4p3 configuration
iface p4p3 inet manual
        bond-master bond1


#p4p4 configuration
iface p4p4 inet dhcp
#iface p4p4 inet dhcp
#address 192.168.1.41
#gateway 192.168.1.1
#netmask 255.255.255.0


# Bonding p4p1-p4p3 to create bond1 NIC for firewall
iface bond1 inet manual
        bond-mode 4
        bond-miimon 100
        bond-updelay 5
        bond-downdelay 5
        slaves p4p1 p4p2 p4p3
#       address 192.168.1.42
#       netmask 255.255.255.0
#       broadcast 192.168.1.255
#       network 192.168.1.0
#       up ifconfig bond1 up


#       gateway 192.168.1.1


                                                                                                                                                                1,1           Top



```

The delays I have tried various amounts with little success. That is why they are different. Have tried all the way to 300ms.  

Below is my if config. As you can see even in ifconfig they are called as slaves yet are assigned ip addresses as well. 

```
bond0     Link encap:Ethernet  HWaddr 00:1b:21:a1:0b:54  
          inet6 addr: fe80::21b:21ff:fea1:b54/64 Scope:Link
          UP BROADCAST RUNNING MASTER MULTICAST  MTU:1500  Metric:1
          RX packets:6610 errors:0 dropped:52 overruns:0 frame:0
          TX packets:533 errors:0 dropped:5 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:942110 (942.1 KB)  TX bytes:118281 (118.2 KB)


bond1     Link encap:Ethernet  HWaddr 00:1b:21:a1:0a:b8  
          inet6 addr: fe80::21b:21ff:fea1:ab8/64 Scope:Link
          UP BROADCAST RUNNING MASTER MULTICAST  MTU:1500  Metric:1
          RX packets:8278 errors:0 dropped:123 overruns:0 frame:0
          TX packets:1237 errors:0 dropped:13 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1233150 (1.2 MB)  TX bytes:133763 (133.7 KB)


eth0      Link encap:Ethernet  HWaddr d8:eb:97:f9:59:cb  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


eth1      Link encap:Ethernet  HWaddr f8:32:e4:8a:4e:55  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:6029 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6029 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1790925 (1.7 MB)  TX bytes:1790925 (1.7 MB)


p11p1     Link encap:Ethernet  HWaddr 00:1b:21:a1:0b:54  
          UP BROADCAST RUNNING SLAVE MULTICAST  MTU:1500  Metric:1
          RX packets:875 errors:0 dropped:0 overruns:0 frame:0
          TX packets:68 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:109779 (109.7 KB)  TX bytes:9036 (9.0 KB)
          Interrupt:55 Memory:fe2a0000-fe2c0000 


p11p2     Link encap:Ethernet  HWaddr 00:1b:21:a1:0b:54  
          inet addr:192.168.1.206  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING SLAVE MULTICAST  MTU:1500  Metric:1
          RX packets:1030 errors:0 dropped:52 overruns:0 frame:0
          TX packets:158 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:86100 (86.1 KB)  TX bytes:28767 (28.7 KB)
          Interrupt:57 Memory:fe240000-fe260000 


p11p3     Link encap:Ethernet  HWaddr 00:1b:21:a1:0b:54  
          UP BROADCAST RUNNING SLAVE MULTICAST  MTU:1500  Metric:1
          RX packets:1960 errors:0 dropped:0 overruns:0 frame:0
          TX packets:113 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:199750 (199.7 KB)  TX bytes:27762 (27.7 KB)
          Interrupt:57 Memory:fe1a0000-fe1c0000 


p11p4     Link encap:Ethernet  HWaddr 00:1b:21:a1:0b:54  
          UP BROADCAST RUNNING SLAVE MULTICAST  MTU:1500  Metric:1
          RX packets:2746 errors:0 dropped:0 overruns:0 frame:0
          TX packets:194 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:546545 (546.5 KB)  TX bytes:52716 (52.7 KB)
          Interrupt:60 Memory:fe140000-fe160000 


p4p1      Link encap:Ethernet  HWaddr 00:1b:21:a1:0a:b8  
          UP BROADCAST RUNNING SLAVE MULTICAST  MTU:1500  Metric:1
          RX packets:2962 errors:0 dropped:38 overruns:0 frame:0
          TX packets:59 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:593590 (593.5 KB)  TX bytes:7455 (7.4 KB)
          Interrupt:46 Memory:fe4a0000-fe4c0000 


p4p2      Link encap:Ethernet  HWaddr 00:1b:21:a1:0a:b8  
          inet addr:192.168.1.244  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING SLAVE MULTICAST  MTU:1500  Metric:1
          RX packets:4598 errors:0 dropped:48 overruns:0 frame:0
          TX packets:1081 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:576109 (576.1 KB)  TX bytes:103864 (103.8 KB)
          Interrupt:50 Memory:fe440000-fe460000 


p4p3      Link encap:Ethernet  HWaddr 00:1b:21:a1:0a:b8  
          UP BROADCAST RUNNING SLAVE MULTICAST  MTU:1500  Metric:1
          RX packets:718 errors:0 dropped:37 overruns:0 frame:0
          TX packets:97 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:63451 (63.4 KB)  TX bytes:22444 (22.4 KB)
          Interrupt:50 Memory:fe3a0000-fe3c0000 


p4p4      Link encap:Ethernet  HWaddr 00:1b:21:a1:0a:bb  
          inet addr:192.168.1.237  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:21ff:fea1:abb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:38268 errors:0 dropped:0 overruns:0 frame:0
          TX packets:43067 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4074352 (4.0 MB)  TX bytes:23476915 (23.4 MB)
          Interrupt:53 Memory:fe340000-fe360000 


virbr0    Link encap:Ethernet  HWaddr ba:17:37:ce:b6:ed  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


vmnet1    Link encap:Ethernet  HWaddr 00:50:56:c0:00:01  
          inet addr:172.16.4.1  Bcast:172.16.4.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:179 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


vmnet8    Link encap:Ethernet  HWaddr 00:50:56:c0:00:08  
          inet addr:172.16.130.1  Bcast:172.16.130.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:177 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)





```



Thank you again for the help. Been tearing my hair out with this. They are acting like dhcp nics and getting leases from my router. Yet nowhere are they configured that way. Only one nic should be getting a dhcp lease.

---

### Post by voiceforhim82 on 2016-01-29
Well for anyone else that has this problem it had to do with the network manager. I had not realized that needed to be uninstalled. It was hijacking a couple interfaces at random for its own devious schemes. Ran [COLOR=#111111][FONT=Consolas]sudo apt-get purge network-manager [/FONT][/COLOR]and did a network restart and it pulled up just fine. Did a full system restart just to verify with no problems. Was really annoying to say the least. Hope this may help someone else in their adventures.

---

