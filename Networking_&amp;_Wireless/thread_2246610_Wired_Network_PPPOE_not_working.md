---
title: "Wired Network PPPOE not working"
date: 2014-10-02
forum: Networking &amp; Wireless
---

### Post by govinda3 on 2014-10-02
[TABLE]
[TR="bgcolor: transparent"]
[TD="class: votecell, bgcolor: transparent"][CENTER][COLOR=#777777]
[/COLOR][COLOR=#808185][/COLOR]
[/CENTER]
[/TD]
[TD="class: postcell, bgcolor: transparent"]I have created PPPOE connection in ubuntu and now my network manager is not showing edit and delete connection as well as all other network manager options are unclickable i am new to ubuntu so please help me to solve this issue.here's few information.

```


 ## interfaces(5) file used by ifup(8) and ifdown(8)
    auto lo
    iface lo inet loopback
    auto dsl-provider
    iface dsl-provider inet ppp
    pre-up /sbin/ifconfig eth1 up # line maintained by pppoeconf
    provider dsl-provider
    auto eth0
    iface eth0 inet manual

    #auto lo
    #iface lo inet loopback

    #auto eth0
    #iface eth0 inet dhcp

 ------------------------------------------------------
root@jack:/home/jackie# sudo ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:25:b3:5e:ec:5f  
          inet6 addr: fe80::225:b3ff:fe5e:ec5f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:31 errors:0 dropped:0 overruns:0 frame:0
          TX packets:29 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9104 (9.1 KB)  TX bytes:3914 (3.9 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:488 errors:0 dropped:0 overruns:0 frame:0
          TX packets:488 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:37480 (37.4 KB)  TX bytes:37480 (37.4 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1f:3c:dd:ca:ff  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```


[/TD]
[/TR]
[/TABLE]

---

### Post by varunendra on 2014-10-04
Any interface mentioned in the /etc/network/interfaces file is no more controlled/controllable by Network Manager. NM is designed as such to avoid possible conflicts with the traditional method (interfaces file). Although it can be made to control it (by just changing the value of 'managed' from 'false' to 'true' in /etc/NetworkManager/NetworkManager.conf file), but is not recommended to do so.

Please tell us what you want to achieve and what have you done so far to get there. If setting up a DSL connection is all you want, it can be done from Network Manager GUI itself, no need to do it manually or any other ways.

---

