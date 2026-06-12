---
title: "Feisty intermittent internet connection - same problem in 2 diferent computers"
date: 2007-03-26
forum: Networking &amp; Wireless
---

### Post by casainho on 2007-03-26
Hello!! I am using Ubuntu since 2 years ago :-)

Since I made a new install to Feisty, I get intermittent internet connection :-(

All looks ok, but in aMule I get errors like "lost connection", It connects to servers but a few seconds after It disconnects and It always reconnecting.
The same with Gaim...
The same with youtube videos... they just download an initial part and I can't never see all the movies :-(
The same with downloads on firefox, in big files, always can't get to end :-(

Well, I have two different computers with the same problem, and the same computers worked great with 6.10 - even one of them have M$ Windows XP and internet is perfect...

Thanks in advance.

Jorge Pinto from Portugal
[www.Casainho.net](www.Casainho.net)

---

### Post by johntabularasa on 2007-04-23
I just installed 7.04 on two computers and have similar issues both worked fine with Edgy Eft.  Now visiting some websites is fine, but others like [http://www.netbeans.org/](http://www.netbeans.org/) will not load.  The throughput also fluctuates from 400b/s to 90kbs?

Using the same networking gear cables and switches other computers with Windows and MacOS X work fine.  I am not sure what the problem is but it seems like a pretty serious one that I am having too :(

[   20.675536] eth0: RTL8169s/8110s at 0xf8826c00, 00:40:f4:f0:18:f9, IRQ 20

---

### Post by anu815 on 2007-04-25
This might help! I was having similar problems and found this article on performance tuning;

[http://tvease.net/wiki/index.php?tit...untu_for_speed](http://tvease.net/wiki/index.php?tit...untu_for_speed)

sudo gedit /etc/sysctl.conf

* Then again, scroll to the bottom and just add these lines to it.

net.core.rmem_default = 524288
net.core.rmem_max = 524288
net.core.wmem_default = 524288
net.core.wmem_max = 524288
net.ipv4.tcp_wmem = 4096 87380 524288
net.ipv4.tcp_rmem = 4096 87380 524288
net.ipv4.tcp_mem = 524288 524288 524288
net.ipv4.tcp_rfc1337 = 1
net.ipv4.ip_no_pmtu_disc = 0
net.ipv4.tcp_sack = 1
net.ipv4.tcp_fack = 1
net.ipv4.tcp_window_scaling = 1
net.ipv4.tcp_timestamps = 1
net.ipv4.tcp_ecn = 0
net.ipv4.route.flush = 1

* You have to reset your sysctl for these to take effect.

sudo sysctl -p

---

### Post by johntabularasa on 2007-04-25
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/59331](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/59331) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I found in my case that this was caused by the tcp_window_scaling sysctl variable.  Doing the following fixed the issue for me.

# sudo vim /etc/sysctl.conf

and adding the following line to the configuration file.

net.ipv4.tcp_window_scaling=0

Then reboot the computer.

The following URL's give more details about this particular problem.  I am not sure if this is the same problem as the original poster but may help.

[https://bugs.launchpad.net/ubuntu/+bug/107195](https://bugs.launchpad.net/ubuntu/+bug/107195)
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/89160](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/89160)
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/59331](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/59331)
[http://kerneltrap.org/node/6723](http://kerneltrap.org/node/6723)
[http://lwn.net/Articles/92727/](http://lwn.net/Articles/92727/)

IMHO, it seems Ubuntu should disable window scaling since it obviously causes problems for a number of people.  The fact that this option is enabled by default seems like ideology winning out over usability.  I would expect this from the kernel folks but not the Ubuntu team ;)

---

### Post by ocdude on 2007-04-25
I'm still having problems with this even after having followed the instructions on this thread and the launchpad bug. I don't know, but would rolling back to the 2.6.17-generic kernel be a solution? It's really annoying me as I lose all communication through GAIM every single time my DCHP lease is renewed (every 24 minutes). I can't extend the lease as I don't have access to the router (university network).

---

### Post by ocdude on 2007-04-29
Bump to see if anyone has found a solution. I ended up reverting to the 2.6.17-generic kernel and I haven't experienced the problem since, but I really wish I knew what was going on.

---

### Post by stu_edgar on 2007-04-30
OCdude,
I am having same problem and can't really roll back to 2.6.17 as my X seems to break when i try an older kernel!
This has not been entered as bug yet on launchpad as far as I can see  because I don't think anyone has found the source.
I'm not techy enough but if you are we'd appreciate some troubleshooting.
Seems like a killer fault to me!
Stu

---

### Post by ocdude on 2007-05-01
well, it seems to have fixed it for a while, but AIM disconnected randomly again. I'm not sure how much of it is the new kernel and how much of it is my campus' crummy network now, though. Yahoo! seems to work fine for some reason, however.

I'm not very savvy in the ways of the linux network stack myself, so I'm really just going off of assumptions and random guesses here.

---

### Post by kvonb on 2007-05-01
Try lowering your MTU to something like 1412, see if it makes a difference.

I think you have to add it to the /etc/network/interfaces file.

---

### Post by ocdude on 2007-05-01
I've changed it. I'll post back if it dies again, or if in two days it's still functioning.

---

### Post by krull_etc on 2007-05-02
I'm having similar issues.  I upgraded to Feisty, and now my Internet only works occasionally.   Sometimes I get lucky and can get online at boot up, but normally nothing works.  I've tried turning off the tcp window scaling and changing the MTU t  1412, but neither made a difference.  I can always get online if I use the old Edgy LiveCD, though

---

### Post by Mischa on 2007-10-24
to fix it back to original working packed sizes do the following as root: (sudo su -)

vi /etc/sysctl.conf

add the following two lines

net.ipv4.tcp_wmem = 4096 16384 131072
net.ipv4.tcp_rmem = 4096 87380 174760

sysctl -p

see [http://inodes.org/blog/2006/09/06/tc...d-kernel-2617/]("http://inodes.org/blog/2006/09/06/tcp-window-scaling-and-kernel-2617/") for an excellent explanation

---

