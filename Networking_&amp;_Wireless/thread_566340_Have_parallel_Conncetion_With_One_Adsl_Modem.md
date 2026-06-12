---
title: "Have parallel Conncetion With One Adsl Modem"
date: 2007-10-03
forum: Networking &amp; Wireless
---

### Post by popeno on 2007-10-03
Hello
I have Asus Am602 Adsl Modem
It is combo and have Ethernet and usb conection
I have Ubunto 7.04 Desktop edition.
And I conncet both usb and ethernet to my computer.
it conncets and i have to ips
but one of my conection does not work properly.
It hase no send or recive how can i use them all (parallel)
I will be happy that you answer me.
Thnx
Pooyan:biggrin:

---

### Post by Lambert on 2007-10-03
> **popeno said:**
> Hello
I have Asus Am602 Adsl Modem
It is combo and have Ethernet and usb conection
I have Ubunto 7.04 Desktop edition.
And I conncet both usb and ethernet to my computer.
it conncets and i have to ips
but one of my conection does not work properly.
It hase no send or recive how can i use them all (parallel)
I will be happy that you answer me.
Thnx
Pooyan:biggrin:

Post the output of the following terminal commands here.

```

ifconfig
route

```

---

### Post by popeno on 2007-10-04
pooyan@Jimbo:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:17:9A:78:98:0A  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 Base address:0xb400 

eth1      Link encap:Ethernet  HWaddr 00:13:D4:2C:32:7C  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:38957 errors:0 dropped:0 overruns:0 frame:0
          TX packets:33535 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:19346275 (18.4 MiB)  TX bytes:3480038 (3.3 MiB)
          Interrupt:17 

eth0:avah Link encap:Ethernet  HWaddr 00:17:9A:78:98:0A  
          inet addr:169.254.5.70  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:17 Base address:0xb400 

eth1:avah Link encap:Ethernet  HWaddr 00:13:D4:2C:32:7C  
          inet addr:169.254.5.116  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1074 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1074 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1923214 (1.8 MiB)  TX bytes:1923214 (1.8 MiB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:91.186.213.193  P-t-P:192.168.22.10  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:1420 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1337 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:609114 (594.8 KiB)  TX bytes:114824 (112.1 KiB)

ppp1      Link encap:Point-to-Point Protocol  
          inet addr:91.186.213.72  P-t-P:192.168.22.10  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:34142 errors:0 dropped:0 overruns:0 frame:0
          TX packets:29285 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:17008309 (16.2 MiB)  TX bytes:2422421 (2.3 MiB)

usb0      Link encap:Ethernet  HWaddr 0A:1B:FC:C3:78:A2  
          inet6 addr: fe80::81b:fcff:fec3:78a2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:85 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:17446 (17.0 KiB)  TX bytes:468 (468.0 b)

pooyan@Jimbo:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.22.10   *               255.255.255.255 UH    0      0        0 ppp0
192.168.22.10   *               255.255.255.255 UH    0      0        0 ppp1
link-local      *               255.255.0.0     U     0      0        0 eth0
link-local      *               255.255.0.0     U     0      0        0 eth1
default         *               0.0.0.0         U     0      0        0 ppp1
default         *               0.0.0.0         U     0      0        0 ppp0

---

### Post by Lambert on 2007-10-05
Is this what you want to do?

[http://www.howtoforge.com/network_bonding_ubuntu_6.10](http://www.howtoforge.com/network_bonding_ubuntu_6.10)

---

### Post by popeno on 2007-10-06
yes
that is what i want bit it is a little bit complicated.
Could you give me a more simple way to do that.
thnx you alot to giving me that article.

---

