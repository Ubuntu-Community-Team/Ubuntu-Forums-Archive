---
title: "Ubuntu unable to ping XP"
date: 2009-06-05
forum: New to Ubuntu
---

### Post by pratiks19 on 2009-06-05
I am using a crossover connection from Ubuntu to Win XP.

The ifconfig output:

```

eth0      Link encap:Ethernet  HWaddr 00:1e:68:6b:95:6d  
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:68ff:fe6b:956d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:148 errors:0 dropped:0 overruns:0 frame:0
          TX packets:253 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:17759 (17.7 KB)  TX bytes:34146 (34.1 KB)
          Interrupt:219 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:394 errors:0 dropped:0 overruns:0 frame:0
          TX packets:394 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:25880 (25.8 KB)  TX bytes:25880 (25.8 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:117.98.19.221  P-t-P:192.168.100.101  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:11348 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14309 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:6515047 (6.5 MB)  TX bytes:7270301 (7.2 MB)

wlan0     Link encap:Ethernet  HWaddr 00:1f:3c:5c:4d:7e  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-1F-3C-5C-4D-7E-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

[B]The XP machine has the ip address: 192.168.0.2.
Subnet mask: 255.255.255.0
[/B]

[B]The firewall on XP machine is disabled.
Also the "ICMP allow incoming echo request is checked"
[/B]

I am not able to understand why my Ubuntu cannot ping XP, whereas XP pings Ubuntu.

Please help me with this.

---

### Post by DBrocks on 2009-06-05
What exactly is the error message from ubuntu?
Also, post the output of 
>  
sudo iptables -L


---

### Post by pratiks19 on 2009-06-06
the following are the outputs:

> pratik@pratik-laptop:~$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
pratik@pratik-laptop:~$ sudo ping 192.168.0.2
PING 192.168.0.2 (192.168.0.2) 56(84) bytes of data.
^C
--- 192.168.0.2 ping statistics ---
10 packets transmitted, 0 received, 100% packet loss, time 9044ms



Ubuntu does not show any errors...

I guess the Network Manager is causing problem...

---

### Post by pratiks19 on 2009-06-06
According to the following post, I am headed in the right direction:

[http://ubuntuforums.org/showpost.php?p=6123143&postcount=2]("http://ubuntuforums.org/showpost.php?p=6123143&postcount=2")

All I need is to setup samba.

---

### Post by The Cog on 2009-06-06
> **pratiks19 said:**
> According to the following post, I am headed in the right direction:

[http://ubuntuforums.org/showpost.php?p=6123143&postcount=2]("http://ubuntuforums.org/showpost.php?p=6123143&postcount=2")

All I need is to setup samba.

If you can't ping it, then I very much doubt if samba will work. I suggest you don't waste your time with samba until you have got pings working. Not that I have any idea what the problem is.

Perhaps see if the arp entries are right. In Linux it's **arp -an** but I don't know whtat the windows version is.

---

### Post by pratiks19 on 2009-06-07
what must the arp entries be like ?
I have absolutely no idea about arp..

---

### Post by pratiks19 on 2009-06-07
Ok.. i put **arp -an** and got the MAC address of the windows machine...
also suddenly.. it was pingable out of nowhere....

anyways I've got what I wanted to do, put them as my signature.

Thanks for the great support to all of you..

---

### Post by The Cog on 2009-06-07
The ARP (Address Resolution Protocol) table provides you with a lookup from IP address to MAC address. I was wondering if the ARP table had the correct MAC address in it, and you confirm that it does.

---

