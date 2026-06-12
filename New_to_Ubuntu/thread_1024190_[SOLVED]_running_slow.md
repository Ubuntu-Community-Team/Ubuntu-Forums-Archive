---
title: "[SOLVED] running slow"
date: 2008-12-28
forum: New to Ubuntu
---

### Post by shadow120 on 2008-12-28
ok i installed ubuntu 8.04 a couple months ago on a dell dimension 2400 with a pentium 4 processor and 2g of memory and it seems to be running slower than it should be.  i dont know much about this os and any help would be appreciated thanks

---

### Post by nhasian on 2008-12-28
one thing you can do is go to System->Preferences->Searching and indexing and disable indexing.

you can see what applications are taking up your cpu & ram with the command *top* in a terminal.  q to quit top and k to kill a process.

---

### Post by shadow120 on 2008-12-28
what dose disabling indexing do and i ran top in the terminal but what do i do now


allen@allen-desktop:~$ top

top - 19:48:48 up  7:03,  2 users,  load average: 0.28, 0.28, 0.15
Tasks: 112 total,   2 running, 110 sleeping,   0 stopped,   0 zombie
Cpu(s):  7.3%us,  1.7%sy,  0.0%ni, 91.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   2074216k total,  1642304k used,   431912k free,    45392k buffers
Swap:  6072528k total,        0k used,  6072528k free,  1175352k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 5254 root      20   0  254m  35m 8408 S  4.0  1.7  44:10.26 /usr/bin/X :0 -br -
 5951 allen     20   0  193m 103m  24m S  1.3  5.1  50:57.96 /usr/lib/firefox-3.
 5744 allen     20   0 24352  17m 7080 S  0.7  0.8   2:35.90 /usr/bin/compiz.rea
12001 allen     20   0 74752  20m  11m R  0.7  1.0   0:00.78 gnome-terminal     
    1 root      20   0  2844 1692  544 S  0.0  0.1   0:01.48 /sbin/init         
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 [kthreadd]         
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 [migration/0]      
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.02 [ksoftirqd/0]      
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 [watchdog/0]       
    6 root      15  -5     0    0    0 S  0.0  0.0   0:00.22 [events/0]         
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 [khelper]          
   41 root      15  -5     0    0    0 S  0.0  0.0   0:00.18 [kblockd/0]        
   44 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 [kacpid]           
   45 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 [kacpi_notify]     
  112 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 [kseriod]          
  146 root      20   0     0    0    0 S  0.0  0.0   0:00.00 [pdflush]          
  147 root      20   0     0    0    0 S  0.0  0.0   0:01.06 [pdflush]

---

### Post by shadow120 on 2008-12-29
bump

---

### Post by nhasian on 2008-12-30
your load average looks good, and i dont see any processes taking up a lot of cpu time.  what is slow in your system?

have you tried going to System->Preferences->Appearance and setting the Visual Effects to None?

---

### Post by Michael.Godawski on 2008-12-30
hi, 

I also do not see anything suspicious.

Perhaps you can use one if these guides:


[LIST]
[*][http://www.chinwong.com/index.php?/site/article/ubuntu_speed_up_tips/](http://www.chinwong.com/index.php?/site/article/ubuntu_speed_up_tips/)
[*][http://news.softpedia.com/news/Optimize-Ubuntu-8-04-for-Speed-86405.shtml](http://news.softpedia.com/news/Optimize-Ubuntu-8-04-for-Speed-86405.shtml)
[/LIST]

---

### Post by gjoellee on 2008-12-30
> **Michael.Godawski said:**
> hi, 

Perhaps you can use one if these guides:

[LIST]
[*][http://news.softpedia.com/news/Optimize-Ubuntu-8-04-for-Speed-86405.shtml](http://news.softpedia.com/news/Optimize-Ubuntu-8-04-for-Speed-86405.shtml)
[/LIST]


You should use ```
gksu
``` and not ```
sudo
```, it is safer!

---

### Post by shadow120 on 2008-12-30
it lags sometimes when i have a few things running thanks for the help and the links this is a great community and has helped me alot

---

