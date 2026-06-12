---
title: "network connected, but no internet :("
date: 2007-03-16
forum: Networking &amp; Wireless
---

### Post by nandasunu on 2007-03-16
I am attepting to connect an old computer with ubuntu 6.10 onto the internet. The machine is about 5 yrs old and was never used for internet access.

I plugged in the ethernet cable and network manager connected it, but I have no internet access still. I tired pinging google.com and no response.

The connection works fine on my laptop (I'm using it right now)

any ideas? could the ethernet card be faulty?

---

### Post by msaied on 2007-03-16
did you configure the DNS?
system->administration->networking->dns tap

---

### Post by lukew on 2007-03-16
> **nandasunu said:**
> I am attepting to connect an old computer with ubuntu 6.10 onto the internet. The machine is about 5 yrs old and was never used for internet access.

I plugged in the ethernet cable and network manager connected it, but I have no internet access still. I tired pinging google.com and no response.

The connection works fine on my laptop (I'm using it right now)

any ideas? could the ethernet card be faulty?

what can and cant you ping.

Can you ping the router?

Can you ping external ip addresses

Can you bing [www.bbc.co.uk?](www.bbc.co.uk?)

Luke

---

### Post by nandasunu on 2007-03-16
> **msaied said:**
> did you configure the DNS?
system->administration->networking->dns tap

I didn't configure that, I am quite useless at these kind of things. The DNS section is empty, how do I configure it?

---

### Post by msaied on 2007-03-16
if you have another  machine connected to the same network . type in the terminal:
cat /etc/resolv.conf 
it will show you the primary and secondary dns.

on a windows machine open a command prompt and type :
ipconfig /all

on the last line of the output you'll fiend the DNS

---

### Post by nandasunu on 2007-03-16
> **msaied said:**
> if you have another  machine connected to the same network . type in the terminal:
cat /etc/resolv.conf 
it will show you the primary and secondary dns.

on a windows machine open a command prompt and type :
ipconfig /all

on the last line of the output you'll fiend the DNS

Thanks for the advice, I typed in the numbers I got from my laptop, but it is still not working :(

In regard to the ping, I don't know how to ping the router etc. but a ping to bbc.co.uk or google.com doesn't get any response, it says that the address can not be found.

---

### Post by msaied on 2007-03-16
can you post the result of  ifconfig  command from the old machine? you can change some IPs for security.

---

### Post by nandasunu on 2007-03-16
here is the ifconfig from the old (not working) computer:

```
kisori@loka:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0C:76:1D:3C:1C  
          inet addr:169.254.228.246  Bcast:169.254.255.255  Mask:255.255.0.0
          inet6 addr: fe80::20c:76ff:fe1d:3c1c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:3006 (2.9 KiB)
          Interrupt:185 Base address:0xb800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

```

and for comparison, here it is from my working laptop:

```
nanda@vrindavana:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0F:B0:45:78:03  
          inet addr:82.3.156.59  Bcast:255.255.255.255  Mask:255.255.252.0
          inet6 addr: fe80::20f:b0ff:fe45:7803/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:30209 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19419 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:40105560 (38.2 MiB)  TX bytes:1657404 (1.5 MiB)
          Interrupt:185 Base address:0xe000 

eth1      Link encap:Ethernet  HWaddr 00:90:4B:B6:8C:75  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:225 Memory:e8100000-e8102000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)
```

---

