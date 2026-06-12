---
title: "Problem with internet"
date: 2006-11-21
forum: Networking &amp; Wireless
---

### Post by frtamal on 2006-11-21
Hi all,
I just install ubuntu 6.10. after that whenever i tried to connect internet, i failed. So that, i tried to ping goole and some other website and did that successfully and colect IP of those domian (so the dns is ok). after that when i tried by those ip, i could visit web sites by firefox. but again if there is any link by name that i click from those site, firefox can't resolve those name and show me error.
for me, i use adsl... tried to use sudo pppoeconf, but after few step it show it can't find or modem may use for other pppoe operation.
so, please help me to solve this problem...

cheers:-k

---

### Post by dbott67 on 2006-11-21
Can you please post the output of the following commands:
```
ifconfig -a
```
```
route -n
```
```
cat /etc/resolv.conf
```
```
sudo iptables -L
```

Are you running a proxy server of any sort?

-Dave

---

### Post by stream303 on 2006-11-23
Pinging ok but dns bad - maybe this will help:

[http://www.ubuntuforums.org/showthread.php?t=305275](http://www.ubuntuforums.org/showthread.php?t=305275)

---

### Post by frtamal on 2006-11-24
Hi,
Here is the output of those command you sugest....
sorry for late
thanks

ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:0D:56:D1:80:DC
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:56ff:fed1:80dc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100
          RX bytes:2500 (2.4 KiB)  TX bytes:2716 (2.6 KiB)
          Base address:0xdf40 Memory:feae0000-feb00000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:500 (500.0 b)  TX bytes:500 (500.0 b)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)




route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0


cat /etc/resolv.conf

nameserver 192.168.1.1


sudo iptables -L

Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

---

### Post by trubblemaker on 2006-11-24
ugh sounds like ipv6 and firefox again. 

Two methods to fix it. 

1) add "blacklist ipv6" to /etc/modpobe.d/blacklist
   this is quickest but a little heavy handed. 
   (sudo echo "blacklist ipv6" >> /etc/modpobe.d/blacklist)

2) disable ipv6 in firefox, can't remeber exactly howto do this, it's something like about:settings and then but ip6 to false, a quick goofle on ipv6 and firefox should tell you.

[If you want to know more ]("http://ubuntuforums.org/showpost.php?p=478267&postcount=8")

could be wrong, but sounds like the issue.

---

### Post by jamesr on 2006-11-24
I would also suggest that having > cat /etc/resolv.conf

nameserver 192.168.1.1 needs to be changed to the nameserver addresses supplied by your ISP. 
These are normally supplied by your ISP or are available on the technical support home page. 
I also have a search line in the the resolv.conf file.

---

### Post by frtamal on 2006-11-28
Sorry, doesn't work these solutions....

---

### Post by jamesr on 2006-11-29
Hi,

Please output the results of following commands
```
ping 192.168.1.255
ping google.com
ping 64.233.187.99 
```

An example follows:-> ashteq@Ashteq:~$ ping google.com
PING google.com (64.233.187.99) 56(84) bytes of data.
64 bytes from 64.233.187.99: icmp_seq=1 ttl=245 time=49.4 ms
64 bytes from 64.233.187.99: icmp_seq=2 ttl=245 time=48.5 ms
64 bytes from 64.233.187.99: icmp_seq=3 ttl=245 time=91.3 ms
64 bytes from 64.233.187.99: icmp_seq=4 ttl=245 time=50.6 ms

--- google.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3011ms
rtt min/avg/max/mdev = 48.540/59.978/91.352/18.129 ms


---

