---
title: "internet very slow in gutsy (ipv6 disabled though)"
date: 2007-10-31
forum: Networking &amp; Wireless
---

### Post by snsoneee on 2007-10-31
internet is very slow in gutsy although ipv6 is disabled globally: 
```
sns@sns-desktop:~$ sudo lsmod|grep ipv6
[sudo] password for sns:
sns@sns-desktop:~$ 

```

and the dns keeps resetting to 192.168.1.248 from 10 to 10 minutes
(ive got 2 dns addresses,static ip address)
what can i do?please helpi've searched here but nothing worked so far.thanks in advance
edit: i have 2 ethernet devices:eth0, eth1..eth0 is in roaming mode because i dont use it and eth1 is the one with which i am connected to the internet

---

### Post by snsoneee on 2007-10-31
anyone?please?
i added also lines in aliases in modprobe.d
```

alias net-pf-9  x25
[B]alias net-pf-10 ipv6 off
alias net-pf-10 off
alias ipv6 off
#alias net-pf-10 ipv6[/B]
alias net-pf-11 rose

```
but there is nothing changed

---

### Post by ercork on 2007-11-02
Mine was really slow in Gutsy too. It would take about 30 - 40 seconds in firefox, opera, etc to connect to a website - once connected though the speeds would increase. I disabled IPV6 as described here:

[http://ubuntuforums.org/showthread.php?t=87798](http://ubuntuforums.org/showthread.php?t=87798)

and all was well after that. Your problem is clearly different though. Can you confirm that the same hardware (network adapter and router) works properly under a different operating system? If so then try Swiftfox. There are lots of little linux optimizations enabled by default in it and one of them might work for you. Failing that you might try disabling roaming mode in the network manager and enter the details manually?
Sorry I have nothing more concrete to offer.

---

### Post by snsoneee on 2007-11-02
yes, same hardware
do you have more info about swiftfox?

---

### Post by Iowan on 2007-11-02
Re: DNS
Have you seen [THIS]("http://ubuntuforums.org/showthread.php?t=282034&highlight=dns") one?

---

### Post by snsoneee on 2007-11-02
Iowan: i just solved my dns problem:

i had to  < sudo apt-get install resolvconf  > in terminal, then added my nameservers in /etc/network/interfaces and voila.no more dns reseting

but internet is still slow (and ipv6 disabled globally).it's a wired network

---

### Post by snsoneee on 2007-11-10
any sugestions?anyone?please

---

### Post by captain semtex on 2007-11-10
I installed Gutsy on a laptop with an internal** BCM4309** card and using the new restricted drivers it was unusably slow. (As I expected, disabling ipv6 made no difference).

I then disabled the internal wireless card card in the BIOS and plugged in a **BCM4306** external PC card and everything worked perfectly immediately... no additional configuration required.

Any suggestions on how to get my BCM4309 working with the new restricted drivers would be appreciated. (Maybe the **BCM4309** firmware needs updating but I don't know how to do that :-().

Thank you.

---

### Post by Lambert on 2007-11-10
> **snsoneee said:**
> any sugestions?anyone?please

3 things to look at.

1. 

If your network interface is eth0 then run this command (this is for a wired connection only)

```

sudo ethtool eth0

```

Post output here.

2.

Post output of this command.

```

sudo ip route

```

3.

Run this command and post output.

```

traceroute www.google.com

```

If you type in the ip address instead of domain name, do you notice a speed difference?

And one last thing, what does the contents of your /etc/resolv.conf file look like?

Read through the following bug report to see if anything helps you.

[https://bugs.launchpad.net/ubuntu/+bug/155393](https://bugs.launchpad.net/ubuntu/+bug/155393)

---

### Post by snsoneee on 2007-11-10
Lambert :


```
 snsone@snsone-desktop:~$ sudo ethtool eth1
[sudo] password for snsone:
Settings for eth1:
        Supported ports: [ TP MII ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
        Advertised auto-negotiation: Yes
        Speed: 10Mb/s
        Duplex: Half
        Port: MII
        PHYAD: 32
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: pumbg
        Wake-on: u
        Current message level: 0x00000007 (7)
        Link detected: no

```

```

snsone@snsone-desktop:~$ sudo ip route
81.196.204.176/29 dev eth1  proto kernel  scope link  src 81.196.204.181 
192.168.1.0/24 dev eth0  proto kernel  scope link  src 192.168.1.151 
169.254.0.0/16 dev eth1  scope link  metric 1000 
default via 192.168.1.1 dev eth0 
default via 81.196.204.177 dev eth1  metric 100 

```

```

snsone@snsone-desktop:~$ sudo traceroute www.google.com
traceroute to www.l.google.com (209.85.135.99), 64 hops max, 40 byte packets
 1  192.168.1.1 (192.168.1.1)  0 ms  0 ms  0 ms
 2  buh-dr51-gr24-25.rdsnet.ro (82.76.12.1)  1 ms  1 ms  1 ms
 3  172-17-205-25.rdsnet.ro (172.17.205.25)  2 ms  3 ms  4 ms
 4  bb01.bucuresti.rdsnet.ro (194.102.81.113)  5 ms  2 ms  3 ms
 5  213-154-124-61.rdsnet.ro (213.154.124.61)  34 ms  33 ms *
 6  xr01.frankfurt.rdsnet.ro (213.154.124.10)  37 ms  35 ms  38 ms
 7  de-cix10.net.google.com (80.81.192.108)  35 ms  34 ms  35 ms
 8  209.85.249.178 (209.85.249.178)  35 ms  35 ms  36 ms
 9  72.14.238.128 (72.14.238.128)  50 ms  51 ms  43 ms
10  66.249.94.85 (66.249.94.85)  42 ms  60 ms 66.249.94.83 (66.249.94.83)  51 ms
11  72.14.239.54 (72.14.239.54)  61 ms 209.85.253.26 (209.85.253.26)  54 ms 72.14.239.54 (72.14.239.54)  239 ms
12  mu-in-f99.google.com (209.85.135.99)  53 ms  44 ms  43 ms

```

and the contents of /etc/resolv.conf look like:
```

# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 193.231.236.25
nameserver 193.231.236.30

```
hope it helps...

edit: set my ip as dns you mean?

---

### Post by snsoneee on 2007-11-11
also:
```

snsone@snsone-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

```
(because some people thought i got wireless)

---

### Post by snsoneee on 2007-11-15
please help me
at this point the internet speed is way better in windows xp then ubuntu.

---

