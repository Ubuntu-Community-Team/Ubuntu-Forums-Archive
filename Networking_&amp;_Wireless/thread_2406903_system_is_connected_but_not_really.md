---
title: "system is connected but not really"
date: 2018-11-27
forum: Networking &amp; Wireless
---

### Post by jgw on 2018-11-27
This is an ongoing problem and mystery.  My network is connected.  System settings tell me so and so does the drop downs under my network icons on the top bar.  When this happens I open a terminal and try to ping yahoo.com (or any other known place).  What happens is, exactly, nothing!  all I see is my command and nothing else.  My solution is to stop/disconnect the network and then bring it back up.  I have absolutely no idea why my machine is behaving this way.  

I am currently using a wireless connection but the same thing happens when I have a wired connection

```
greg@greg-down:~$ ip route
default via 192.168.0.1 dev enp2s0 
default via 192.168.0.1 dev wlx1c4bd6ded3b0 proto dhcp metric 600 
169.254.0.0/16 dev enp2s0 scope link metric 1000 
192.168.0.0/24 dev enp2s0 proto kernel scope link src 192.168.0.5 
192.168.0.0/24 dev wlx1c4bd6ded3b0 proto kernel scope link src 192.168.0.50 metric 600 
192.168.0.1 dev enp2s0 scope link 
205.171.2.65 via 192.168.0.1 dev enp2s0 

greg@greg-down:~$ iwconfig
wlx1c4bd6ded3b0  IEEE 802.11bgn  ESSID:"TP-LINK_7496C2"  Nickname:"rtl_wifi"
          Mode:Managed  Frequency:2.432 GHz  Access Point: 60:E3:27:74:96:C2   
          Bit Rate:150 Mb/s   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=100/100  Signal level=100/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
enp2s0    no wireless extensions.
lo        no wireless extensions.
```

I have also tried sudo service network-manager restart



Would appreciate any thoughts on this one as its driving my nuts.

Thank you..............

---

### Post by mitesh.agrwl on 2018-11-27
> **jgw said:**
> This is an ongoing problem and mystery.  My network is connected.  System settings tell me so and so does the drop downs under my network icons on the top bar.  When this happens I open a terminal and try to ping yahoo.com (or any other known place).  What happens is, exactly, nothing!  all I see is my command and nothing else.  My solution is to stop/disconnect the network and then bring it back up.  I have absolutely no idea why my machine is behaving this way.

Would appreciate any thoughts on this one as its driving my nuts.

Thank you..............


Post the output of following commands:

```
$ ip a
$  ping -f -c 5 -i 0.5 8.8.8.8
$  ping -f -c 5 -i 0.5 www.yahoo.com
 
```

---

### Post by jgw on 2018-11-27
Thanks for the reply!!

Sorry to be so long.  I am doing this on one machine and then posting to a memory stick and moving this stuff here.3

```
greg@greg-down:~$ ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp2s0: <BROADCAST,MULTICAST,DYNAMIC,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether e0:3f:49:ad:2e:0a brd ff:ff:ff:ff:ff:ff
3: wlx1c4bd6ded3b0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 1c:4b:d6:de:d3:b0 brd ff:ff:ff:ff:ff:ff
    inet 192.168.0.50/24 brd 192.168.0.255 scope global dynamic noprefixroute wlx1c4bd6ded3b0
       valid_lft 86372sec preferred_lft 86372sec
    inet6 fe80::1e4b:d6ff:fede:d3b0/64 scope link 
       valid_lft forever preferred_lft forever

greg@greg-down:~$ ping -f -c 5 -i 0.5 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.2
--- 8.8.8.8 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 2005ms
rtt min/avg/max/mdev = 27.678/31.145/38.491/4.307 ms, ipg/ewma 501.364/29.497 ms

greg@greg-down:~$ ping -f -c 5 -i 0.5 [www.yahoo.com\](www.yahoo.com\)
ping: [www.yahoo.com:](www.yahoo.com:) Name or service not known

for the heck of it I did some plain pings and got:

greg@greg-down:~$ ping 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=122 time=27.1 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=122 time=27.1 ms
64 bytes from 8.8.8.8: icmp_seq=3 ttl=122 time=26.5 ms
^C
--- 8.8.8.8 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 26.582/26.944/27.130/0.318 ms

greg@greg-down:~$ ping yahoo.com
ping: yahoo.com: Name or service not known
```

I should also mention that I was able to ping my router at 192.168.0.1

---

### Post by wildmanne39 on 2018-11-27
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by jgw on 2018-11-27
I am a bit confused about code tags thing.  What I posted was not code but command lines followed by the results of same.  Are these considered code? 

Oh, I was using the quick reply.

---

### Post by oldos2er on 2018-11-27
The forum's vbulletin software uses the word "code" when it refers to commands and their output. Bit of a misnomer.

---

### Post by jgw on 2018-11-27
I may have fixed something.  I was reading and somebody suggested changing the nameserver in /etc/resolv.conf.  My problem is that I think this is temporary.  I will see.  the nameserver was set to 127.0.0.53   When I tried to go there it couldn't connect.  Have no idea where that came from.  I changed it to google nameserver 8.8.8.8 and it worked!

---

### Post by The Cog on 2018-11-27
> **jgw said:**
> I am a bit confused about code tags thing.  What I posted was not code but command lines followed by the results of same.  Are these considered code? 
For this forum, yes. The code tags make the text lay out with fixed width font so all the columns line up properly. So it looks like it would in the terminal.

---

### Post by jgw on 2018-11-27
got it - about the code thing and will try to remember

I am going to mark this one as solved and then start a new one about the nameserver thing

thanks for all the help!

---

