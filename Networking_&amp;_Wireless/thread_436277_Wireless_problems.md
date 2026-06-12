---
title: "Wireless problems"
date: 2007-05-07
forum: Networking &amp; Wireless
---

### Post by karmon on 2007-05-07
Well until about a week ago, I had ubuntu 5.10 installed on my dell desktop. Everything worked great, no problems with internet. What I use is my internet reciever is this xbox wireless adapter:

[http://www.amazon.com/Microsoft-R86-00001-Wireless-G-Xbox-Adapter/dp/B0000C5FMJ](http://www.amazon.com/Microsoft-R86-00001-Wireless-G-Xbox-Adapter/dp/B0000C5FMJ)

It connects through the ethernet port of my computer, and worked without any problems. No drivers needed to be installed, nothing; it just worked. So I installed ubuntu 7.04, and it says I am connected, but whenever I use firefox I get the 'could not connect to server' message. Anybody know what could be causing this?

---

### Post by chili555 on 2007-05-08
Could be a few things, but let's start with some basics. Please do these commands in a terminal and post the result:```
ifconfig eth0
ping -c3 www.google.com
ping -c3 216.239.51.99
cat /etc/resolv.conf
```For the ping commands, there is no need to post the entire result, just tell us if pings returned or not. My sixth sense says this is a DNS issue which we can fix easily.

---

### Post by karmon on 2007-05-08
Thanks for your reply. Here are my results:

```
karmon@karmon-ubuntu:~$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:C0:A8:80:EA:91  
          inet addr:192.168.1.113  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:a8ff:fe80:ea91/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:63 errors:0 dropped:0 overruns:0 frame:0
          TX packets:63 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:20284 (19.8 KiB)  TX bytes:12963 (12.6 KiB)
          Interrupt:16 Base address:0x6c00 

karmon@karmon-ubuntu:~$ ping -c3 www.google.com
ping: unknown host www.google.com

karmon@karmon-ubuntu:~$ ping -c3 216.239.51.99
connect: Network is unreachable

karmon@karmon-ubuntu:~$ cat /etc/resolv.conf
nameserver 67.69.184.208
nameserver 67.69.184.144

```

As well, I'm not sure if I have my network devices (eth0, wireless...) configured properly.

---

