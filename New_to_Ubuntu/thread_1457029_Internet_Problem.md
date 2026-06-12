---
title: "Internet Problem"
date: 2010-04-18
forum: New to Ubuntu
---

### Post by Experimental on 2010-04-18
Hi everyone ,

I installed ubuntu yesterday(I also have xp in this computer) and everything was just fine . This morning i tried to log on to windows and windows was working fine too . It was connecting to internet . But when I get back to ubuntu I couldn't connect to internet . My zoom adsl modem's LAN light never stopped blinking. In windows it's fine . I'm using ubuntu 9.10 . 

And also one other problem is when I first tried to install ubuntu my external hdd was plugged in so it installed it there .  When I realized i plugged it out and install ubuntu again . Now my external has 117 gb of ntsf and rest of it is ext2 or something. How can I change it all back to change it back to ntsf without losing my datas.

Thank You

---

### Post by gmxgeek on 2010-04-18
What is the output of ```
ifconfig
``` in terminal?

---

### Post by Experimental on 2010-04-18
eth0      Link encap:Ethernet  HWaddr 00:24:1d:0e:88:65  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:27 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by Experimental on 2010-04-18
up

---

### Post by Experimental on 2010-04-19
come on guys no answer

---

### Post by Drenriza on 2010-04-19
to me, with a quick look. It looks like you need to give your eth0 an ip-address and mask
 
```
ifconfig eth0 (ip address) (mask) up
```
example
```
ifconfig eth0 192.168.0.0 255.255.255.0 up
```

---

### Post by Zintha on 2010-04-19
I had a problem like this, got fixed by the suggestions made.

Had to put in that command everytime I booted up.
Eventually fixed itself when it updated some drivers relevant to it.

It was a hassle but I didn't understand enough how to permanently fix the problem!

---

### Post by dineshs on 2010-04-19
> **Zintha said:**
>  but I didn't understand enough how to permanently fix the problem!

You can configure network manager with static IP
[https://help.ubuntu.com/community/NetworkManager0.7](https://help.ubuntu.com/community/NetworkManager0.7)

---

