---
title: "wifi Internet"
date: 2008-05-05
forum: Networking &amp; Wireless
---

### Post by iv_s on 2008-05-05
hi!

i have pc with ubuntu 8.04 and macbook with os x 10.5.2.
i want to share ubuntu internet connection to mac
ubuntu connected to internet with dsl modem connected to eth1
and has usb wifi adapter D-Link DWA-120 with ndiswrapper driver
i tried to setup interne&#1077; like in this article [http://anojrs.blogspot.com/2007/07/ubuntu-creating-wireless-home-network.html](http://anojrs.blogspot.com/2007/07/ubuntu-creating-wireless-home-network.html)

all seems to be ok, mac connected to ubuntu, but i have not internet on mac...

i'm newbie in linux so i need help:)

ping 192.168.0.1 on mac gives
ping: sendto: No route to host and then
ping: sendto: Host is down

on ubuntu:
ivansid@ubuntu:~$ ping 192.168.0.2
PING 192.168.0.2 (192.168.0.2) 56(84) bytes of data.
From 192.168.0.1 icmp_seq=1 Destination Host Unreachable

my macbook options are:
IPv4 Address: 192.168.0.2
Subnet Mask: 255.255.255.0
Router: 192.168.0.1

ubuntu ifconfig and iwconfig:
```

ivansid@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1a:4d:48:0c:c0  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:219 Base address:0x6000 

eth1      Link encap:Ethernet  HWaddr 00:14:78:04:2a:c1  
          inet addr:90.188.229.9  Bcast:90.188.229.255  Mask:255.255.255.0
          inet6 addr: fe80::214:78ff:fe04:2ac1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:31661 errors:0 dropped:0 overruns:0 frame:0
          TX packets:29922 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:31173130 (29.7 MB)  TX bytes:3244378 (3.0 MB)
          Interrupt:21 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2086 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2086 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:105192 (102.7 KB)  TX bytes:105192 (102.7 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1b:11:b4:b8:e5  
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:11ff:feb4:b8e5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1909 errors:0 dropped:0 overruns:0 frame:0
          TX packets:65 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:118676 (115.8 KB)  TX bytes:7294 (7.1 KB)

ivansid@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"ubuntu"  
          Mode:Ad-Hoc  Frequency:2.437 GHz  Cell: 8E:B2:37:B4:B8:25   
          Bit Rate=54 Mb/s   
          Power Management:off
          Link Quality:92/100  Signal level:-37 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

---

### Post by nixscripter on 2008-05-05
It appears both machines think they have IP addresses, but which interface to send the data down might be in question. On ubuntu run ```
route
``` and on the mac run ```
route get 192.168.97.01
``` and post the output.

Also, make sure to use code tags on the output so the forum doesn't mess with the formatting.

---

### Post by iv_s on 2008-05-05
ubuntu:
```

ivansid@ubuntu:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     0      0        0 wlan0
90.188.230.0    *               255.255.255.0   U     0      0        0 eth1
link-local      *               255.255.0.0     U     1000   0        0 eth1
default         90-188-230-178. 0.0.0.0         UG    0      0        0 eth1

```

mac:
```

ivan-sidorovs-macbook:~ ivansidorov$ route get 192.168.97.01
   route to: 192.168.97.1
destination: default
       mask: default
    gateway: 192.168.0.1
  interface: en1
      flags: <UP,GATEWAY,DONE,STATIC,PRCLONING>
 recvpipe  sendpipe  ssthresh  rtt,msec    rttvar  hopcount      mtu     expire
       0         0         0         0         0         0      1500         0 

```

---

### Post by nixscripter on 2008-05-06
Er, oops, typo. I meant route get 192.168.**0**.1, but I think you will get the same answer. I was looking for the lines about "gateway" and "interface".

Well, it looks like the packets are being sent down the interface. So, we must conclude that for some reason, the Ubuntu machine is dropping them. I would guess this based on the second ping message (if you send more packets, it repeats, right?) "host is down".

Please dump your routing tables on the Ubuntu machine: ```
sudo iptables -L
``` to make sure the rules look okay.

---

### Post by iv_s on 2008-05-06
my ubuntu iptables:
```

ivansid@ubuntu:~$ sudo iptables -L
Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
LOG        all  --  127.0.0.0/8          anywhere            LOG level warning 
DROP       all  --  127.0.0.0/8          anywhere            
ACCEPT     all  --  anywhere             255.255.255.255     
ACCEPT     all  --  192.168.0.0/24       anywhere            
ACCEPT    !tcp  --  anywhere             BASE-ADDRESS.MCAST.NET/4 
LOG        all  --  192.168.0.0/24       anywhere            LOG level warning 
DROP       all  --  192.168.0.0/24       anywhere            
ACCEPT     all  --  anywhere             255.255.255.255     
ACCEPT     all  --  anywhere             90-188-228-226.pppoe.irtel.ru 
ACCEPT     all  --  anywhere             90-188-228-255.pppoe.irtel.ru 
DROP       all  --  anywhere             ALL-SYSTEMS.MCAST.NET 
LOG        all  --  anywhere             anywhere            LOG level warning 
DROP       all  --  anywhere             anywhere            

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ACCEPT     all  --  192.168.0.0/24       anywhere            
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
LOG        all  --  anywhere             192.168.0.0/24      LOG level warning 
DROP       all  --  anywhere             192.168.0.0/24      
DROP       all  --  anywhere             ALL-SYSTEMS.MCAST.NET 
LOG        all  --  anywhere             anywhere            LOG level warning 
DROP       all  --  anywhere             anywhere            

Chain OUTPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             255.255.255.255     
ACCEPT     all  --  anywhere             192.168.0.0/24      
ACCEPT    !tcp  --  anywhere             BASE-ADDRESS.MCAST.NET/4 
LOG        all  --  anywhere             192.168.0.0/24      LOG level warning 
DROP       all  --  anywhere             192.168.0.0/24      
ACCEPT     all  --  anywhere             255.255.255.255     
ACCEPT     all  --  90-188-228-226.pppoe.irtel.ru  anywhere            
ACCEPT     all  --  90-188-228-255.pppoe.irtel.ru  anywhere            
DROP       all  --  anywhere             ALL-SYSTEMS.MCAST.NET 
LOG        all  --  anywhere             anywhere            LOG level warning 
DROP       all  --  anywhere             anywhere            

```
and when i reboot ubuntu, my wifi adapter disappear...
i should start ndisgtk, uninstall driver and then install it again
after it i should do all this commands again:
ifconfig wlan0 192.168.0.1
iptables -t nat -A POSTROUTING -o eth1 -j MASQUERADE 
etc...
how to do it automatically?

---

### Post by nixscripter on 2008-05-07
Looking at this, the FORWARD chain seems to ACCEPT the packets as it should. Now could you please post the PRE and POST ROUTING chains: ```
sudo iptables -t nat -L
``` This will make sure that the masquerading is being set up properly.

As to your question, I might suggest writing an init script which runs at startup to save and restore the settings for iptables. Someone has adapted the handy script that comes with Gentoo [here]("http://ubuntuforums.org/showthread.php?t=57111")

Hope this helps.

---

### Post by iv_s on 2008-05-08
```

ivansid@ubuntu:~$ sudo iptables -t nat -L
Chain PREROUTING (policy ACCEPT)
target     prot opt source               destination         

Chain POSTROUTING (policy ACCEPT)
target     prot opt source               destination         
MASQUERADE  all  --  192.168.0.0/24       anywhere            
MASQUERADE  all  --  anywhere             anywhere            

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

```

Why this problem with wifi connection appear? I didn't change anything, just installed ubuntu and tried to setup internet... Maybe something wrong with version 8.04?

And about that script, it's too hard to me... I'll better try to do it myself:)

---

### Post by nixscripter on 2008-05-08
Try getting rid of that second MASQUERADE rule. It doesn't seem right to me: ```
sudo iptables -t nat -D POSTROUTING 2
``` If it still doesn't work, you can put it back with ```
sudo iptables -t nat -A POSTROUTING -j MASQUERADE
``` (I think).

---

### Post by iv_s on 2008-05-08
I tried, nothing changed...

---

### Post by nixscripter on 2008-05-08
I notice there are some LOG rules. Does /var/log/messages have any packets in it? The PREROUTING chain might cause masquerading to make the packets look odd, and thus not match some of the rules in FORWARD.

---

