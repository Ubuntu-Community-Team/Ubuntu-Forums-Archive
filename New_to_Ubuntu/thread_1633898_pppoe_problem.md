---
title: "pppoe problem"
date: 2010-11-29
forum: New to Ubuntu
---

### Post by BlindSqaure on 2010-11-29
Hey all,

I installed Ubuntu and used sudo pppoeconf to make ppp connection.
It worked. I restarted and its gone!!

I reinstalled Ubuntu and same story.

i tried sudo pon dsl-provider .. nothings working

i can see my ip address by ifconfig ppp0 but ping returns error.

one interesting thing i noticed is .. my mask in Ubuntu is 255.255.255.255

but in windows it is 255.255.252.0

is this creating the problem?

any help is deeply appreciated.

Cheers

---

### Post by newbuntuxx on 2010-11-29
Are you sure you were looking at your subnet mask and not at your Broadcast? If the answer is yes, then that is certainly your problem.

A subnet mask simply tells network devices which part of the ip address is the network address and which part is the host. A subnet mask of 32 bits (255.255.255.255) says that the ip address is really the network address! So, any packets you try to send using that information won't be routed.

try this: 
ifconfig ppp0 netmask 255.255.252.0

let me know if it works.

---

### Post by newbuntuxx on 2010-11-29
Also, if it doesn't work, paste the following:

```
ifconfig
```

And run:

```
sudo tcpdump -n -i ppp0 | tee tcpdump.txt
```


Let it run for a while. It will capture network traffic. Upload the file tcpdump.txt which will be created in the directory that you were in (most likely your home director ~)

---

### Post by BlindSqaure on 2010-11-30
Pasting results as you said .. and pasting something which i think could be important

C:\Documents and Settings\Quark>ipconfig /all

Windows IP Configuration

        Host Name . . . . . . . . . . . . : iit-f5b7b99a41c
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Hybrid
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No
        DNS Suffix Search List. . . . . . : rolahola.local

Ethernet adapter Wireless Network Connection:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : Broadcom 802.11g Network Adapter
        Physical Address. . . . . . . . . : 00-25-56-BC-B7-8A
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        Autoconfiguration IP Address. . . : 169.254.119.9
        Subnet Mask . . . . . . . . . . . : 255.255.0.0
        Default Gateway . . . . . . . . . :

Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . : rolahola.local
        Description . . . . . . . . . . . : Broadcom NetLink (TM) Fast Ethernet
        Physical Address. . . . . . . . . : 00-26-22-0B-39-29
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        IP Address. . . . . . . . . . . . : 172.20.67.166
        Subnet Mask . . . . . . . . . . . : 255.255.252.0
        Default Gateway . . . . . . . . . :
        DHCP Server . . . . . . . . . . . : 172.20.64.4
        DNS Servers . . . . . . . . . . . : 172.20.64.4
        NetBIOS over Tcpip. . . . . . . . : Disabled
        Lease Obtained. . . . . . . . . . : Tuesday, November 30, 2010 1:44:37 A
M
        Lease Expires . . . . . . . . . . : Wednesday, December 01, 2010 1:44:37
 AM

PPP adapter Connection to TUdelft-FTTD at DePoort1:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : WAN (PPP/SLIP) Interface
        Physical Address. . . . . . . . . : 00-53-45-00-00-00
        Dhcp Enabled. . . . . . . . . . . : No
        IP Address. . . . . . . . . . . . : 145.94.5.163
        Subnet Mask . . . . . . . . . . . : 255.255.255.255
        Default Gateway . . . . . . . . . : 145.94.5.163
        NetBIOS over Tcpip. . . . . . . . : Disabled






Now linux output

ifconfig
eth0      Link encap:Ethernet  HWaddr 00:26:22:0b:39:29  
          inet6 addr: fe80::226:22ff:fe0b:3929/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:322 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:37148 (37.1 KB)  TX bytes:1112 (1.1 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:145.94.5.163  P-t-P:145.94.1.0  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:30 (30.0 B)  TX bytes:30 (30.0 B)








sudo dhclient eth0

Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/eth0/00:26:22:0b:39:29
Sending on   LPF/eth0/00:26:22:0b:39:29
Sending on   Socket/fallback
DHCPREQUEST of 172.20.65.6 on eth0 to 255.255.255.255 port 67
DHCPACK of 172.20.65.6 from 172.20.64.4
bound to 172.20.65.6 -- renewal in 41853 seconds.




I hope you can figure out the problem.

Thanks


I will upload the txt file you said . Forgot to copy :P

---

### Post by BlindSqaure on 2010-11-30
uploading the file

---

### Post by dineshs on 2010-11-30
In ubuntu versions having Network manager installed, there can be a problem with pppoeconf.Pl see the link below
[http://ubuntuforums.org/showpost.php?p=9611450&postcount=2](http://ubuntuforums.org/showpost.php?p=9611450&postcount=2)
Please try STEP-I alone then reboot.See if pon dsl-provider works.
(You can also try the alternate method explained in STEP-III)

---

### Post by BlindSqaure on 2010-12-03
Hey Dinesh,

i tried it.

I think i am able to connect to internet. But not access it.


I used a manual fr pppoeconf... may be this is helpful..

i need linux fr some project work..

pls check if something can be done...


//

Change the line (probably somewhere at the end of the file; assuming the network interface is 
eth0): 
 plugin rp-pppoe.so eth0 
to: 
 plugin rp-pppoe.so rp_pppoe_service TUdelft-FTTD rp_pppoe_ac DePoort eth0

---

### Post by dineshs on 2010-12-03
Can you ping 4.2.2.1?please post results of```
ping -c5 4.2.2.1
```and```
cat /etc/resolv.conf
```

---

### Post by BlindSqaure on 2010-12-03
----------------------------------------------------------
ping -c5 4.2.2.1

quark@quark-laptop:~$ ping -c5 4.2.2.1
PING 4.2.2.1 (4.2.2.1) 56(84) bytes of data.
64 bytes from 4.2.2.1: icmp_seq=1 ttl=247 time=9.45 ms
64 bytes from 4.2.2.1: icmp_seq=2 ttl=247 time=9.38 ms
64 bytes from 4.2.2.1: icmp_seq=3 ttl=247 time=9.44 ms
64 bytes from 4.2.2.1: icmp_seq=4 ttl=247 time=9.24 ms
64 bytes from 4.2.2.1: icmp_seq=5 ttl=247 time=9.53 ms

--- 4.2.2.1 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4005ms
rtt min/avg/max/mdev = 9.241/9.410/9.532/0.130 ms
quark@quark-laptop:~$ 
----------------------------------------------------------

cat /etc/resolv.conf

# Generated by NetworkManager

-------------------------------------------------------

---

### Post by dineshs on 2010-12-04
> cat /etc/resolv.conf
# Generated by NetworkManager

You are connected to the net and the problem is with DNS.Please try this
Run```
sudo gedit /etc/resolv.conf
```Edit the file so that it contains
```
# Generated by NetworkManager
nameserver 4.2.2.1
nameserver 8.8.8.8
```
Save and close the file
Now see if pages are loading 
Note:Instead of 4.2.2.1 and 8.8.8.8 you can use the DNS given by your ISP.

---

### Post by BlindSqaure on 2010-12-04
Replying from UBUNTU ..

Thanks forum

Thanks Dinesh

( i will bug u again fr wifi .. but fr nw i need to work :P)

---

