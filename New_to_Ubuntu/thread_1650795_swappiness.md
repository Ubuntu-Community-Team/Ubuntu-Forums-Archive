---
title: "swappiness???"
date: 2010-12-22
forum: New to Ubuntu
---

### Post by Johnny420 on 2010-12-22
I am a NooB and I wanted my system to run a little better so I started doing research on virtual memory...lol and found out that in the linux world VM is called swap partitions and I understand the concept but some of the terms I am not understanding 
swappiness??

And how do I go about setting up the swap partition?

---

### Post by Elfy on 2010-12-22
When you install and assuming you let the installer create partitions it will create swap as it goes. No intervention required.

If you have already installed 

```
free -m
```

will show you the swap you have.

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)
[https://help.ubuntu.com/community/SwapFaq#What%20is%20swappiness%20and%20how%20do%20I%20change%20it?](https://help.ubuntu.com/community/SwapFaq#What%20is%20swappiness%20and%20how%20do%20I%20change%20it?)

---

### Post by NightwishFan on 2010-12-22
Generally the swappiness value will have little impact. Con Kolivas (who is a reputable kernel hacker) states that a value of 0 will have the only benefit to desktop workloads. My own research leads me to believe that a value of 100 would be better, though I go by Con's suggestions and use a value of 0.

The link above ([https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)) will show you how to set swappiness.

---

### Post by Grenage on 2010-12-22
[QUOTE=some_site]    * swappiness can have a value of between 0 and 100
    * swappiness=0 tells the kernel to avoid swapping processes out of physical memory for as long as possible
    * swappiness=100 tells the kernel to aggressively swap processes out of physical memory and move them to swap cache
[/QUOTE]

There we go.

---

### Post by NightwishFan on 2010-12-22
I should add the advantages of both, to my knowledge. A swappiness of 0 will be good for "responsiveness". It will keep processes in ram, and thus you will not notice the lag as programs are swapped back in. Generally all programs reside in RAM anyway since systems have in the GB of RAM today. Con Kolivas (a much smarter man than me I am sure) recommends this setting.

A swappiness of 100 will cause idle programs to be swapped out of RAM way more often, but on most workloads it will not happen anyway. If something essential is swapped out you may or may not notice delay as it is swapped back in. The system will make better use of memory as cache, so certain tasks will be faster. I recommend this setting because generally what it does swap, will be for the greater good and you will find tasks finish faster.

There will probably not be much difference between the two in practice, and if you are worried at all about the system "feeling fast" use a setting of 0. I do on all of my workstations. (I use 100 on servers).

---

### Post by cchhrriiss121212 on 2010-12-22
You should try out a package called preload, it automatically remembers what programs you use the most and loads them into RAM for quicker startup times. I saw an article on it a while back and the benchmarks show that it can shave of up to 10 secs from boot times.

---

### Post by Johnny420 on 2010-12-22
Thanx to all and I understand now that swappiness determines how often my system moves info into swap and I will mess with this until I feel my machines does what its told.
 I also learned about Con Kolivas and I am amazed that that guy has the time to do all the kick *** stuff he has done. I must be Lazy

---

### Post by mykes on 2010-12-29
I run a vBulletin based WWW site that has served 10's of millions of pages over the past couple of years.

The server is running Ubuntu server version (x64).  It has 16G of RAM and two quad core xeon CPUs and RAID 1 15,000 RPM Raptor drives.

One of the first things I did when setting up the server was to completely disable swap.  Ubuntu (and other operating systems) do not necessarily swap only when there is a need for physical memory and it's all in use by idle applications.

IMO, having swap is ok for a workstation, because you may want to run some application that needs all your real memory and then some (like video editing or working with large graphic images).  But on a server, it's always good to avoid going to disk whenever possible.

My experience with this server swap strategy has been outstanding.  The server has had uptimes over 450 days two times, and the only reason I ever had to reboot it was when the hosting provider forced us to change the IP addresses on our servers.

Whether it's good to not reboot servers for 450 days is a different subject to consider.  On one hand, the server has provided robust 24/7/365 reliability for the site's users.  On the other, the kernel was last updated when we had to change those IPs.  Current uptime on that server is 328 days.

---

### Post by Johnny420 on 2010-12-30
I am not marking this thread solved because I think its interesting how many opinions there are on the matter
I appreciate all of your help and the info is good I have set my swappiness to 20 for now.

---

### Post by Elfy on 2010-12-30
Question's been answered - thread set at solved.

---

