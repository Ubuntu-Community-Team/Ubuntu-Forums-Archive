---
title: "[Help]Can't share my Internet Connection"
date: 2009-11-23
forum: New to Ubuntu
---

### Post by Madel on 2009-11-23
Im dual booting Windows XP and Ubuntu.
Wanted to try Ubuntu in my gateway computer. And wanted to share the internet connection to my workstations in LAN.

I followed the guide:  [https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)
But still my internet connection is not accesible by the computers in my LAN.
I even try to install Firestarter to do the job using the wizard, still my internet connection will not be shared. Firestarter just blocks the connection from my LAN computers. It shows in events that it is blocked. It already took me 1 and a half hour figuring this out myself. Doing the guide in help.ubuntu.com again and again, probably i already mess some of my config files doing that again and again, yet, i still can't share the connection.

What else should i do?

result of ifconfig
```

eth0      Link encap:Ethernet  HWaddr 00:12:17:5c:01:92  
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::212:17ff:fe5c:192/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2370 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2155 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:165340 (165.3 KB)  TX bytes:123386 (123.3 KB)
          Interrupt:21 Base address:0xe800 

eth1      Link encap:Ethernet  HWaddr 00:1a:92:62:bd:d8  
          inet addr:192.168.254.253  Bcast:192.168.255.255  Mask:255.255.224.0
          inet6 addr: fe80::21a:92ff:fe62:bdd8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:70929 errors:0 dropped:0 overruns:0 frame:0
          TX packets:68633 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:88610811 (88.6 MB)  TX bytes:7350076 (7.3 MB)
          Interrupt:23 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1622 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1622 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:120958 (120.9 KB)  TX bytes:120958 (120.9 KB)


```

---

### Post by ukripper on 2009-11-23
post output of this command:
```
sudo iptables -L
```

---

### Post by Madel on 2009-11-23
> **ukripper said:**
> post output of this command:
```
sudo iptables -L
```

Here's the output:

```

Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  ns3.smartbro.net     anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  ns3.smartbro.net     anywhere            
ACCEPT     tcp  --  ns1.smartbro.net     anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  ns1.smartbro.net     anywhere            
ACCEPT     tcp  --  ns2.smartbro.net     anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  ns2.smartbro.net     anywhere            
ACCEPT     tcp  --  ns4.smartbro.net     anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  dns4.smartbro.net    anywhere            
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5 
DROP       all  --  anywhere             255.255.255.255     
DROP       all  --  anywhere             192.168.255.255     
DROP       all  --  BASE-ADDRESS.MCAST.NET/8  anywhere            
DROP       all  --  anywhere             BASE-ADDRESS.MCAST.NET/8 
DROP       all  --  255.255.255.255      anywhere            
DROP       all  --  anywhere             0.0.0.0             
DROP       all  --  anywhere             anywhere            state INVALID 
LSI        all  -f  anywhere             anywhere            limit: avg 10/min burst 5 
INBOUND    all  --  anywhere             anywhere            
INBOUND    all  --  anywhere             192.168.254.253     
INBOUND    all  --  anywhere             192.168.0.1         
INBOUND    all  --  anywhere             192.168.255.255     
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Input' 

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5 
TCPMSS     tcp  --  anywhere             anywhere            tcp flags:SYN,RST/SYN TCPMSS clamp to PMTU 
OUTBOUND   all  --  anywhere             anywhere            
ACCEPT     tcp  --  anywhere             192.168.224.0/19    state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             192.168.224.0/19    state RELATED,ESTABLISHED 
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Forward' 
ACCEPT     all  --  192.168.0.0/24       anywhere            ctstate NEW 
ACCEPT     all  --  anywhere             anywhere            ctstate RELATED,ESTABLISHED 
ACCEPT     all  --  192.168.0.0/24       anywhere            ctstate NEW 
ACCEPT     all  --  anywhere             anywhere            ctstate RELATED,ESTABLISHED 

Chain OUTPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  192.168.0.1          ns3.smartbro.net    tcp dpt:domain 
ACCEPT     udp  --  192.168.0.1          ns3.smartbro.net    udp dpt:domain 
ACCEPT     tcp  --  192.168.0.1          ns1.smartbro.net    tcp dpt:domain 
ACCEPT     udp  --  192.168.0.1          ns1.smartbro.net    udp dpt:domain 
ACCEPT     tcp  --  192.168.0.1          ns2.smartbro.net    tcp dpt:domain 
ACCEPT     udp  --  192.168.0.1          ns2.smartbro.net    udp dpt:domain 
ACCEPT     tcp  --  192.168.0.1          ns4.smartbro.net    tcp dpt:domain 
ACCEPT     udp  --  192.168.0.1          dns4.smartbro.net   udp dpt:domain 
ACCEPT     all  --  anywhere             anywhere            
DROP       all  --  BASE-ADDRESS.MCAST.NET/8  anywhere            
DROP       all  --  anywhere             BASE-ADDRESS.MCAST.NET/8 
DROP       all  --  255.255.255.255      anywhere            
DROP       all  --  anywhere             0.0.0.0             
DROP       all  --  anywhere             anywhere            state INVALID 
OUTBOUND   all  --  anywhere             anywhere            
OUTBOUND   all  --  anywhere             anywhere            
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Output' 

Chain INBOUND (4 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
LSI        all  --  anywhere             anywhere            

Chain LOG_FILTER (5 references)
target     prot opt source               destination         

Chain LSI (2 references)
target     prot opt source               destination         
LOG_FILTER  all  --  anywhere             anywhere            
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN 
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST 
LOG        icmp --  anywhere             anywhere            icmp echo-request limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       icmp --  anywhere             anywhere            icmp echo-request 
LOG        all  --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Inbound ' 
DROP       all  --  anywhere             anywhere            

Chain LSO (0 references)
target     prot opt source               destination         
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Outbound ' 
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable 

Chain OUTBOUND (3 references)
target     prot opt source               destination         
ACCEPT     icmp --  anywhere             anywhere            
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     all  --  anywhere             anywhere            


```

By the way, after both doesn't work, i removed Firestarter and the other application that got installed with firestarter, named "menu".

---

### Post by ukripper on 2009-11-23
Even though you removed firestarter, Iptables rules are still in place which you might have created using firestarter. You may want to flush your iptables rules and follow that guide again.

---

### Post by Madel on 2009-11-23
> **ukripper said:**
> Even though you removed firestarter, Iptables rules are still in place which you might have created using firestarter. You may want to flush your iptables rules and follow that guide again.

Actually, i installed Firestarter first. But it doesn't work.
Then, I followed that guide. Then I followed another guide in some ubuntu-geek website. Running all of those commands. Except that eth0 and eth1 which is not the same setup compared to the guides. As my eth0 is my LAN. And eth1 is my internet connection.

Btw, how do i flush my iptables? You mean, i will have to clean it? Delete it and make a new one?

How exactly can I do that?

---

### Post by ukripper on 2009-11-23
> **Madel said:**
> Actually, i installed Firestarter first. But 

Btw, how do i flush my iptables? You mean, i will have to clean it? Delete it and make a new one?

How exactly can I do that?

[http://www.cyberciti.biz/tips/linux-iptables-how-to-flush-all-rules.html](http://www.cyberciti.biz/tips/linux-iptables-how-to-flush-all-rules.html)

[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)


This will help you to reset your iptables.

---

### Post by Madel on 2009-11-23
Done flushing wiht "sudo iptables -F". And followed the guide again. Still internet connection is still not shared.
Here's the new output if doing "sudo iptables -L":

```

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     all  --  192.168.0.0/24       anywhere            ctstate NEW 
ACCEPT     all  --  anywhere             anywhere            ctstate RELATED,ESTABLISHED 

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination        

```

---

### Post by ukripper on 2009-11-23
have you done this bit?

> Enable routing

    * Configure the gateway for routing between two interfaces by enabling IP forwarding: 

sudo sh -c "echo 1 > /proc/sys/net/ipv4/ip_forward"

    * Edit /etc/sysctl.conf and add these lines: 

net.ipv4.conf.default.forwarding=1
net.ipv4.conf.all.forwarding=1

---

### Post by Madel on 2009-11-23
Yup i've done that part.

I flush iptables again then follow the guide here:
[http://www.ubuntugeek.com/sharing-internet-connection-in-ubuntu.html](http://www.ubuntugeek.com/sharing-internet-connection-in-ubuntu.html)

Execpt the part of installing ipmasq. It won't install with error:
Package ipmasq is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package ipmasq has no installation candidate


And then, it worked. It shares the internet connection.

But after I restarted Ubuntu, internet connection sharing is gone. It's not sharing again.
Do I have to enter all those commands everytime I boot ubuntu?
Is there any way to make the sharing permanent?

---

### Post by ukripper on 2009-11-23
The link i posted before, read the below quotes:

> Saving iptables

If you were to reboot your machine right now, your iptables configuration would disappear. Rather than type this each time you reboot, however, you can save the configuration, and have it start up automatically. To save the configuration, you can use iptables-save and iptables-restore.



Save your firewall rules to a file

# iptables-save >/etc/iptables.rules

read that guide in the link again [https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

you need to save your iptables before  reboot. 

Check your iptables again. and make sure you save all the iptables rule (iptables -L) you made changes to before reboot.

```
iptables-save >/etc/iptables.rules
```

---

### Post by Madel on 2009-11-23
Owh. Sorry. I didn't get on that part as I was following different guide.

Thank you very much for your help. It's fully working now. It shares internet connection even after rebooting my computer. It even shares the internet even before I log-in in gnome.

Problem solved.

---

### Post by Iowan on 2009-11-23
> **Madel said:**
> Problem solved.
Consider marking it as such (Thread Tools) :p

---

### Post by Madel on 2009-11-23
Thanks. I didn't know it exist. Thanks for the tip. :)

---

