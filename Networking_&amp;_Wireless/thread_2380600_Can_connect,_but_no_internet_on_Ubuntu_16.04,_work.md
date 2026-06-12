---
title: "Can connect, but no internet on Ubuntu 16.04, works fine on windows 10"
date: 2017-12-19
forum: Networking &amp; Wireless
---

### Post by juaninsantiago on 2017-12-19
Hi!

I am having problems with my internet connection on Ubuntu 16.04. I can connect to the wireless network but i have no access to internet, 
In my laptop i also have windows 10 and it can connect and browse perfectly fine.
I noticed that i can ping IPv6 addresses but not IPv4:

```
output ping Google DNS

luka@luka-Inspiron-3458:~$ ping 8.8.8.8


PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.


^C


--- 8.8.8.8 ping statistics ---


173 packets transmitted, 0 received, 100% packet loss, time 173374ms






output ping6 Google DNS


luka@luka-Inspiron-3458:~$ ping6 2001:4860:4860::8888


PING 2001:4860:4860::8888(2001:4860:4860::8888) 56 data bytes


64 bytes from 2001:4860:4860::8888: icmp_seq=1 ttl=48 time=286 ms


64 bytes from 2001:4860:4860::8888: icmp_seq=2 ttl=48 time=60.6 ms


64 bytes from 2001:4860:4860::8888: icmp_seq=3 ttl=48 time=61.3 ms


64 bytes from 2001:4860:4860::8888: icmp_seq=4 ttl=48 time=60.8 ms


64 bytes from 2001:4860:4860::8888: icmp_seq=5 ttl=48 time=60.9 ms


64 bytes from 2001:4860:4860::8888: icmp_seq=6 ttl=48 time=60.2 ms


64 bytes from 2001:4860:4860::8888: icmp_seq=7 ttl=48 time=59.5 ms


64 bytes from 2001:4860:4860::8888: icmp_seq=8 ttl=48 time=60.8 ms


^C


--- 2001:4860:4860::8888 ping statistics ---


8 packets transmitted, 8 received, 0% packet loss, time 7010ms


rtt min/avg/max/mdev = 59.573/88.846/286.406/74.672 ms



```

But it seems that i can't resolve any hostname with IPv6 (neither with IPv4)

```
trying to resolve hostname

luka@luka-Inspiron-3458:~$ ping6 google.com


unknown host


luka@luka-Inspiron-3458:~$ ping6 ipv6.google.com


unknown host


luka@luka-Inspiron-3458:~$ ping6 localhost


unknown host



```

I can normally ping localhost though

This is NOT a new install of Ubuntu, it happened when I try to connect in a new network (I am unable to test if i can connect to other networks rigth now)

Let me know if you need me to run any command.

Thank you for your help.

---

### Post by praseodym on 2017-12-19
Please run the wireless-script from the sticky thread and show the outputs here

---

### Post by juaninsantiago on 2017-12-19
I followed the instructions on how to run it with no internet, and the result is just a text file with

########## wireless info START ##########

nothing more :/

---

### Post by praseodym on 2017-12-19
So, show the outputs of these commands
```

lspci -nnk | grep -iA2 net
lsusb
lsmod
ifconfig -a
iwconfig
route -n
cat /etc/resolv.conf
```
Do we talk LAN or wireless?

---

### Post by juaninsantiago on 2017-12-19
Figured out the answer.
I ended up disabling IPv4 and using public DNS64 servers.
If it isn't against any rule i'm going to leave the link to my post on another forum where this was solved
[https://superuser.com/questions/1278597/i-can-ping-ipv6-but-not-ipv4?noredirect=1#comment1888081_1278597](https://superuser.com/questions/1278597/i-can-ping-ipv6-but-not-ipv4?noredirect=1#comment1888081_1278597)

---

