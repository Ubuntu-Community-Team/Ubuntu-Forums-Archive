---
title: "Slow internet - Some page not loading at all"
date: 2007-10-31
forum: Networking &amp; Wireless
---

### Post by ikus060 on 2007-10-31
I install Gustyon my laptop (thinkpad T43) and I experience some problem to surf on the web.

The problem is not every where. On the univercity network it's work without a problem. But, at my home it's an other thing. Some page like the ubuntu forum or iGoogle are just not loading. Firefox just spin and nothing append. The same page can be load on other network. To be sure that firefox is not the problem I try with Opera and the problem is the same.

I also do some test with a virtual machine using VMWare server that I ues every day. The VM is a Windows guest and the network are bridge to eth0. The VM work very well on both network (at home and at Univercity).

The same problem appen with the Gusty Ubuntu LiveCD

Before I post on the forum I googlt it and I found some solution like disabling ipv6 by editing /etc/modprob.d/aliases. I modify /etc/hosts to remove any reference to ipv6.

Thank for helping me.

---

### Post by mpokrywka on 2007-10-31
There is probably some problem with your connection/configuration of network at home - you didn't mention your home connection type but there may be for example MTU problem if you are using pppoe or pptp. Or maybe you misconfigured DNS servers...
Open Terminal and try:
```
ping -c 1 64.233.167.99
```
If you got reply then "internet" is somehow reachable...

then try:
```
ping -c 1 google.com
```
If you got reply then DNS is configured properly...

If above tests are positive, but "web" cannot be opened then it could be that MTU problem, but some info about your connection type is required.

---

### Post by wieman01 on 2007-10-31
Disable IPV6:

[http://ubuntuforums.org/showthread.php?t=87798]("http://ubuntuforums.org/showthread.php?t=87798")

---

### Post by ikus060 on 2007-10-31
mpokrywka -> Thank for your reply. Has I mention in my first post, I run a virtual machine ( a Windows XP pro guest) on Ubuntu and the network in this virtual machine work very well and it's use the same interface (eth0) to connecto to internet. According to this fact I don't think the problem is at the hardware level.

To answer your question : I can ping every adress (ip or DNS) and I receive the response in 16ms. I think it's could be interesting to mention that I have 6 others computers at my "home" (every one runing Windows XP). Every thing are connect with a switch (Intel express 510T). I don't have a very good knowlegd of TCP/IP protocol but if the switch have any thing to do to support ipv6 I'm sure that it don't support it (it's to old).

wieman01-> First, your link are not the good one the title of this post are "What do the pictures and titles mean??? Here's where you can find out about the beans" There nothing to do about ipv6. But submit to good one and i will try to disable ipv6 according to your information. I think that I already disable it. If I do a "ip a"
```
1: lo: <LOOPBACK,UP> mtu 16436 qdisc noqueue 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
2: eth0: <BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast qlen 1000
    link/ether 00:0c:29:20:65:db brd ff:ff:ff:ff:ff:ff
    inet 192.168.1.20/24 brd 192.168.1.255 scope global eth0
```
"ipconfig" :
```
eth0      Link encap:Ethernet  HWaddr 00:0C:29:20:65:DB  
          inet addr:192.168.1.20  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:66834715 errors:25 dropped:33 overruns:0 frame:0
          TX packets:64312709 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4203932368 (3.9 GiB)  TX bytes:1224609108 (1.1 GiB)
          Interrupt:177 Base address:0x1400 
```

---

### Post by wieman01 on 2007-10-31
Oops... edited the post. Should be the right link now. Sorry.

---

### Post by airbornemist6 on 2007-10-31
If you want some additional speed, you can also try switching to a private DNS server, my choice suggestions are:
4.2.2.1
4.2.2.3

---

### Post by mpokrywka on 2007-10-31
So, another os sending packets from your machine works without problems?
There was some incompatibility with linux TCP sack implementation and some buggy routers (maybe yours or your ISP's), try:
echo 0 > /proc/sys/net/ipv4/tcp_sack

If this cures your problem add following line to /etc/sysctl.conf
net.ipv4.tcp_sack = 0

EDIT:
err, sorry that was tcp window scaling, see [http://lwn.net/Articles/92727/](http://lwn.net/Articles/92727/)
echo 0 > /proc/sys/net/ipv4/tcp_default_win_scale
and
net.ipv4.tcp_default_win_scale = 0

BUT try both settings and maybe one of these will fix your problem

---

### Post by ikus060 on 2007-11-01
mpokrywka -> I can't execute the command "echo 0 > /proc/sys/net/ipv4/tcp_sack" because root user don't have permission on it. I try to change it via "chmod +w" and I receive "Operation not permitted". 
So I  add this two line in the /etc/sysctl.conf file.
```
net.ipv4.tcp_sack = 0
net.ipv4.tcp_default_win_scale = 0

```
and reboot. There is not change.

I think we are in the good way.

airbornemist6 -> Thank for helping me, be DNS are not the problem. Using dig A google.com or any other DNS name are resolve in 72 msec.


I disable ipv6 like there doing in this post (
[http://ubuntuforums.org/showthread.php?t=87798](http://ubuntuforums.org/showthread.php?t=87798)) and when I do "ip a" to list all ip adress. eth0 have a  inet6 adress. So I remove all the change don in /etc/modprobe.d/aliases and add blacklist ipv6 in /etc/modeprobe.b/blacklist. This way ipv6 seams really disable. When I do "ip a" eth0 just got inet adress.

---

### Post by drf_av on 2007-11-01
Same problem here... I can ping anything but firefox doesn't load anything. Note that in Feisty network worked flawlessly.

---

### Post by wieman01 on 2007-11-01
Depending on what browser you use you need to disable IPV6 there as well. Firefox has such an option on the config page.

---

### Post by ikus060 on 2007-11-01
wieman01 -> I already disable ipv6 in firefox by setting to "false" the variable "network.dns.ipv6" in the configuration page "about:config". Also to be sure firefox is not the problem I try with Opera and same page not loading. ?? weird !

I know a tool named tcpflow and I try something this morning using this tool. tcpflow save every data that are transfert via tcp protocol for a specific port. I execute tcpflow over port 80 when I try to load this page [http://www.ifolder.com/index.php/Main_Page](http://www.ifolder.com/index.php/Main_Page). I find out that file are incomplete. For example the CSS file end with an open {. and html are not ended with </html>.

I try 4 other web page and it's the same thing
[http://www.flickr.com/photos/chemist/1811471244/](http://www.flickr.com/photos/chemist/1811471244/)
[http://lea-linux.org/cached/index/Accueil.html](http://lea-linux.org/cached/index/Accueil.html)
[https://help.ubuntu.com/community/SeamlessVirtualization](https://help.ubuntu.com/community/SeamlessVirtualization)
[https://help.ubuntu.com/community/](https://help.ubuntu.com/community/)


I try every page with wget some work other not.
Working  with wget
[http://www.flickr.com/photos/chemist/1811471244/](http://www.flickr.com/photos/chemist/1811471244/)
[https://help.ubuntu.com/community/SeamlessVirtualization](https://help.ubuntu.com/community/SeamlessVirtualization)
[https://help.ubuntu.com/community/](https://help.ubuntu.com/community/)
Not working
[http://lea-linux.org/cached/index/Accueil.html](http://lea-linux.org/cached/index/Accueil.html)
[http://www.ifolder.com/index.php/Main_Page](http://www.ifolder.com/index.php/Main_Page)

I'm really confused !

---

### Post by wieman01 on 2007-11-01
ikus06:

The last thing I can offer is the DNS setting (which was suggested a little earlier). Replace your current DNS with an "open" one and see if it gets any faster. Go here for instance:

[http://www.opendns.com/how/dns/turning-names-into-numbers]("http://www.opendns.com/how/dns/turning-names-into-numbers")

---

### Post by ikus060 on 2007-11-01
Like I said in other post, it's not a DNS problem. I receive good information when I use dig and I still persist that the problem are not present when I use the Edgy Live CD but are present when I use the Gusty gibbon Live CD. I'm sure it's a software issue.

This comments present the same symptom.
[https://bugs.launchpad.net/ubuntu/+bug/155393/comments/32](https://bugs.launchpad.net/ubuntu/+bug/155393/comments/32)

---

### Post by ikus060 on 2007-11-01
To be sure I try with OpenDNS and nothing change.

---

### Post by jamouneau on 2007-11-01
ikus060,

try this

sudo gedit /etc/sysctl.conf

scroll down to the bottom of the file through #Tweaks for faster broadband..

and change the following parameters to 0: (they are already in the list and you only need to change from "1" to "0")

net.ipv4.tcp_sack = 0
net.ipv4.tcp_window_scaling = 0

save file, reboot 

see if that changes things

mpokrywka was on the right track but I think "net.ipv4.tcp_default_win_scale" was the old reference.

---

### Post by ikus060 on 2007-11-02
jamouneau -> I modify my sysctl.conf file. And it's work. Thanks for your help.

---

### Post by ikus060 on 2007-11-02
To fix the problem of ever I update the firmware of my router. There is a fix for TCP Window scaling.

---

