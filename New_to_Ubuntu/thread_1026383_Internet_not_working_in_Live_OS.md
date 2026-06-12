---
title: "Internet not working in Live OS"
date: 2008-12-31
forum: New to Ubuntu
---

### Post by harshpkaria on 2008-12-31
The internet is not working in the LIVE version. In fact, it does not let me enter my ip address configuration.
network-admin is not installed and asks me to apt-get install it, which in turn requires internet....
Is this normal with the LIVE OS? or just a problem to me??

---

### Post by sadaruwan12 on 2008-12-31
Well no, all the live CD from ubuntu can connect to the internet. I like to know wich version you're using and is it burned fron a downloaded ISO image or you got an original CD from Ubuntu.

---

### Post by Michael.Godawski on 2008-12-31
hi,

and that is not normal. :D

Have you burnt the ISO correctly and checked for defects?
[http://godawski.oxyhost.com/downloadingubuntu.html](http://godawski.oxyhost.com/downloadingubuntu.html)

What are the specs of your machine and what version did you download?

---

### Post by qwertpie on 2009-01-01
i am haveing the same problem... i downloaded from ubuntu and have used ISO burner and the burner they recomended "infraRecorder" i think, and have made 3 diff copy's of the ubuntu 8.10 cd... on none of them have i been able to excess the internet

---

### Post by superprash2003 on 2009-01-01
go to the Terminal and type ifconfig and post output here..

---

### Post by qwertpie on 2009-01-01
> **superprash2003 said:**
> go to the Terminal and type ifconfig and post output here..


ubuntu@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1d:60:18:c8:a5  
          UP BROADCAST RUNNING MULTICAST  MTU:64  Metric:1
          RX packets:44 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6911 (6.9 KB)  TX bytes:1933 (1.9 KB)
          Interrupt:21 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:216 errors:0 dropped:0 overruns:0 frame:0
          TX packets:216 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:13536 (13.5 KB)  TX bytes:13536 (13.5 KB)

ubuntu@ubuntu:~$ sudo gedit/etc/networks/interfaces
sudo: gedit/etc/networks/interfaces: command not found

---

### Post by superprash2003 on 2009-01-02
ok.. your problem is that you arent getting an ip address.. you could try setting up static ip manually.. what is your router ip address??is it 192.168.1.1 ? or 192.168.0.1?

---

### Post by sadaruwan12 on 2009-01-02
> ok.. your problem is that you arent getting an ip address.. you could try setting up static ip manually.. what is your router ip address??is it 192.168.1.1 ? or 192.168.0.1?

Hi,

I'd a similar kind of a problem with my Ubuntu v8.10 I don't know what all other Ubuntu installations worked with my router that had the IP range 10.0.0.xx I tried every thing I know to solve this but I couldn't over come this then I found out that it was a bug in the forcedeth network driver I thought of downgrading my drivers but passed that thought 'cos it's not recommended. So I just went back to my Hardy Haron and I'm using it with out any problems up to now. And I personally recommend to use a LTS version rather than installing the latest Ubuntu release.

---

### Post by sadaruwan12 on 2009-01-02
and another thing che this thred out  [http://ubuntuforums.org/showthread.php?t=1023570]("http://ubuntuforums.org/showthread.php?t=1023570") that was posted by me when I came across this problem.

---

