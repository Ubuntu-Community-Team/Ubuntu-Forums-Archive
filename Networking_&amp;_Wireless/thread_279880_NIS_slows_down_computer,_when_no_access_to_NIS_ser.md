---
title: "NIS slows down computer, when no access to NIS server"
date: 2006-10-18
forum: Networking &amp; Wireless
---

### Post by Del Pede on 2006-10-18
I have a laptop with two quickswitch profiles, that i can change at boot time. One that connects to a NIS domain through wifi (eth1) and another, that configures the wired netcard (eth0) with a fixed IP, for my home network. It all works really fine. The problem is, that the upstart takes up to 5 more minutes, before users can log in. The computer is really slow, untill i disable nis, through the init script as root. 

Is there any tool og config options that can make be start/stop NIS, if i'm not connected to the NIS domain. It's really problematic, that the upstart of my laptop takes 6-7 minutes, before i can login.

Thanks in advance
Del Pede

---

