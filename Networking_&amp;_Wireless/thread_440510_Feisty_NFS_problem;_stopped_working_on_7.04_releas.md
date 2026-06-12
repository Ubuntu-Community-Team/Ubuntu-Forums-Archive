---
title: "Feisty NFS problem; stopped working on 7.04 release version?"
date: 2007-05-11
forum: Networking &amp; Wireless
---

### Post by krosenvold on 2007-05-11
I have my file server in the basement running an "old" debian x64. The server is:
Linux base26 2.6.17-2-amd64 #1 SMP Wed Sep 13 17:49:33 CEST 2006 x86_64 GNU/Linux

I have three clients connecting to this server Two of them were at the time clean-installed with the 7.04 HERD pre-release CD's. They have since been upgraded through update manager and work perfectly.

Inspired by this success I tried to upgrade the last pc to 7.04 from 6.10. NFS stopped working.
Then I reinstalled (clean - from the alternate cd) 7.04 and ran
sudo apt-get install portmap nfs-common

And setup a simple fstab:
192.168.1.5:/mnt/d1  /mnt/d1  nfs   defaults 0 0
192.168.1.5:/mnt/d2  /mnt/d2  nfs   defaults 0 0

When I try to access the device using for instance 
ls /mnt/d1

It just hangs and hangs for a looong time. I get these messages in the syslog:
kernel: [54558.075598] nfs: server 192.168.1.5 not responding, still trying

Anyone have any suggestions as to what is happening ? I basically only upgraded the clients here.

Kristian

---

### Post by krosenvold on 2007-05-15
Nice talking to myself :-) Upgrading server to something slightly more recent solved the trick.

---

### Post by krosenvold on 2007-05-16
I was being optimistic: The problem remains, now with a pure 7.04 system. NFS works fine for a little while, and then it breaks totally and I need to reboot client to actually get it working again. No messages in syslog.

---

### Post by jrev on 2007-05-25
Hi,

My problem with feisty 07.4 and NFS :

If I install feisty on an NFS client and the eth0 plug is in I got a perturbated boot.  (I tried with one feisty DVD and one CD with the sme result  

When i want to open a folder the first time it takes 48 seconds instead of 4 normally

If I install withour the plug in everything is normal, but as soon as I install Internet sharing the problem commes again.

Otherwise internet sharing and files sharing are OK

---

