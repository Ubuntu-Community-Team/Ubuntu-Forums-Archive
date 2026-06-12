---
title: "internet troubles"
date: 2009-04-10
forum: New to Ubuntu
---

### Post by fknyeah on 2009-04-10
I feel like I have the strangest problems on Ubuntu.  So I went to visit a friend this past weekend at Wesleyan University.  While there I made a point to transfer some music from his external to mine.  Since the window says its going to take a couple hours I leave the computer to do its work.  When I come back the transfer has gone okay, but now essentially any application that uses the Internet has some sort of problem.  Songbird doesn't run.  Pidgin doesn't run.  Firefox, while it works, is much slower.  Firefox also won't let me bookmark and has seemingly lost all of the bookmarks I had saved.  In addition multimedia doesn't work in firefox, such as youtube and vimeo.

Please Help.  I've never even heard of something like this as a problem.

---

### Post by superprash2003 on 2009-04-11
well , the problems you have are common, but the cause of the problem is pretty weird.. just transferring some files shouldnt cause such problems.. have you tried rebooting.. i would have told you to try switching to opendns servers.. but if you didnt have these problems earlier.. its pretty weird.. you could try though.. post an output of** ifconfig **too

---

### Post by fknyeah on 2009-04-11
sam@honus-wagner:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1c:23:87:dd:d3  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr 00:1c:26:06:8d:4d  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:26ff:fe06:8d4d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2795 errors:0 dropped:0 overruns:0 frame:2037
          TX packets:3091 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2211747 (2.2 MB)  TX bytes:669183 (669.1 KB)
          Interrupt:17 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:80 errors:0 dropped:0 overruns:0 frame:0
          TX packets:80 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6384 (6.3 KB)  TX bytes:6384 (6.3 KB)

---

### Post by fknyeah on 2009-04-11
bump x2

---

### Post by fknyeah on 2009-04-12
> **fknyeah said:**
> bump x2

please help

nothing's worked.

---

### Post by fknyeah on 2009-04-13
Tried to update, but I got this error:

Failed to run /usr/sbin/synaptic '--hide-main-window' '--non-interactive' '--parent-window-id' '52428803' '--update-at-startup' as user root.

Unable to copy the user's Xauthorization file.

---

### Post by Procuro on 2009-04-14
Do you think something could have happened to the filesystem when you were writing to your machine? Did the power or something fail? I don't see how random applications would stop working after that. 

I'd hate to suggest reinstalling ubuntu, but it sounds like something bad happened if all of these apps are failing to work properly now. My guess is something else caused the problem and you noticed it when you were transfering files. Good luck.

---

### Post by fknyeah on 2009-04-14
I'm pretty sure I'm resolved to just reinstalling ubuntu. This isn't worth it anymore and it doesn't seem like anyone can really help.

---

