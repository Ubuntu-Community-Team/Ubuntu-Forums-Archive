---
title: "Wireless Network Card - Macbook Pro 13&quot; Retina Display"
date: 2014-10-07
forum: Networking &amp; Wireless
---

### Post by usamah2 on 2014-10-07
Hello,

I have been scavenging around so many forums and pages regarding this issue. Some provided clarity however I am still not able to solve this problem.

I have a Macbook Pro 13" Retina Display (no Ethernet cable option). I have dual booted it with Ubuntu 14.04 LTS. I can not get to make the wifi work on it. It continues to say "No Network devices available". 

From the research I have done so far I have been able to gather that I can not use b43 driver to make internet work on my mac. When executed the command "lspci -vvnn | grep 14e4" this is my output:
 

02:00.0 Multimedia controller [0480]: Broadcom Corporation Device [14e4:1570] 
    Subsystem: Broadcom Corporation Device [14e4:1570]
03:00.0 Network controller [0280]: Broadcom Corporation BCM4360 802.11ac Wireless Network Adapter [14e4:43a0] (rev 03)



Could anyone please help me with regard to getting my wireless working on my Ubuntu. I would really appreciate it alot. 
Thanks in advance!

---

### Post by Hadaka on 2014-10-07
Hi, try this..
```
sudo apt-get install bcmwl-kernel-source
sudo modprobe wl
```
thanks.

---

### Post by usamah2 on 2014-10-08
this is the output I got upon executing those lines 

ubuntu_usamah@Ubuntu:~$ sudo apt-get install bcmwl-kernel-source
[sudo] 
password for ubuntu_usamah: 
Reading package lists... Done
Building dependency tree       


Reading state information... 
Done
Package bcmwl-kernel-source is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source


E: Package 'bcmwl-kernel-source' has no installation candidate


ubuntu_usamah@Ubuntu:~$ sudo modprobe wl
modprobe: FATAL: Module wl not found.



For reference if it matters, I installed via a USB so when exploring it, I don't see any system files or drivers I could extract from there. Also prior to knowing that b43 won't work I did however did some installation of it using instructions given here on this link. [http://linuxforums.org.uk/index.php?topic=5842.msg81040;PHPSESSID=4q55jchh4hjprqf95e6g1h8dn7#msg81040](http://linuxforums.org.uk/index.php?topic=5842.msg81040;PHPSESSID=4q55jchh4hjprqf95e6g1h8dn7#msg81040)
I only managed to make it work till "[COLOR=#000000][FONT=dejavu sans mono]**sudo**[/FONT][/COLOR][COLOR=#000000][FONT=dejavu sans mono] b43-fwcutter -w /lib/firmware wl_apsta-[/FONT][/COLOR][COLOR=#40A070][FONT=dejavu sans mono]3.130.20.0[/FONT][/COLOR][COLOR=#000000][FONT=dejavu sans mono].o"

[/FONT][/COLOR]
Is there a way to get rid of it or undo the b43 so it doesn't interfere? or is that fine?

thanks

---

### Post by usamah2 on 2014-10-08
Okay so i managed to solve it! read a lot of comments around in issues similar to it.

This link was of best help [http://www.alexvictorchan.com/2013/05/01/installing-ubuntu-13-04-on-13-macbook-pro-retina-102/](http://www.alexvictorchan.com/2013/05/01/installing-ubuntu-13-04-on-13-macbook-pro-retina-102/)

The first comment on this post; if follow the sequence of depackaging the drivers in that order seemed to work for me! 
Finally have wifi on Ubuntu. yes!

---

### Post by Hadaka on 2014-10-08
Excellent !! good job! Glad you have it going
please take the time to mark your thread SOLVED
how to ->[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

