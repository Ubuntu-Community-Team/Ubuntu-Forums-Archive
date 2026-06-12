---
title: "Not able to access Internet.... but wired network connected."
date: 2008-03-17
forum: Networking &amp; Wireless
---

### Post by pschandra on 2008-03-17
Hai,

I have a dual boot system Ubuntu and Vista. If I am in Vista.... Network working perfectly fine. But not able access internet in Ubuntu. 

Interesting things as follows:

1. Wired Network connected via DHCP
2. I can able to ping google.com (0% packet loss)
3. But not able to connect net through firefox. Also, I can not able to login to servers using  "ssh" command.

Please help me in this regard...................

Following are outputs to different commands: 

---------------------------------
[I][FONT="Courier New"]$ ifconfig 

eth0      Link encap:Ethernet  HWaddr 00:1A:6B:3A:98:4F   
          inet addr:134.96.187.124  Bcast:134.96.187.255  Mask:255.255.255.0 
          inet6 addr: fe80::21a:6bff:fe3a:984f/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:2086 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:79 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:100  
          RX bytes:176607 (172.4 KB)  TX bytes:7663 (7.4 KB) 
          Base address:0x1840 Memory:fe200000-fe220000  
 
lo        Link encap:Local Loopback   
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:199 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:199 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0  
          RX bytes:74113 (72.3 KB)  TX bytes:74113 (72.3 KB) 
 
wlan0     Link encap:Ethernet  HWaddr 00:13:E8:9A:48:D9   
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b) 
 
wmaster0  Link encap:UNSPEC  HWaddr 00-13-E8-9A-48-D9-00-00-00-00-00-00-00-00-00-00   
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)[/FONT][/I]

----------------------------

[I][FONT="Courier New"]$  ping google.com

PING google.com (72.14.207.99) 56(84) bytes of data. 
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=1 ttl=242 time=115 ms 
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=2 ttl=242 time=114 ms 
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=3 ttl=242 time=113 ms 
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=4 ttl=242 time=114 ms 
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=5 ttl=242 time=113 ms 
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=6 ttl=242 time=113 ms 
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=7 ttl=242 time=116 ms 
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=8 ttl=242 time=113 ms 
 
--- google.com ping statistics --- 
8 packets transmitted, 8 received, 0% packet loss, time 7000ms 
rtt min/avg/max/mdev = 113.725/114.471/116.143/0.947 ms[/FONT][/I]

------------------------------------

[I][FONT="Courier New"]
$ cat /etc/network/interfaces

auto lo 
iface lo inet loopback[/FONT][/I]

--------------------------------------

[I][FONT="Courier New"]$ lshw -C network

 *-network                
       description: Ethernet interface 
       product: 82566MM Gigabit Network Connection 
       vendor: Intel Corporation 
       physical id: 19 
       bus info: pci@0000:00:19.0 
       logical name: eth0 
       version: 03 
       serial: 00:1a:6b:3a:98:4f 
       size: 100MB/s 
       capacity: 1GB/s 
       width: 32 bits 
       clock: 33MHz 
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.20-k2-NAPI duplex=full firmware=0.3-0 ip=134.96.187.124 latency=0 link=yes module=e1000 multicast=yes port=twisted pair speed=100MB/s 
  *-network 
       description: Wireless interface 
       product: PRO/Wireless 4965 AG or AGN Network Connection 
       vendor: Intel Corporation 
       physical id: 0 
       bus info: pci@0000:03:00.0 
       logical name: wmaster0 
       version: 61 
       serial: 00:13:e8:9a:48:d9 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless 
       configuration: broadcast=yes driver=iwl4965 latency=0 module=iwl4965 multicast=yes wireless=IEEE 802.11g
[/FONT][/I]
 
---------------------------------

[I][FONT="Courier New"]$ iwlist scan 

lo        Interface doesn't support scanning. 
 
eth0      Interface doesn't support scanning. 
 
wmaster0  Interface doesn't support scanning. 
 
wlan0     No scan results [/FONT][/I]

---

### Post by Arthur Archnix on 2008-03-17
what about sudo apt-get update, does that retrieve a list of packages and complete or give errros?

---

### Post by pschandra on 2008-03-17
Trying to connect to internet.... stopped at 0% 
so not able to connect to internet

---

### Post by arcktos on 2008-03-17
I got same problem. Can anybody help?(it worked on 7.04)

---

### Post by pschandra on 2008-03-17
Apt-get also not working......... bcz internet not connected.....

---

### Post by pschandra on 2008-03-18
Actually, Internet was working fine before I tried to Install VPN Client. But now, I am not able to connect internet. Can any body help me plz..........

If there is no way.... I will reinstall Ubuntu OS...... is that a good idea?

---

### Post by superprash2003 on 2008-03-18
could be a DNS Problem

---

### Post by pschandra on 2008-03-18
[I][FONT="Courier New"]$ cat  /etc/resolv.conf

search dfki.uni-sb.de
nameserver 134.96.188.22
nameserver 134.96.188.27
nameserver 134.96.188.33
[/FONT][/I]

So, It seems DNS is OK. Any other problem??????????:confused:

---

### Post by Eiríkr on 2008-03-18
What exactly do you mean by "internet not connected"?  Your [font=courier]ifconfig[/font] results clearly show that interface [font=courier]eth0[/font] has an IPv4 internet address of **134.96.187.124**, with 79 packets transmitted for 0 errors.  Moreover, your [font=courier]ping[/font] of Google was totally successful.  **You are connected.**  Is it that your browser isn't working (a different issue altogether)?

Cheers,

Eiríkr

---

### Post by arcktos on 2008-03-18
No thats weird. I got same problem. and it ******* weird.
i can ping google.com but cannot wget it on my disk not the mention about firefox using. I cannot get packages from internet. I runed ubuntu live installed ndiswrapper and so on...and its still same. got one question - WTF?

---

### Post by Eiríkr on 2008-03-18
Is there any chance you have a firewall running?  In some configurations, a firewall could be configured to lock out any TCP / UDP traffic (web connections), but allow ICMP traffic (pings) through.

---

### Post by pschandra on 2008-03-20
Hai,

I found solution for this!!!!!!!! :lolflag:

The problem is firewall is ON. when I tried to install VPN client, firewall was ON automatically. 

To STOP firewall RUN following script (with sudo) :


        IPTABLES="/sbin/iptables"

        $IPTABLES -F
        $IPTABLES -F -t nat
        $IPTABLES -F -t mangle
        $IPTABLES -X
        $IPTABLES -X -t nat
        $IPTABLES -X -t mangle

        $IPTABLES -P INPUT   ACCEPT
        $IPTABLES -P FORWARD ACCEPT
        $IPTABLES -P OUTPUT  ACCEPT   


Thats it!!!!!!!!!! my firewall Stopped. Now, I can able access internet. 
Thanks for helping anyway......... :) : ) :) :) :)

---

### Post by Arthur Archnix on 2008-03-20
It's good that you got it working, though, you should perhaps not disable the firewall completely. 

Another option is to install firestarter, which gives you a graphical user interface into iptables. Perhaps there is a simpler way of opening up the ports needed for vpn to work.

---

