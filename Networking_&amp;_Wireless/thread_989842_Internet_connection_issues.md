---
title: "Internet connection issues"
date: 2008-11-22
forum: Networking &amp; Wireless
---

### Post by Ralex1098 on 2008-11-22
Alrighty, so I decided I wanted to set up a home network sort of deal on an older computer and installed xubuntu on a machine. The install went fine (Ibex) and afterwards, I realize that I can't connect to the internet.

I followed the cables and so far, I have an ethernet cable running from my computer to a router, which then runs to the cable box. I can't figure out why Xubuntu isn't picking up the internet signal.

Any ideas?

---

### Post by SpaceTeddy on 2008-11-22
lots of ideas - but they are too many to acctually write them down here. 

but, could you answer a few questions ?

1.) is your cable modem a router or a modem
2.) what is the ip-address of a working internet machine
3.) did you ever have more than one computer on the internet at the same time
4.) what is the output of the following commands

```
cat /etc/network/interfaces
cat /etc/resolv.conf
ifconfig -a
sudo iptables -L

```

just general debugging information...

---

### Post by Ralex1098 on 2008-11-22
Okay, after playing around a bit, this command allows me to get onto the internet.

```
sudo dhclient eth0
```

However, everytime I reboot I don't instantly get access again. It's strange.

To answer your questions.

1) It's a cable modem.
2)An IP is 72.230.185.90
3)Yes, we've had multiple Windows and Linux machines on the internet at the same time
4)

```

scott@scott-desktop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

scott@scott-desktop:~$ cat  /etc/resolv.conf
nameserver 192.168.1.1

scott@scott-desktop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:0c:f1:79:0e:7c  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:f1ff:fe79:e7c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1679 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1287 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2216883 (2.2 MB)  TX bytes:146656 (146.6 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:36 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1800 (1.8 KB)  TX bytes:1800 (1.8 KB)

pan0      Link encap:Ethernet  HWaddr fe:10:d4:32:0a:f4  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

scott@scott-desktop:~$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination   

```

What do you think?

---

