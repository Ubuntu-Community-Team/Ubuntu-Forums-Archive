---
title: "Offline installaiton of linux-headers-2.6.15-23"
date: 2007-05-28
forum: Networking &amp; Wireless
---

### Post by azzid on 2007-05-28
Hi,

I'm trying to install linux-headers-2.6.15-23 on my ubuntu 6.06.
The problem really is that it's a virtual machine and suddenly it lost its network interface.

My fellow administrator told me to do:
apt-get install linux-headers-`uname -r` build-essential

problem is, it's kind of hard to get atp-get to work without internet.

I downloaded ubuntu-6.06.1-server-i386.iso and used apt-cdrom to add it to the sources list, but apt-get still won't install the linux-headers. It only says "unable to fetch some archives".

Am I using the wrong cd? or am I just doing it wrong?

Where can I find a more complete iso-image containing the linux-headers package? Or how do I compile my own? As I understand it the cd must have some index file in order to get it to work with apt-get.

---

### Post by azzid on 2007-05-28
I did'nt solve the issue above, but this [sollution]("http://www.vmware.com/community/thread.jspa?threadID=46069&tstart=0") was what I was really looking for, so I no longer need to get the offline installation working.

---

