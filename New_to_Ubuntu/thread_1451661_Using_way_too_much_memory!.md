---
title: "Using way too much memory!"
date: 2010-04-10
forum: New to Ubuntu
---

### Post by outleradam on 2010-04-10
It's taking forever for my computer to boot up.   

I totaled everything in the processes section of the system monitor, and it says I'm using 276ish megs of ram.  The System monitor Resources tab reports I'm using 1.2 gigs of memory.   Even shell command 'top' reports the same as system monitor. 

Where is this difference coming from?    How can I remove this extra junk being loaded at startup?  What is loading it?

---

### Post by buddyd16 on 2010-04-10
how much of the 1.2 gigs is labled as cached?

There should be a line when you run ```
free -m
``` that looks like ```
+/- cache and buffer
``` I believe that is the line you want to be looking at.

---

### Post by nemilar on 2010-04-10
Can you post the output of 

```
free -m
```

As comment #2 alludes to, Linux will "consume" most available memory (memory not used by running processes) for I/O cache; if a process needs memory, then it will give up this cache-allocated RAM.

---

### Post by no2498 on 2010-04-11
correct me if im wrong
cache is for places i have been 
things in java that change all the time
things i have done
pics i have looked at or loaded

this is all fine if you do the same thing over and over again
i set mine to 50kb
and i clean it out as flash and java keep changing 
and i do not load the same pics all the time
pages change every minute 

just my way of thinking

---

### Post by Joeb454 on 2010-04-11
> **no2498 said:**
> correct me if im wrong
cache is for places i have been 
things in java that change all the time
things i have done
pics i have looked at or loaded

this is all fine if you do the same thing over and over again
i set mine to 50kb
and i clean it out as flash and java keep changing 
and i do not load the same pics all the time
pages change every minute 

just my way of thinking

I'm taking a guess that you're referring to firefox cache or something here, which is entirely different. Running *free -m* in a terminal will give a result similar to below.

```
~$ free -m
             total       used       free     shared    buffers     cached
Mem:          4027       2460       1567          0        353       1586
-/+ buffers/cache:        520       3507
Swap:         4094          0       4094
```

Here, we see that I'm apparently using 2.4GB of RAM, when in fact, it's the 2nd line that we need to be looking at, so, currently, 520MB :)

---

### Post by r-senior on 2010-04-11
> **no2498 said:**
> this is all fine if you do the same thing over and over again
i set mine to 50kb
and i clean it out as flash and java keep changing 
and i do not load the same pics all the time
pages change every minute
I think the other posts address the issue of memory usage and caching but you really are doing yourself a disservice if you set your browser cache so small. The content of pages may change but logos, spacer bars, image buttons, etc. are pretty much constant. By setting your browser cache small and clearing it out frequently, you just force the browser to download the same things over and over again. You'll have pages loading slower as a result.

Disk space is relatively cheap. Unless you are really short of space, you are much better off setting the browser cache larger (say 100MB) and leaving the browser to manage it.

---

### Post by audiomick on 2010-04-11
Have a look at this.
[http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)
It wont speed up your boot, but it is a rather good explanation of RAM use and Cache use in Linux.

---

### Post by no2498 on 2010-04-11
if you look at the 2nd link
you will see it
if it is loaded 1 time it gets faster
now put in some bad things ? what does it do

now what good is the temp files
do they not do the same thing ?

---

### Post by outleradam on 2010-04-11
Ok, apparently there is something very wrong...
```
adam@adam-desktop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3955       3877         77          0         23       1707
-/+ buffers/cache:       2146       1808
Swap:         4416          0       4416

```
It fires up 2g of ram on boot.

---

### Post by outleradam on 2010-04-12
Apparently I have a ton of programs using resident memory
```
adam@adam-desktop:~$ top
top - 23:06:46 up 6 min,  2 users,  load average: 0.18, 0.83, 0.50
Tasks: 225 total,   2 running, 223 sleeping,   0 stopped,   0 zombie
Cpu0  :  0.0%us,  1.0%sy,  0.0%ni, 99.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu1  :  0.7%us,  5.5%sy,  0.0%ni, 93.8%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu2  :  0.0%us,  0.3%sy,  0.0%ni, 99.7%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu3  :  3.5%us,  7.5%sy,  0.0%ni, 89.1%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   4050088k total,  1800584k used,  2249504k free,    91808k buffers
Swap:  4522256k total,        0k used,  4522256k free,   365876k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                          
 1177 root      20   0  323m 141m  29m S    6  3.6   0:11.22 Xorg                             
 2510 adam      20   0  623m  76m  33m S    0  1.9   0:02.03 firefox-bin                      
 1970 adam      20   0  365m  44m   9m S    0  1.1   0:00.93 gnome-settings-                  
 2268 adam      20   0  149m  42m 5580 S    0  1.1   0:06.40 ubuntuone-syncd                  
 1989 adam      20   0  249m  35m 9228 S    0  0.9   0:00.86 compiz                           
 2237 adam      20   0  270m  27m  12m S    0  0.7   0:00.27 python                           
 2231 adam      20   0  373m  27m  10m S    0  0.7   0:00.55 gwibber-service                  
  959 mysql     20   0  239m  26m 7020 S    0  0.7   0:00.09 mysqld                           
  923 mythtv    20   0  448m  25m  20m S    0  0.6   0:00.25 mythbackend                      
 2378 adam      20   0  197m  23m 4460 S    0  0.6   0:01.51 beam.smp                         
 2543 adam      20   0  239m  22m  17m S    8  0.6   0:02.04 gnome-system-mo                  
 2012 adam      20   0  572m  21m  15m S    0  0.5   0:00.66 nautilus                         
 2235 adam      20   0  177m  18m 5420 S    0  0.5   0:00.63 desktopcouch-se                  
 2013 adam      20   0  256m  18m  12m S    0  0.5   0:00.66 gnome-panel                      
 2175 adam      20   0  472m  17m  12m S    0  0.5   0:00.08 clock-applet                     
 2448 root      20   0 95668  15m 5348 S    0  0.4   0:00.18 aptd                             
 2467 adam      20   0  209m  15m  11m S    0  0.4   0:00.50 gnome-terminal                   
 2142 adam      20   0  250m  14m  10m S    0  0.4   0:00.28 wnck-applet                      
 2170 adam      20   0  262m  14m  11m S    0  0.4   0:00.09 indicator-apple                  
 2173 adam      20   0  264m  14m  10m S    0  0.4   0:00.10 indicator-apple                  
 2236 adam      20   0  419m  13m  10m S    0  0.3   0:00.07 evolution-alarm                  
 2242 adam      20   0  345m  13m  10m S    0  0.3   0:00.06 evolution-excha                  
 2439 adam      20   0  201m  13m 9896 S    0  0.3   0:00.11 update-notifier                  
 1998 adam      20   0  231m  12m 9332 S    0  0.3   0:00.09 nm-applet
```I have all these programs reporting that they are using alot of ram, however system monitor is not reporting them.

What can I do?

---

### Post by r-senior on 2010-04-12
It's very difficult to equate process memory usage figures against the cumulative usage. Utilities like top and ps essentially show the memory that would be consumed by that process if it were the only process on the system. It doesn't take account of actual shared memory usage and, as a result, individual process memory usages can look alarming. 

Linux memory is more complex than a beer bottle. Worrying about how much is left is not usually productive. 

I think it's best to view memory as a resource to be used to improve performance, not something that you are going to run out of. You've got 4GB to play with. The machine I'm typing on is running fine with 512MB and only struggles when I run a real memory hog. I don't think you are about to run out ...

... when the disk starts churning and the swap usage goes up, that's when you need to worry. 

Practical things you can do to reduce memory usage would be not starting applications you don't need at startup, not running unnecessary applets, not leaving programs open you don't need and so on. I don't think you need to, but if you want to feel like you are being lean on memory, go ahead.

---

### Post by mörgæs on 2010-04-12
If you want a system eating less memory, a minimal install might be worth trying:

[http://ubuntuforums.org/showthread.php?t=1155961](http://ubuntuforums.org/showthread.php?t=1155961)

---

### Post by J V on 2010-04-12
Please post the output of ps aux

---

### Post by k3lt01 on 2010-04-12
I'm assuming you are using Lucid so I will base much of my answer on that. This assumption is based on the fact that under you name you have Ubuntu Development release written.

There have been numerous reports about Lucid using alot of memory on certain boots, usually the first after an update. I know of at least one dev who has been working on this issue and apparently an update is coming, or has come, that will fix it.

I have also seen my laptop have similar issues. Another person who I have tried to help with a similar issue reported back today that the new 2.6.32-20 kernel which was released last night has fixed his issue.

Soooooo, my advice atm is, if you are using Lucid update to the new kernel and try it. If you are not using Lucid I would go into your start up list and see what's in there and if you really need all this programs starting at startup.

---

### Post by outleradam on 2010-04-12
> **mörgæs said:**
> If you want a system eating less memory, a minimal install might be worth trying:
 
[http://ubuntuforums.org/showthread.php?t=1155961](http://ubuntuforums.org/showthread.php?t=1155961)
 
That's not what I want at all!   
 
When I installed Ubuntu on my new Asus motherboard and processor less then a month ago, it booted quickly and firefox was loaded and ready to use within a fraction of a second after I released my mouse after clicking on the icon.  I have no clue what's going on now.  it's just slow and using a ton of memory on startup.  Firefox now takes 3-10 seconds to load.
 
I bought new hardware because it's quick.  I use Ubuntu because it's quick.  Now my new hardware and my OS are functioning like old hardware.   As far as Ubuntu is concerned, I've really only installed VirtualBox and daily updates and my system is a month old.
 
 
When I get home I'll post the outputs.  If it's caching anything, it's not caching the right stuff.  Whatever it's caching is worthless to me.

---

### Post by Mighty_Joe on 2010-04-12
> **outleradam said:**
>  As far as Ubuntu is concerned, I've really only installed VirtualBox and daily updates and my system is a month old.
 

According to [this post]("http://ubuntuforums.org/showpost.php?p=9110074&postcount=10"), it looks like you've got MySQL and MythTV installed and running, so I'd say you aren't being entirely truthful with us.
According to top, you have 225 processes running.  I have a Ubuntu 9.10 VM handy, and at startup it has 127 processes running.  There may be something there, but your CPU utilization is low and your memory use is not excessive, so I'm not sure how to reconcile what you are saying with what top tells us.
Is VirtualBox running when your computer is slow?  Keep in mind that it can be run as a daemon (i.e. without a GUI interface).

---

### Post by fromthehill on 2010-04-12
> **outleradam said:**
> Apparently I have a ton of programs using resident memory
```
adam@adam-desktop:~$ top
top - 23:06:46 up 6 min,  2 users,  load average: 0.18, 0.83, 0.50
Tasks: 225 total,   2 running, 223 sleeping,   0 stopped,   0 zombie
Cpu0  :  0.0%us,  1.0%sy,  0.0%ni, 99.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu1  :  0.7%us,  5.5%sy,  0.0%ni, 93.8%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu2  :  0.0%us,  0.3%sy,  0.0%ni, 99.7%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu3  :  3.5%us,  7.5%sy,  0.0%ni, 89.1%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   4050088k total,  1800584k used,  2249504k free,    91808k buffers
Swap:  4522256k total,        0k used,  4522256k free,   365876k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                          
 1177 root      20   0  323m 141m  29m S    6  3.6   0:11.22 Xorg                             
 2510 adam      20   0  623m  76m  33m S    0  1.9   0:02.03 firefox-bin                      
 1970 adam      20   0  365m  44m   9m S    0  1.1   0:00.93 gnome-settings-                  
 2268 adam      20   0  149m  42m 5580 S    0  1.1   0:06.40 ubuntuone-syncd                  
 1989 adam      20   0  249m  35m 9228 S    0  0.9   0:00.86 compiz                           
 2237 adam      20   0  270m  27m  12m S    0  0.7   0:00.27 python                           
 2231 adam      20   0  373m  27m  10m S    0  0.7   0:00.55 gwibber-service                  
  959 mysql     20   0  239m  26m 7020 S    0  0.7   0:00.09 mysqld                           
  923 mythtv    20   0  448m  25m  20m S    0  0.6   0:00.25 mythbackend                      
 2378 adam      20   0  197m  23m 4460 S    0  0.6   0:01.51 beam.smp                         
 2543 adam      20   0  239m  22m  17m S    8  0.6   0:02.04 gnome-system-mo                  
 2012 adam      20   0  572m  21m  15m S    0  0.5   0:00.66 nautilus                         
 2235 adam      20   0  177m  18m 5420 S    0  0.5   0:00.63 desktopcouch-se                  
 2013 adam      20   0  256m  18m  12m S    0  0.5   0:00.66 gnome-panel                      
 2175 adam      20   0  472m  17m  12m S    0  0.5   0:00.08 clock-applet                     
 2448 root      20   0 95668  15m 5348 S    0  0.4   0:00.18 aptd                             
 2467 adam      20   0  209m  15m  11m S    0  0.4   0:00.50 gnome-terminal                   
 2142 adam      20   0  250m  14m  10m S    0  0.4   0:00.28 wnck-applet                      
 2170 adam      20   0  262m  14m  11m S    0  0.4   0:00.09 indicator-apple                  
 2173 adam      20   0  264m  14m  10m S    0  0.4   0:00.10 indicator-apple                  
 2236 adam      20   0  419m  13m  10m S    0  0.3   0:00.07 evolution-alarm                  
 2242 adam      20   0  345m  13m  10m S    0  0.3   0:00.06 evolution-excha                  
 2439 adam      20   0  201m  13m 9896 S    0  0.3   0:00.11 update-notifier                  
 1998 adam      20   0  231m  12m 9332 S    0  0.3   0:00.09 nm-applet
```I have all these programs reporting that they are using alot of ram, however system monitor is not reporting them.

What can I do?

the largest process only uses 3.9% of your memory:confused:
and you still have half of your memory unused
your swap isn't in use at all

whatever is causing your computer to be slow, it probably isn't your ram

---

### Post by outleradam on 2010-04-12
^^ On the first page, you can see that my +- buffers are at about 2gig.  
 
> **Mighty_Joe said:**
> According to [this post]("http://ubuntuforums.org/showpost.php?p=9110074&postcount=10"), it looks like you've got MySQL and MythTV installed and running, so I'd say you aren't being entirely truthful with us.
According to top, you have 225 processes running. I have a Ubuntu 9.10 VM handy, and at startup it has 127 processes running. There may be something there, but your CPU utilization is low and your memory use is not excessive, so I'm not sure how to reconcile what you are saying with what top tells us.
Is VirtualBox running when your computer is slow? Keep in mind that it can be run as a daemon (i.e. without a GUI interface).
Yeah, I forgot about that. I'm developing a script to work with mythtv. MythTv is not configured to work with a tuner or record currently. It's a dummy install.  I do the actual work on my media center computer.

---

### Post by outleradam on 2010-04-12
If I had accidentally configured a windows XP virtual box machine to run as a daemon, would it show up in the process list?  Virtualbox does not report any running machines...

---

### Post by outleradam on 2010-04-12
I am running ubuntu beta 1 with daily dist-upgrades on my part.

I just did my daily routine of apt-get update, apt-get dist-upgrade, reboot  just now and it seems that the memory has reduced.  Boot is not much quicker though.  

```
adam@adam-desktop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3955       1959       1995          0        133        300
-/+ buffers/cache:       1525       2429
Swap:         4416          0       4416
adam@adam-desktop:~$ ps -aux
Warning: bad ps syntax, perhaps a bogus '-'? See http://procps.sf.net/faq.html
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.4  0.0  23816  2064 ?        Ss   17:32   0:00 /sbin/init
root         2  0.0  0.0      0     0 ?        S    17:32   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S    17:32   0:00 [migration/0]
root         4  0.1  0.0      0     0 ?        S    17:32   0:00 [ksoftirqd/0]
root         5  0.0  0.0      0     0 ?        S    17:32   0:00 [watchdog/0]
root         6  0.0  0.0      0     0 ?        S    17:32   0:00 [migration/1]
root         7  3.6  0.0      0     0 ?        S    17:32   0:07 [ksoftirqd/1]
root         8  0.0  0.0      0     0 ?        S    17:32   0:00 [watchdog/1]
root         9  0.0  0.0      0     0 ?        S    17:32   0:00 [migration/2]
root        10  4.1  0.0      0     0 ?        S    17:32   0:08 [ksoftirqd/2]
root        11  0.0  0.0      0     0 ?        S    17:32   0:00 [watchdog/2]
root        12  0.0  0.0      0     0 ?        S    17:32   0:00 [migration/3]
root        13  1.7  0.0      0     0 ?        S    17:32   0:03 [ksoftirqd/3]
root        14  0.0  0.0      0     0 ?        S    17:32   0:00 [watchdog/3]
root        15  0.0  0.0      0     0 ?        S    17:32   0:00 [events/0]
root        16  0.0  0.0      0     0 ?        S    17:32   0:00 [events/1]
root        17  0.0  0.0      0     0 ?        S    17:32   0:00 [events/2]
root        18  0.0  0.0      0     0 ?        S    17:32   0:00 [events/3]
root        19  0.0  0.0      0     0 ?        S    17:32   0:00 [cpuset]
root        20  0.0  0.0      0     0 ?        S    17:32   0:00 [khelper]
root        21  0.0  0.0      0     0 ?        S    17:32   0:00 [netns]
root        22  0.0  0.0      0     0 ?        S    17:32   0:00 [async/mgr]
root        23  0.0  0.0      0     0 ?        S    17:32   0:00 [pm]
root        25  0.0  0.0      0     0 ?        S    17:32   0:00 [sync_supers]
root        26  0.0  0.0      0     0 ?        S    17:32   0:00 [bdi-default]
root        27  0.0  0.0      0     0 ?        S    17:32   0:00 [kintegrityd/0]
root        28  0.0  0.0      0     0 ?        S    17:32   0:00 [kintegrityd/1]
root        29  0.0  0.0      0     0 ?        S    17:32   0:00 [kintegrityd/2]
root        30  0.0  0.0      0     0 ?        S    17:32   0:00 [kintegrityd/3]
root        31  0.0  0.0      0     0 ?        S    17:32   0:00 [kblockd/0]
root        32  0.0  0.0      0     0 ?        S    17:32   0:00 [kblockd/1]
root        33  0.0  0.0      0     0 ?        S    17:32   0:00 [kblockd/2]
root        34  0.0  0.0      0     0 ?        S    17:32   0:00 [kblockd/3]
root        35  0.0  0.0      0     0 ?        S    17:32   0:00 [kacpid]
root        36  0.0  0.0      0     0 ?        S    17:32   0:00 [kacpi_notify]
root        37  0.0  0.0      0     0 ?        S    17:32   0:00 [kacpi_hotplug]
root        38  0.0  0.0      0     0 ?        S    17:32   0:00 [ata/0]
root        39  0.0  0.0      0     0 ?        S    17:32   0:00 [ata/1]
root        40  0.0  0.0      0     0 ?        S    17:32   0:00 [ata/2]
root        41  0.0  0.0      0     0 ?        S    17:32   0:00 [ata/3]
root        42  0.0  0.0      0     0 ?        S    17:32   0:00 [ata_aux]
root        43  0.0  0.0      0     0 ?        S    17:32   0:00 [ksuspend_usbd]
root        44  0.0  0.0      0     0 ?        S    17:32   0:00 [khubd]
root        45  0.0  0.0      0     0 ?        S    17:32   0:00 [kseriod]
root        46  0.0  0.0      0     0 ?        S    17:32   0:00 [kmmcd]
root        51  0.0  0.0      0     0 ?        S    17:32   0:00 [khungtaskd]
root        52  0.0  0.0      0     0 ?        S    17:32   0:00 [kswapd0]
root        53  0.0  0.0      0     0 ?        SN   17:32   0:00 [ksmd]
root        54  0.0  0.0      0     0 ?        S    17:32   0:00 [aio/0]
root        55  0.0  0.0      0     0 ?        S    17:32   0:00 [aio/1]
root        56  0.0  0.0      0     0 ?        S    17:32   0:00 [aio/2]
root        57  0.0  0.0      0     0 ?        S    17:32   0:00 [aio/3]
root        58  0.0  0.0      0     0 ?        S    17:32   0:00 [ecryptfs-kthrea]
root        59  0.0  0.0      0     0 ?        S    17:32   0:00 [crypto/0]
root        60  0.0  0.0      0     0 ?        S    17:32   0:00 [crypto/1]
root        61  0.0  0.0      0     0 ?        S    17:32   0:00 [crypto/2]
root        62  0.0  0.0      0     0 ?        S    17:32   0:00 [crypto/3]
root        65  0.0  0.0      0     0 ?        S    17:32   0:00 [scsi_eh_0]
root        66  0.0  0.0      0     0 ?        S    17:32   0:00 [scsi_eh_1]
root        69  0.0  0.0      0     0 ?        S    17:32   0:00 [scsi_eh_2]
root        70  0.0  0.0      0     0 ?        S    17:32   0:00 [scsi_eh_3]
root        73  0.0  0.0      0     0 ?        S    17:32   0:00 [kstriped]
root        74  0.0  0.0      0     0 ?        S    17:32   0:00 [kmpathd/0]
root        75  0.0  0.0      0     0 ?        S    17:32   0:00 [kmpathd/1]
root        76  0.0  0.0      0     0 ?        S    17:32   0:00 [kmpathd/2]
root        77  0.0  0.0      0     0 ?        S    17:32   0:00 [kmpathd/3]
root        78  0.0  0.0      0     0 ?        S    17:32   0:00 [kmpath_handlerd]
root        79  0.0  0.0      0     0 ?        S    17:32   0:00 [ksnapd]
root        80  0.0  0.0      0     0 ?        S    17:32   0:00 [kondemand/0]
root        81  0.0  0.0      0     0 ?        S    17:32   0:00 [kondemand/1]
root        82  0.1  0.0      0     0 ?        S    17:32   0:00 [kondemand/2]
root        83  0.0  0.0      0     0 ?        S    17:32   0:00 [kondemand/3]
root        84  0.0  0.0      0     0 ?        S    17:32   0:00 [kconservative/0]
root        85  0.0  0.0      0     0 ?        S    17:32   0:00 [kconservative/1]
root        86  0.0  0.0      0     0 ?        S    17:32   0:00 [kconservative/2]
root        87  0.0  0.0      0     0 ?        S    17:32   0:00 [kconservative/3]
root       301  0.0  0.0      0     0 ?        S    17:32   0:00 [khpsbpkt]
root       314  0.0  0.0      0     0 ?        S    17:32   0:00 [scsi_eh_4]
root       319  0.0  0.0      0     0 ?        S    17:32   0:00 [scsi_eh_5]
root       323  0.0  0.0      0     0 ?        S    17:32   0:00 [scsi_eh_6]
root       324  0.0  0.0      0     0 ?        S    17:32   0:00 [scsi_eh_7]
root       329  0.0  0.0      0     0 ?        S    17:32   0:00 [knodemgrd_0]
root       345  0.0  0.0      0     0 ?        S    17:32   0:00 [usbhid_resumer]
root       354  0.0  0.0      0     0 ?        S    17:32   0:00 [flush-1:0]
root       355  0.0  0.0      0     0 ?        S    17:32   0:00 [flush-1:1]
root       356  0.0  0.0      0     0 ?        S    17:32   0:00 [flush-1:2]
root       357  0.0  0.0      0     0 ?        S    17:32   0:00 [flush-1:3]
root       358  0.0  0.0      0     0 ?        S    17:32   0:00 [flush-1:4]
root       359  0.0  0.0      0     0 ?        S    17:32   0:00 [flush-1:5]
root       360  0.0  0.0      0     0 ?        S    17:32   0:00 [flush-1:6]
root       361  0.0  0.0      0     0 ?        S    17:32   0:00 [flush-1:7]
root       362  0.0  0.0      0     0 ?        S    17:32   0:00 [flush-1:8]
root       363  0.0  0.0      0     0 ?        S    17:32   0:00 [flush-1:9]
root       364  0.0  0.0      0     0 ?        S    17:32   0:00 [flush-1:10]
root       365  0.0  0.0      0     0 ?        S    17:32   0:00 [flush-1:11]
root       366  0.0  0.0      0     0 ?        S    17:32   0:00 [flush-1:12]
root       367  0.0  0.0      0     0 ?        S    17:32   0:00 [flush-1:13]
root       368  0.0  0.0      0     0 ?        S    17:32   0:00 [flush-1:14]
root       369  0.0  0.0      0     0 ?        S    17:32   0:00 [flush-1:15]
root       370  0.0  0.0      0     0 ?        S    17:32   0:00 [flush-8:16]
root       371  0.0  0.0      0     0 ?        S    17:32   0:00 [flush-8:0]
root       372  0.0  0.0      0     0 ?        S    17:32   0:00 [flush-8:32]
root       375  0.0  0.0      0     0 ?        S    17:32   0:00 [kjournald]
root       418  0.0  0.0  17028  1084 ?        S    17:32   0:00 upstart-udev-bridge --daemon
root       422  0.0  0.0  17456  1308 ?        S<s  17:32   0:00 udevd --daemon
root       762  0.0  0.0      0     0 ?        S    17:32   0:00 [kpsmoused]
root       764  0.0  0.0      0     0 ?        S    17:32   0:00 [bluetooth]
root       786  0.0  0.1  94296  4532 ?        Ss   17:32   0:00 smbd -F
root       820  0.0  0.0      0     0 ?        S    17:32   0:00 [cx18-0-out/0]
root       821  0.0  0.0      0     0 ?        S    17:32   0:00 [cx18-0-out/1]
root       822  0.0  0.0      0     0 ?        S    17:32   0:00 [cx18-0-out/2]
root       823  0.0  0.0      0     0 ?        S    17:32   0:00 [cx18-0-out/3]
root       824  0.0  0.0      0     0 ?        S    17:32   0:00 [cx18-0-in]
syslog     831  0.0  0.0 125972  1644 ?        Sl   17:32   0:00 rsyslogd -c4
102        869  0.1  0.0  24404  1940 ?        Ss   17:32   0:00 dbus-daemon --system --fork
root       877  0.0  0.0      0     0 ?        S<   17:32   0:00 [kslowd000]
root       878  0.0  0.0      0     0 ?        S<   17:32   0:00 [kslowd001]
root       901  0.0  0.0      0     0 ?        S    17:32   0:00 [hd-audio0]
root       914  0.0  0.0      0     0 ?        S    17:32   0:00 [hd-audio1]
root       919  0.0  0.0  76588  3492 ?        Ssl  17:32   0:00 gdm-binary
avahi      955  0.0  0.0  34048  1672 ?        S    17:32   0:00 avahi-daemon: running [adam-desktop.local]
avahi      956  0.0  0.0  33920   572 ?        Ss   17:32   0:00 avahi-daemon: chroot helper
root       961  0.0  0.0   4088   608 ?        Ss   17:32   0:00 /bin/sh -e /proc/self/fd/12
mythtv     964  0.0  0.6 459068 25788 ?        Sl   17:32   0:00 /usr/bin/mythbackend --logfile /var/log/mythtv/mythbackend.log --user mythtv
root       987  0.0  0.1  87556  4080 ?        Ssl  17:32   0:00 NetworkManager
mysql      997  0.1  0.6 245184 26924 ?        Ssl  17:32   0:00 /usr/sbin/mysqld
root      1004  0.0  0.0 120452  3628 ?        Sl   17:32   0:00 /usr/sbin/console-kit-daemon --no-daemon
root      1009  0.0  0.0  57856  2528 ?        S    17:32   0:00 /usr/sbin/modem-manager
root      1012  0.0  0.0  28344  2100 ?        S    17:32   0:00 /sbin/wpa_supplicant -u -s
root      1013  0.0  0.0   6548  1112 ?        S    17:32   0:00 /sbin/dhclient -d -sf /usr/lib/NetworkManager/nm-dhcp-client.action -pf /var/run/dhclient-eth0.pid -lf /var/lib/dhcp3/dhclient-fb1b9e25-70bc-4dac-af7c-e4bfeee52463-eth0.lease -cf /var/run/nm-dhclient-eth0.conf eth0
root      1083  0.0  0.1  93452  4056 ?        Sl   17:32   0:00 /usr/lib/gdm/gdm-simple-slave --display-id /org/gnome/DisplayManager/Display1
root      1085  0.0  0.0  17452  1340 ?        S<   17:32   0:00 udevd --daemon
root      1105  8.6  3.6 259956 146484 tty7    Ss+  17:32   0:14 /usr/bin/X :0 -nr -verbose -auth /var/run/gdm/auth-for-gdm-DaFk5K/database -nolisten tcp vt7
root      1111  0.0  0.0  94296  1344 ?        S    17:32   0:00 smbd -F
root      1133  0.0  0.0      0     0 ?        S    17:32   0:00 [firegl]
root      1211  0.0  0.0   6072   656 tty4     Ss+  17:32   0:00 /sbin/getty -8 38400 tty4
root      1216  0.0  0.0   6072   652 tty5     Ss+  17:32   0:00 /sbin/getty -8 38400 tty5
root      1222  0.0  0.0   6072   648 tty2     Ss+  17:32   0:00 /sbin/getty -8 38400 tty2
root      1223  0.0  0.0   6072   652 tty3     Ss+  17:32   0:00 /sbin/getty -8 38400 tty3
root      1225  0.0  0.0   6072   652 tty6     Ss+  17:32   0:00 /sbin/getty -8 38400 tty6
root      1228  0.0  0.0   4552  1176 ?        Ss   17:32   0:00 acpid -c /etc/acpi/events -s /var/run/acpid.socket
root      1232  0.0  0.0  21068  1016 ?        Ss   17:32   0:00 cron
daemon    1233  0.0  0.0  18876   456 ?        Ss   17:32   0:00 atd
root      1248  0.0  0.0  11272   644 ?        Ss   17:32   0:00 /usr/sbin/irqbalance
root      1335  0.1  0.1 165016  5036 ?        Sl   17:32   0:00 /usr/sbin/libvirtd -d
root      1350  0.0  0.0   6256   392 ?        Ss   17:32   0:00 /usr/sbin/dhcrelay3 -q -i eth0 192.168.1.1
root      1402  0.0  0.0      0     0 ?        S    17:32   0:00 [cifsd]
kernoops  1412  0.0  0.0  22312   984 ?        Ss   17:32   0:00 /usr/sbin/kerneloops
root      1418  0.0  0.0  60504  1752 ?        Ss   17:32   0:00 nmbd -D
uml-net   1506  0.0  0.0   4004   532 ?        S    17:32   0:00 /usr/bin/uml_switch -unix /var/run/uml-utilities/uml_switch.ctl
nobody    1511  0.0  0.0  21420   920 ?        S    17:32   0:00 dnsmasq --strict-order --bind-interfaces --pid-file=/var/run/libvirt/network/default.pid --conf-file=  --listen-address 192.168.122.1 --except-interface lo --dhcp-range 192.168.122.2,192.168.122.254 --dhcp-lease-max=253
ntp       1551  0.0  0.0  27852  1556 ?        Ss   17:32   0:00 /usr/sbin/ntpd -p /var/run/ntpd.pid -g -u 117:125
root      1571  0.0  0.0  17452  1340 ?        S<   17:32   0:00 udevd --daemon
root      1607  0.0  0.0  65712  1512 ?        Ss   17:32   0:00 /usr/sbin/winbindd
root      1627  0.0  0.0  65824  1680 ?        S    17:32   0:00 /usr/sbin/winbindd
root      1631  0.0  0.0  27428  2096 ?        S<s  17:32   0:00 /usr/sbin/bluetoothd --udev
root      1666  0.0  0.0  75388  3104 ?        Ss   17:32   0:00 /usr/sbin/cupsd -C /etc/cups/cupsd.conf
root      1670  0.0  0.0      0     0 ?        S<   17:32   0:00 [krfcommd]
root      1898  0.0  0.0   6072   652 tty1     Ss+  17:32   0:00 /sbin/getty -8 38400 tty1
root      1901  0.0  0.0  95236  3352 ?        Sl   17:32   0:00 /usr/lib/gdm/gdm-session-worker
adam      1915  0.0  0.1 167312  7724 ?        Ssl  17:32   0:00 gnome-session
adam      1956  0.0  0.0  11928   412 ?        Ss   17:32   0:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session gnome-session
adam      1959  0.0  0.0  26252   820 ?        S    17:32   0:00 /usr/bin/dbus-launch --exit-with-session gnome-session
adam      1960  0.1  0.0  24208  1668 ?        Ss   17:32   0:00 /bin/dbus-daemon --fork --print-pid 5 --print-address 9 --session
adam      1963  0.2  0.1  46116  5712 ?        S    17:32   0:00 /usr/lib/libgconf2-4/gconfd-2
adam      1970  0.5  1.1 374196 45460 ?        Ss   17:32   0:00 /usr/lib/gnome-settings-daemon/gnome-settings-daemon
adam      1972  0.0  0.0  77948  2976 ?        SLl  17:32   0:00 gnome-keyring-daemon --start --components=pkcs11
adam      1976  0.0  0.0  47984  2524 ?        S    17:33   0:00 /usr/lib/gvfs/gvfsd
adam      1981  0.0  0.0  78016  2752 ?        Ssl  17:33   0:00 /usr/lib/gvfs//gvfs-fuse-daemon /home/adam/.gvfs
adam      1987  0.7  0.8 255020 36260 ?        S    17:33   0:01 compiz
adam      1996  0.0  0.3 237540 13104 ?        S    17:33   0:00 nm-applet --sm-disable
adam      1999  0.0  0.2 201648 11324 ?        S    17:33   0:00 bluetooth-applet
adam      2000  0.0  0.2 176012  8980 ?        S    17:33   0:00 gnome-power-manager
adam      2001  0.3  0.5 585780 22184 ?        S    17:33   0:00 nautilus
adam      2002  0.2  0.4 259792 17900 ?        S    17:33   0:00 gnome-panel
adam      2003  0.0  0.1 161868  7028 ?        S    17:33   0:00 /usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1
adam      2009  0.0  0.1 221184  5060 ?        S<sl 17:33   0:00 /usr/bin/pulseaudio --start --log-target=syslog
rtkit     2011  0.0  0.0 109168  1304 ?        SNl  17:33   0:00 /usr/lib/rtkit/rtkit-daemon
root      2015  0.1  0.1  54220  4412 ?        S    17:33   0:00 /usr/lib/policykit-1/polkitd
adam      2019  0.0  0.0  96640  3504 ?        S    17:33   0:00 /usr/lib/pulseaudio/pulse/gconf-helper
root      2022  0.0  0.0  53584  3080 ?        S    17:33   0:00 /usr/lib/upower/upowerd
109       2064  0.0  0.1  46848  5104 ?        Ssl  17:33   0:00 /usr/sbin/hald
root      2065  0.0  0.0  22308  1392 ?        S    17:33   0:00 hald-runner
adam      2077  0.0  0.0 153972  3888 ?        S    17:33   0:00 /usr/lib/gvfs/gvfs-gdu-volume-monitor
root      2093  0.0  0.0  65776  3680 ?        Sl   17:33   0:00 /usr/lib/udisks/udisks-daemon
root      2094  0.0  0.0  46684   944 ?        S    17:33   0:00 udisks-daemon: polling /dev/sr0
root      2095  0.0  0.0  24428  1300 ?        S    17:33   0:00 hald-addon-input: Listening on /dev/input/event4 /dev/input/event3 /dev/input/event0 /dev/input/event1 /dev/input/event6
root      2098  0.0  0.0  24420  1280 ?        S    17:33   0:00 /usr/lib/hal/hald-addon-rfkill-killswitch
root      2113  0.0  0.0  24424  1416 ?        S    17:33   0:00 hald-addon-storage: polling /dev/sr0 (every 2 sec)
root      2121  0.0  0.0  24436  1288 ?        S    17:33   0:00 /usr/lib/hal/hald-addon-cpufreq
109       2122  0.0  0.0  26260  1248 ?        S    17:33   0:00 hald-addon-acpi: listening on acpid socket /var/run/acpid.socket
adam      2124  0.0  0.0  69204  2728 ?        Sl   17:33   0:00 /usr/lib/gvfs/gvfs-afc-volume-monitor
adam      2127  0.0  0.0  55288  2680 ?        S    17:33   0:00 /usr/lib/gvfs/gvfs-gphoto2-volume-monitor
adam      2128  0.0  0.0 171504  3124 ?        Ss   17:33   0:00 gnome-screensaver
adam      2130  0.0  0.0  52472  3184 ?        S    17:33   0:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.8 /org/gtk/gvfs/exec_spaw/0
adam      2132  0.0  0.1 218316  4140 ?        Ssl  17:33   0:00 /usr/lib/bonobo-activation/bonobo-activation-server --ac-activate --ior-output-fd=19
adam      2139  0.1  0.3 256772 14772 ?        S    17:33   0:00 /usr/lib/gnome-panel/wnck-applet --oaf-activate-iid=OAFIID:GNOME_Wncklet_Factory --oaf-ior-fd=18
adam      2140  0.0  0.0   4088   592 ?        Ss   17:33   0:00 /bin/sh -c /usr/bin/compiz-decorator
adam      2141  0.1  0.2 176760 11320 ?        S    17:33   0:00 /usr/bin/gtk-window-decorator
adam      2150  0.1  0.3 240948 12800 ?        S    17:33   0:00 /usr/lib/gnome-applets/trashapplet --oaf-activate-iid=OAFIID:GNOME_Panel_TrashApplet_Factory --oaf-ior-fd=21
root      2158  0.0  0.0      0     0 ?        S    17:33   0:00 [flush-11:0]
adam      2167  0.1  0.2 211672 12124 ?        S    17:33   0:00 /usr/lib/gnome-applets/cpufreq-applet --oaf-activate-iid=OAFIID:GNOME_CPUFreqApplet_Factory --oaf-ior-fd=18
adam      2169  0.0  0.2 208192 10244 ?        S    17:33   0:00 /usr/lib/gnome-panel/notification-area-applet --oaf-activate-iid=OAFIID:GNOME_NotificationAreaApplet_Factory --oaf-ior-fd=28
adam      2171  0.0  0.4 418168 18364 ?        S    17:33   0:00 /usr/lib/gnome-panel/clock-applet --oaf-activate-iid=OAFIID:GNOME_ClockApplet_Factory --oaf-ior-fd=40
adam      2173  0.0  0.3 271272 14972 ?        S    17:33   0:00 /usr/lib/indicator-applet/indicator-applet --oaf-activate-iid=OAFIID:GNOME_IndicatorApplet_Factory --oaf-ior-fd=34
adam      2174  0.0  0.3 334652 15056 ?        S    17:33   0:00 /usr/lib/indicator-applet/indicator-applet-session --oaf-activate-iid=OAFIID:GNOME_FastUserSwitchApplet_Factory --oaf-ior-fd=46
adam      2179  0.0  0.0  41724  2340 ?        S    17:33   0:00 /usr/lib/gvfs/gvfsd-metadata
adam      2181  0.0  0.1 143824  5664 ?        S    17:33   0:00 /usr/lib/indicator-me/indicator-me-service
adam      2183  0.0  0.1 140840  5536 ?        S    17:33   0:00 /usr/lib/indicator-session/indicator-session-service
adam      2185  0.0  0.2 176648  8164 ?        S    17:33   0:00 /usr/lib/gnome-disk-utility/gdu-notification-daemon
adam      2187  0.0  0.1 138088  4972 ?        S    17:33   0:00 /usr/lib/indicator-messages/indicator-messages-service
adam      2189  0.0  0.1 146872  4892 ?        S    17:33   0:00 /usr/lib/indicator-application/indicator-application-service
adam      2191  0.0  0.1 219004  5364 ?        S    17:33   0:00 /usr/lib/indicator-sound/indicator-sound-service
adam      2201  0.0  0.1 150472  7140 ?        S    17:33   0:00 /usr/lib/gnome-user-share/gnome-user-share
adam      2204  0.0  0.0  47852  2604 ?        S    17:33   0:00 /usr/lib/gvfs/gvfsd-burn --spawner :1.8 /org/gtk/gvfs/exec_spaw/1
adam      2206  0.0  0.0  79664  3260 ?        S    17:33   0:00 /usr/bin/obex-data-server --no-daemon 
root      2226  0.0  0.0  65728  1780 ?        S    17:33   0:00 /usr/sbin/winbindd
root      2229  0.0  0.0      0     0 ?        S<   17:33   0:00 [khidpd_046db003]
adam      2238  0.8  0.3 214912 15840 ?        Sl   17:33   0:00 gnome-terminal
adam      2239  0.0  0.0  14480   812 ?        S    17:33   0:00 gnome-pty-helper
adam      2240  0.2  0.1  21732  4544 pts/0    Ss   17:33   0:00 bash
adam      2256  0.3  0.6 383016 27960 ?        Sl   17:33   0:00 /usr/bin/python /usr/bin/gwibber-service
adam      2261  0.5  0.4 181720 18956 ?        SLl  17:33   0:00 /usr/bin/python /usr/lib/desktopcouch/desktopcouch-service
adam      2262  0.0  0.3 430060 14008 ?        Sl   17:33   0:00 /usr/lib/evolution/2.28/evolution-alarm-notify
adam      2263  0.1  0.6 276992 28200 ?        S    17:33   0:00 python /usr/share/system-config-printer/applet.py
adam      2272  0.0  0.3 353380 13796 ?        Sl   17:33   0:00 /usr/lib/evolution/2.28/evolution-exchange-storage --oaf-activate-iid=OAFIID:GNOME_Evolution_Exchange_Connector_CalFactory:1.2 --oaf-ior-fd=34
adam      2277  0.0  0.2 456348 11028 ?        Sl   17:33   0:00 /usr/lib/evolution/evolution-data-server-2.28 --oaf-activate-iid=OAFIID:GNOME_Evolution_DataServer_CalFactory:1.2 --oaf-ior-fd=35
adam      2319  5.2  1.0 153248 43744 ?        SLl  17:33   0:05 /usr/bin/python /usr/lib/ubuntuone-client/ubuntuone-syncdaemon
root      2342  0.0  0.0      0     0 ?        S<   17:33   0:00 [khidpd_046db307]
adam      2383  0.0  0.0   4088   672 ?        S    17:33   0:00 /bin/sh -e /usr/bin/couchdb -n -a \"/etc/couchdb/default.ini\" -a \"/etc/xdg/desktop-couch/compulsory-auth.ini\" -a \"/home/adam/.config/desktop-couch/desktop-couchdb.ini\" -b -r 0 -p /home/adam/.cache/desktop-couch/desktop-couchdb.pid -o /home/adam/.cache/desktop-couch/desktop-couchdb.stdout -e /home/adam/.cache/desktop-couch/desktop-couchdb.stderr -R
adam      2411  0.0  0.0   4088   384 ?        S    17:33   0:00 /bin/sh -e /usr/bin/couchdb -n -a \"/etc/couchdb/default.ini\" -a \"/etc/xdg/desktop-couch/compulsory-auth.ini\" -a \"/home/adam/.config/desktop-couch/desktop-couchdb.ini\" -b -r 0 -p /home/adam/.cache/desktop-couch/desktop-couchdb.pid -o /home/adam/.cache/desktop-couch/desktop-couchdb.stdout -e /home/adam/.cache/desktop-couch/desktop-couchdb.stderr -R
adam      2412  1.6  0.5 134356 22512 ?        Sl   17:33   0:01 /usr/lib/erlang/erts-5.7.4/bin/beam.smp -Bd -K true -- -root /usr/lib/erlang -progname erl -- -home /home/adam -- -noshell -noinput -smp auto -sasl errlog_type error -pa /usr/lib/couchdb/erlang/lib/couch-0.10.0/ebin /usr/lib/couchdb/erlang/lib/mochiweb-r97/ebin /usr/lib/couchdb/erlang/lib/ibrowse-1.5.2/ebin /usr/lib/couchdb/erlang/lib/erlang-oauth/ebin -eval application:load(ibrowse) -eval application:load(oauth) -eval application:load(crypto) -eval application:load(couch) -eval crypto:start() -eval ssl:start() -eval ibrowse:start() -eval couch_server:start([ "/etc/couchdb/default.i
adam      2424  0.0  0.0   3856   512 ?        Ss   17:33   0:00 heart -pid 2412 -ht 11
adam      2475  0.1  0.3 206008 13444 ?        S    17:34   0:00 update-notifier
adam      2479  0.2  0.0  20020  2904 ?        Ss   17:34   0:00 /usr/lib/erlang/lib/ssl-3.10.7/priv/bin/ssl_esock
adam      2480  0.0  0.0  10704   540 ?        Ss   17:34   0:00 inet_gethost 4
adam      2481  0.0  0.0  19084   788 ?        S    17:34   0:00 inet_gethost 4
root      2486  0.1  0.3  95672 15776 ?        S    17:34   0:00 /usr/bin/python /usr/sbin/aptd
adam      2499  0.0  0.0  15248  1208 pts/0    R+   17:35   0:00 ps -aux

```Any recommendations?

---

### Post by J V on 2010-04-12
Do you need that printer applet?

It looks like a whole bunch of small programs are using large amounts of memory... Nonetheless, why don't you reprofile grub, if you made any hardware changes (Or a plug fell out somewhere) the profile will be wrong so it will need to boot up once and fail then a second time extra slow while it tries to find your hardware again.

---

### Post by outleradam on 2010-04-12
[LEFT]nevermind...  it's still the same.

```
adam@adam-desktop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3955       2221       1733          0        134        344
-/+ buffers/cache:       1741       2213
Swap:         4416          0       4416
adam@adam-desktop:~$ ps -aux
Warning: bad ps syntax, perhaps a bogus '-'? See http://procps.sf.net/faq.html
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.1  0.0  23816  2064 ?        Ss   17:32   0:00 /sbin/init
root         2  0.0  0.0      0     0 ?        S    17:32   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S    17:32   0:00 [migration/0]
root         4  0.0  0.0      0     0 ?        S    17:32   0:00 [ksoftirqd/0]
root         5  0.0  0.0      0     0 ?        S    17:32   0:00 [watchdog/0]
root         6  0.0  0.0      0     0 ?        S    17:32   0:00 [migration/1]
root         7  1.1  0.0      0     0 ?        S    17:32   0:07 [ksoftirqd/1]
root         8  0.0  0.0      0     0 ?        S    17:32   0:00 [watchdog/1]
root         9  0.0  0.0      0     0 ?        S    17:32   0:00 [migration/2]
root        10  1.2  0.0      0     0 ?        S    17:32   0:08 [ksoftirqd/2]
root        11  0.0  0.0      0     0 ?        S    17:32   0:00 [watchdog/2]
root        12  0.0  0.0      0     0 ?        S    17:32   0:00 [migration/3]
root        13  0.5  0.0      0     0 ?        S    17:32   0:03 [ksoftirqd/3]
root        14  0.0  0.0      0     0 ?        S    17:32   0:00 [watchdog/3]
root        15  0.0  0.0      0     0 ?        S    17:32   0:00 [events/0]
root        16  0.0  0.0      0     0 ?        S    17:32   0:00 [events/1]
root        17  0.0  0.0      0     0 ?        S    17:32   0:00 [events/2]
root        18  0.0  0.0      0     0 ?        S    17:32   0:00 [events/3]
root        19  0.0  0.0      0     0 ?        S    17:32   0:00 [cpuset]
root        20  0.0  0.0      0     0 ?        S    17:32   0:00 [khelper]
root        21  0.0  0.0      0     0 ?        S    17:32   0:00 [netns]
root        22  0.0  0.0      0     0 ?        S    17:32   0:00 [async/mgr]
root        23  0.0  0.0      0     0 ?        S    17:32   0:00 [pm]
root        25  0.0  0.0      0     0 ?        S    17:32   0:00 [sync_supers]
root        26  0.0  0.0      0     0 ?        S    17:32   0:00 [bdi-default]
root        27  0.0  0.0      0     0 ?        S    17:32   0:00 [kintegrityd/0]
root        28  0.0  0.0      0     0 ?        S    17:32   0:00 [kintegrityd/1]
root        29  0.0  0.0      0     0 ?        S    17:32   0:00 [kintegrityd/2]
root        30  0.0  0.0      0     0 ?        S    17:32   0:00 [kintegrityd/3]
root        31  0.0  0.0      0     0 ?        S    17:32   0:00 [kblockd/0]
root        32  0.0  0.0      0     0 ?        S    17:32   0:00 [kblockd/1]
root        33  0.0  0.0      0     0 ?        S    17:32   0:00 [kblockd/2]
root        34  0.0  0.0      0     0 ?        S    17:32   0:00 [kblockd/3]
root        35  0.0  0.0      0     0 ?        S    17:32   0:00 [kacpid]
root        36  0.0  0.0      0     0 ?        S    17:32   0:00 [kacpi_notify]
root        37  0.0  0.0      0     0 ?        S    17:32   0:00 [kacpi_hotplug]
root        38  0.0  0.0      0     0 ?        S    17:32   0:00 [ata/0]
root        39  0.0  0.0      0     0 ?        S    17:32   0:00 [ata/1]
root        40  0.0  0.0      0     0 ?        S    17:32   0:00 [ata/2]
root        41  0.0  0.0      0     0 ?        S    17:32   0:00 [ata/3]
root        42  0.0  0.0      0     0 ?        S    17:32   0:00 [ata_aux]
root        43  0.0  0.0      0     0 ?        S    17:32   0:00 [ksuspend_usbd]
root        44  0.0  0.0      0     0 ?        S    17:32   0:00 [khubd]
root        45  0.0  0.0      0     0 ?        S    17:32   0:00 [kseriod]
root        46  0.0  0.0      0     0 ?        S    17:32   0:00 [kmmcd]
root        51  0.0  0.0      0     0 ?        S    17:32   0:00 [khungtaskd]
root        52  0.0  0.0      0     0 ?        S    17:32   0:00 [kswapd0]
root        53  0.0  0.0      0     0 ?        SN   17:32   0:00 [ksmd]
root        54  0.0  0.0      0     0 ?        S    17:32   0:00 [aio/0]
root        55  0.0  0.0      0     0 ?        S    17:32   0:00 [aio/1]
root        56  0.0  0.0      0     0 ?        S    17:32   0:00 [aio/2]
root        57  0.0  0.0      0     0 ?        S    17:32   0:00 [aio/3]
root        58  0.0  0.0      0     0 ?        S    17:32   0:00 [ecryptfs-kthrea]
root        59  0.0  0.0      0     0 ?        S    17:32   0:00 [crypto/0]
root        60  0.0  0.0      0     0 ?        S    17:32   0:00 [crypto/1]
root        61  0.0  0.0      0     0 ?        S    17:32   0:00 [crypto/2]
root        62  0.0  0.0      0     0 ?        S    17:32   0:00 [crypto/3]
root        65  0.0  0.0      0     0 ?        S    17:32   0:00 [scsi_eh_0]
root        66  0.0  0.0      0     0 ?        S    17:32   0:00 [scsi_eh_1]
root        69  0.0  0.0      0     0 ?        S    17:32   0:00 [scsi_eh_2]
root        70  0.0  0.0      0     0 ?        S    17:32   0:00 [scsi_eh_3]
root        73  0.0  0.0      0     0 ?        S    17:32   0:00 [kstriped]
root        74  0.0  0.0      0     0 ?        S    17:32   0:00 [kmpathd/0]
root        75  0.0  0.0      0     0 ?        S    17:32   0:00 [kmpathd/1]
root        76  0.0  0.0      0     0 ?        S    17:32   0:00 [kmpathd/2]
root        77  0.0  0.0      0     0 ?        S    17:32   0:00 [kmpathd/3]
root        78  0.0  0.0      0     0 ?        S    17:32   0:00 [kmpath_handlerd]
root        79  0.0  0.0      0     0 ?        S    17:32   0:00 [ksnapd]
root        80  0.0  0.0      0     0 ?        S    17:32   0:00 [kondemand/0]
root        81  0.0  0.0      0     0 ?        S    17:32   0:00 [kondemand/1]
root        82  0.0  0.0      0     0 ?        S    17:32   0:00 [kondemand/2]
root        83  0.0  0.0      0     0 ?        S    17:32   0:00 [kondemand/3]
root        84  0.0  0.0      0     0 ?        S    17:32   0:00 [kconservative/0]
root        85  0.0  0.0      0     0 ?        S    17:32   0:00 [kconservative/1]
root        86  0.0  0.0      0     0 ?        S    17:32   0:00 [kconservative/2]
root        87  0.0  0.0      0     0 ?        S    17:32   0:00 [kconservative/3]
root       301  0.0  0.0      0     0 ?        S    17:32   0:00 [khpsbpkt]
root       314  0.0  0.0      0     0 ?        S    17:32   0:00 [scsi_eh_4]
root       319  0.0  0.0      0     0 ?        S    17:32   0:00 [scsi_eh_5]
root       323  0.0  0.0      0     0 ?        S    17:32   0:00 [scsi_eh_6]
root       324  0.0  0.0      0     0 ?        S    17:32   0:00 [scsi_eh_7]
root       329  0.0  0.0      0     0 ?        S    17:32   0:00 [knodemgrd_0]
root       345  0.0  0.0      0     0 ?        S    17:32   0:00 [usbhid_resumer]
root       370  0.0  0.0      0     0 ?        S    17:32   0:00 [flush-8:16]
root       375  0.0  0.0      0     0 ?        S    17:32   0:00 [kjournald]
root       418  0.0  0.0  17028  1084 ?        S    17:32   0:00 upstart-udev-bridge --daemon
root       422  0.0  0.0  17456  1308 ?        S<s  17:32   0:00 udevd --daemon
root       762  0.0  0.0      0     0 ?        S    17:32   0:00 [kpsmoused]
root       764  0.0  0.0      0     0 ?        S    17:32   0:00 [bluetooth]
root       786  0.0  0.1  94296  4532 ?        Ss   17:32   0:00 smbd -F
root       820  0.0  0.0      0     0 ?        S    17:32   0:00 [cx18-0-out/0]
root       821  0.0  0.0      0     0 ?        S    17:32   0:00 [cx18-0-out/1]
root       822  0.0  0.0      0     0 ?        S    17:32   0:00 [cx18-0-out/2]
root       823  0.0  0.0      0     0 ?        S    17:32   0:00 [cx18-0-out/3]
root       824  0.0  0.0      0     0 ?        S    17:32   0:00 [cx18-0-in]
syslog     831  0.0  0.0 125972  1644 ?        Sl   17:32   0:00 rsyslogd -c4
102        869  0.0  0.0  24404  1944 ?        Ss   17:32   0:00 dbus-daemon --system --fork
root       877  0.0  0.0      0     0 ?        S<   17:32   0:00 [kslowd000]
root       878  0.0  0.0      0     0 ?        S<   17:32   0:00 [kslowd001]
root       901  0.0  0.0      0     0 ?        S    17:32   0:00 [hd-audio0]
root       914  0.0  0.0      0     0 ?        S    17:32   0:00 [hd-audio1]
root       919  0.0  0.0  76588  3492 ?        Ssl  17:32   0:00 gdm-binary
avahi      955  0.0  0.0  34048  1672 ?        S    17:32   0:00 avahi-daemon: running [adam-desktop.local]
avahi      956  0.0  0.0  33920   572 ?        Ss   17:32   0:00 avahi-daemon: chroot helper
root       961  0.0  0.0   4088   608 ?        Ss   17:32   0:00 /bin/sh -e /proc/self/fd/12
mythtv     964  0.0  0.6 459068 25808 ?        Sl   17:32   0:00 /usr/bin/mythbackend --logfile /var/log/mythtv/mythbackend.log --user mythtv
root       987  0.0  0.1  87556  4080 ?        Ssl  17:32   0:00 NetworkManager
mysql      997  0.0  0.6 245184 26924 ?        Ssl  17:32   0:00 /usr/sbin/mysqld
root      1004  0.0  0.0 120452  3628 ?        Sl   17:32   0:00 /usr/sbin/console-kit-daemon --no-daemon
root      1009  0.0  0.0  57856  2528 ?        S    17:32   0:00 /usr/sbin/modem-manager
root      1012  0.0  0.0  28344  2100 ?        S    17:32   0:00 /sbin/wpa_supplicant -u -s
root      1013  0.0  0.0   6548  1112 ?        S    17:32   0:00 /sbin/dhclient -d -sf /usr/lib/NetworkManager/nm-dhcp-client.action -pf /var/run/dhclient-eth0.pid -lf /var/lib/dhcp3/dhclient-fb1b9e25-70bc-4dac-af7c-e4bfeee52463-eth0.lease -cf /var/run/nm-dhclient-eth0.conf eth0
root      1083  0.0  0.1  93452  4056 ?        Sl   17:32   0:00 /usr/lib/gdm/gdm-simple-slave --display-id /org/gnome/DisplayManager/Display1
root      1085  0.0  0.0  17452  1340 ?        S<   17:32   0:00 udevd --daemon
root      1105  5.7  3.7 263588 151824 tty7    Ss+  17:32   0:37 /usr/bin/X :0 -nr -verbose -auth /var/run/gdm/auth-for-gdm-DaFk5K/database -nolisten tcp vt7
root      1111  0.0  0.0  94296  1344 ?        S    17:32   0:00 smbd -F
root      1133  0.0  0.0      0     0 ?        S    17:32   0:00 [firegl]
root      1211  0.0  0.0   6072   656 tty4     Ss+  17:32   0:00 /sbin/getty -8 38400 tty4
root      1216  0.0  0.0   6072   652 tty5     Ss+  17:32   0:00 /sbin/getty -8 38400 tty5
root      1222  0.0  0.0   6072   648 tty2     Ss+  17:32   0:00 /sbin/getty -8 38400 tty2
root      1223  0.0  0.0   6072   652 tty3     Ss+  17:32   0:00 /sbin/getty -8 38400 tty3
root      1225  0.0  0.0   6072   652 tty6     Ss+  17:32   0:00 /sbin/getty -8 38400 tty6
root      1228  0.0  0.0   4552  1176 ?        Ss   17:32   0:00 acpid -c /etc/acpi/events -s /var/run/acpid.socket
root      1232  0.0  0.0  21068  1016 ?        Ss   17:32   0:00 cron
daemon    1233  0.0  0.0  18876   456 ?        Ss   17:32   0:00 atd
root      1248  0.0  0.0  11272   644 ?        Ss   17:32   0:00 /usr/sbin/irqbalance
root      1335  0.0  0.1 165016  5036 ?        Sl   17:32   0:00 /usr/sbin/libvirtd -d
root      1350  0.0  0.0   6256   392 ?        Ss   17:32   0:00 /usr/sbin/dhcrelay3 -q -i eth0 192.168.1.1
root      1402  0.0  0.0      0     0 ?        S    17:32   0:00 [cifsd]
kernoops  1412  0.0  0.0  22312   984 ?        Ss   17:32   0:00 /usr/sbin/kerneloops
root      1418  0.0  0.0  60532  1776 ?        Ss   17:32   0:00 nmbd -D
uml-net   1506  0.0  0.0   4004   532 ?        S    17:32   0:00 /usr/bin/uml_switch -unix /var/run/uml-utilities/uml_switch.ctl
nobody    1511  0.0  0.0  21420   920 ?        S    17:32   0:00 dnsmasq --strict-order --bind-interfaces --pid-file=/var/run/libvirt/network/default.pid --conf-file=  --listen-address 192.168.122.1 --except-interface lo --dhcp-range 192.168.122.2,192.168.122.254 --dhcp-lease-max=253
ntp       1551  0.0  0.0  27852  1560 ?        Ss   17:32   0:00 /usr/sbin/ntpd -p /var/run/ntpd.pid -g -u 117:125
root      1571  0.0  0.0  17452  1340 ?        S<   17:32   0:00 udevd --daemon
root      1607  0.0  0.0  65712  1512 ?        Ss   17:32   0:00 /usr/sbin/winbindd
root      1627  0.0  0.0  65824  1680 ?        S    17:32   0:00 /usr/sbin/winbindd
root      1631  0.0  0.0  27428  2096 ?        S<s  17:32   0:00 /usr/sbin/bluetoothd --udev
root      1666  0.0  0.0  75388  3104 ?        Ss   17:32   0:00 /usr/sbin/cupsd -C /etc/cups/cupsd.conf
root      1670  0.0  0.0      0     0 ?        S<   17:32   0:00 [krfcommd]
root      1898  0.0  0.0   6072   652 tty1     Ss+  17:32   0:00 /sbin/getty -8 38400 tty1
root      1901  0.0  0.0  95236  3352 ?        Sl   17:32   0:00 /usr/lib/gdm/gdm-session-worker
adam      1915  0.0  0.1 167312  7724 ?        Ssl  17:32   0:00 gnome-session
adam      1956  0.0  0.0  11928   412 ?        Ss   17:32   0:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session gnome-session
adam      1959  0.0  0.0  26252   820 ?        S    17:32   0:00 /usr/bin/dbus-launch --exit-with-session gnome-session
adam      1960  0.0  0.0  24208  1668 ?        Ss   17:32   0:00 /bin/dbus-daemon --fork --print-pid 5 --print-address 9 --session
adam      1963  0.0  0.1  46116  5712 ?        S    17:32   0:00 /usr/lib/libgconf2-4/gconfd-2
adam      1970  0.1  1.1 374196 45460 ?        Ss   17:32   0:01 /usr/lib/gnome-settings-daemon/gnome-settings-daemon
adam      1972  0.0  0.0  77948  2976 ?        SLl  17:32   0:00 gnome-keyring-daemon --start --components=pkcs11
adam      1976  0.0  0.0  47984  2528 ?        S    17:33   0:00 /usr/lib/gvfs/gvfsd
adam      1981  0.0  0.0  78016  2752 ?        Ssl  17:33   0:00 /usr/lib/gvfs//gvfs-fuse-daemon /home/adam/.gvfs
adam      1987  0.3  0.8 255020 36340 ?        S    17:33   0:02 compiz
adam      1996  0.0  0.3 237540 13104 ?        S    17:33   0:00 nm-applet --sm-disable
adam      1999  0.0  0.2 201648 11324 ?        S    17:33   0:00 bluetooth-applet
adam      2000  0.0  0.2 176012  8980 ?        S    17:33   0:00 gnome-power-manager
adam      2001  0.0  0.5 585780 22184 ?        S    17:33   0:00 nautilus
adam      2002  0.1  0.4 259940 18036 ?        S    17:33   0:00 gnome-panel
adam      2003  0.0  0.1 161868  7028 ?        S    17:33   0:00 /usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1
adam      2009  0.0  0.1 221184  5072 ?        S<sl 17:33   0:00 /usr/bin/pulseaudio --start --log-target=syslog
rtkit     2011  0.0  0.0 109168  1304 ?        SNl  17:33   0:00 /usr/lib/rtkit/rtkit-daemon
root      2015  0.0  0.1  54220  4412 ?        S    17:33   0:00 /usr/lib/policykit-1/polkitd
adam      2019  0.0  0.0  96640  3504 ?        S    17:33   0:00 /usr/lib/pulseaudio/pulse/gconf-helper
root      2022  0.0  0.0  53584  3080 ?        S    17:33   0:00 /usr/lib/upower/upowerd
109       2064  0.0  0.1  46848  5104 ?        Ssl  17:33   0:00 /usr/sbin/hald
root      2065  0.0  0.0  22308  1392 ?        S    17:33   0:00 hald-runner
adam      2077  0.0  0.0 153972  3888 ?        S    17:33   0:00 /usr/lib/gvfs/gvfs-gdu-volume-monitor
root      2093  0.0  0.0  65776  3680 ?        Sl   17:33   0:00 /usr/lib/udisks/udisks-daemon
root      2094  0.0  0.0  46684   944 ?        S    17:33   0:00 udisks-daemon: polling /dev/sr0
root      2095  0.0  0.0  24428  1300 ?        S    17:33   0:00 hald-addon-input: Listening on /dev/input/event4 /dev/input/event3 /dev/input/event0 /dev/input/event1 /dev/input/event6
root      2098  0.0  0.0  24420  1280 ?        S    17:33   0:00 /usr/lib/hal/hald-addon-rfkill-killswitch
root      2113  0.0  0.0  24424  1416 ?        S    17:33   0:00 hald-addon-storage: polling /dev/sr0 (every 2 sec)
root      2121  0.0  0.0  24436  1288 ?        S    17:33   0:00 /usr/lib/hal/hald-addon-cpufreq
109       2122  0.0  0.0  26260  1248 ?        S    17:33   0:00 hald-addon-acpi: listening on acpid socket /var/run/acpid.socket
adam      2124  0.0  0.0  69204  2728 ?        Sl   17:33   0:00 /usr/lib/gvfs/gvfs-afc-volume-monitor
adam      2127  0.0  0.0  55288  2680 ?        S    17:33   0:00 /usr/lib/gvfs/gvfs-gphoto2-volume-monitor
adam      2128  0.0  0.0 171504  3148 ?        Ss   17:33   0:00 gnome-screensaver
adam      2130  0.0  0.0  52472  3184 ?        S    17:33   0:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.8 /org/gtk/gvfs/exec_spaw/0
adam      2132  0.0  0.1 218316  4140 ?        Ssl  17:33   0:00 /usr/lib/bonobo-activation/bonobo-activation-server --ac-activate --ior-output-fd=19
adam      2139  0.0  0.3 256812 14964 ?        S    17:33   0:00 /usr/lib/gnome-panel/wnck-applet --oaf-activate-iid=OAFIID:GNOME_Wncklet_Factory --oaf-ior-fd=18
adam      2140  0.0  0.0   4088   592 ?        Ss   17:33   0:00 /bin/sh -c /usr/bin/compiz-decorator
adam      2141  0.0  0.2 176760 11336 ?        S    17:33   0:00 /usr/bin/gtk-window-decorator
adam      2150  0.0  0.3 240948 12800 ?        S    17:33   0:00 /usr/lib/gnome-applets/trashapplet --oaf-activate-iid=OAFIID:GNOME_Panel_TrashApplet_Factory --oaf-ior-fd=21
adam      2167  0.0  0.3 211672 12156 ?        S    17:33   0:00 /usr/lib/gnome-applets/cpufreq-applet --oaf-activate-iid=OAFIID:GNOME_CPUFreqApplet_Factory --oaf-ior-fd=18
adam      2169  0.0  0.2 208192 10392 ?        S    17:33   0:00 /usr/lib/gnome-panel/notification-area-applet --oaf-activate-iid=OAFIID:GNOME_NotificationAreaApplet_Factory --oaf-ior-fd=28
adam      2171  0.0  0.4 418168 18512 ?        S    17:33   0:00 /usr/lib/gnome-panel/clock-applet --oaf-activate-iid=OAFIID:GNOME_ClockApplet_Factory --oaf-ior-fd=40
adam      2173  0.0  0.3 271272 15008 ?        S    17:33   0:00 /usr/lib/indicator-applet/indicator-applet --oaf-activate-iid=OAFIID:GNOME_IndicatorApplet_Factory --oaf-ior-fd=34
adam      2174  0.0  0.3 334652 15084 ?        S    17:33   0:00 /usr/lib/indicator-applet/indicator-applet-session --oaf-activate-iid=OAFIID:GNOME_FastUserSwitchApplet_Factory --oaf-ior-fd=46
adam      2179  0.0  0.0  41724  2340 ?        S    17:33   0:00 /usr/lib/gvfs/gvfsd-metadata
adam      2181  0.0  0.1 143824  5664 ?        S    17:33   0:00 /usr/lib/indicator-me/indicator-me-service
adam      2183  0.0  0.1 140840  5536 ?        S    17:33   0:00 /usr/lib/indicator-session/indicator-session-service
adam      2185  0.0  0.2 176648  8164 ?        S    17:33   0:00 /usr/lib/gnome-disk-utility/gdu-notification-daemon
adam      2187  0.0  0.1 138088  4972 ?        S    17:33   0:00 /usr/lib/indicator-messages/indicator-messages-service
adam      2189  0.0  0.1 146872  4892 ?        S    17:33   0:00 /usr/lib/indicator-application/indicator-application-service
adam      2191  0.0  0.1 219004  5364 ?        S    17:33   0:00 /usr/lib/indicator-sound/indicator-sound-service
adam      2201  0.0  0.1 150472  7140 ?        S    17:33   0:00 /usr/lib/gnome-user-share/gnome-user-share
adam      2204  0.0  0.0  47852  2604 ?        S    17:33   0:00 /usr/lib/gvfs/gvfsd-burn --spawner :1.8 /org/gtk/gvfs/exec_spaw/1
adam      2206  0.0  0.0  79664  3260 ?        S    17:33   0:00 /usr/bin/obex-data-server --no-daemon 
root      2226  0.0  0.0  65728  1780 ?        S    17:33   0:00 /usr/sbin/winbindd
root      2229  0.0  0.0      0     0 ?        S<   17:33   0:00 [khidpd_046db003]
adam      2238  0.2  0.3 214912 16104 ?        Rl   17:33   0:01 gnome-terminal
adam      2239  0.0  0.0  14480   812 ?        S    17:33   0:00 gnome-pty-helper
adam      2240  0.0  0.1  21732  4544 pts/0    Ss   17:33   0:00 bash
adam      2256  0.0  0.6 383016 27964 ?        Sl   17:33   0:00 /usr/bin/python /usr/bin/gwibber-service
adam      2261  0.1  0.4 181720 18956 ?        SLl  17:33   0:00 /usr/bin/python /usr/lib/desktopcouch/desktopcouch-service
adam      2262  0.0  0.3 430060 14008 ?        Sl   17:33   0:00 /usr/lib/evolution/2.28/evolution-alarm-notify
adam      2263  0.0  0.6 276992 28200 ?        S    17:33   0:00 python /usr/share/system-config-printer/applet.py
adam      2272  0.0  0.3 353380 13796 ?        Sl   17:33   0:00 /usr/lib/evolution/2.28/evolution-exchange-storage --oaf-activate-iid=OAFIID:GNOME_Evolution_Exchange_Connector_CalFactory:1.2 --oaf-ior-fd=34
adam      2277  0.0  0.2 456348 11028 ?        Sl   17:33   0:00 /usr/lib/evolution/evolution-data-server-2.28 --oaf-activate-iid=OAFIID:GNOME_Evolution_DataServer_CalFactory:1.2 --oaf-ior-fd=35
adam      2319  1.0  1.0 153248 43748 ?        SLl  17:33   0:06 /usr/bin/python /usr/lib/ubuntuone-client/ubuntuone-syncdaemon
root      2342  0.0  0.0      0     0 ?        S<   17:33   0:00 [khidpd_046db307]
adam      2383  0.0  0.0   4088   672 ?        S    17:33   0:00 /bin/sh -e /usr/bin/couchdb -n -a \"/etc/couchdb/default.ini\" -a \"/etc/xdg/desktop-couch/compulsory-auth.ini\" -a \"/home/adam/.config/desktop-couch/desktop-couchdb.ini\" -b -r 0 -p /home/adam/.cache/desktop-couch/desktop-couchdb.pid -o /home/adam/.cache/desktop-couch/desktop-couchdb.stdout -e /home/adam/.cache/desktop-couch/desktop-couchdb.stderr -R
adam      2411  0.0  0.0   4088   384 ?        S    17:33   0:00 /bin/sh -e /usr/bin/couchdb -n -a \"/etc/couchdb/default.ini\" -a \"/etc/xdg/desktop-couch/compulsory-auth.ini\" -a \"/home/adam/.config/desktop-couch/desktop-couchdb.ini\" -b -r 0 -p /home/adam/.cache/desktop-couch/desktop-couchdb.pid -o /home/adam/.cache/desktop-couch/desktop-couchdb.stdout -e /home/adam/.cache/desktop-couch/desktop-couchdb.stderr -R
adam      2412  0.4  0.5 134356 22348 ?        Sl   17:33   0:02 /usr/lib/erlang/erts-5.7.4/bin/beam.smp -Bd -K true -- -root /usr/lib/erlang -progname erl -- -home /home/adam -- -noshell -noinput -smp auto -sasl errlog_type error -pa /usr/lib/couchdb/erlang/lib/couch-0.10.0/ebin /usr/lib/couchdb/erlang/lib/mochiweb-r97/ebin /usr/lib/couchdb/erlang/lib/ibrowse-1.5.2/ebin /usr/lib/couchdb/erlang/lib/erlang-oauth/ebin -eval application:load(ibrowse) -eval application:load(oauth) -eval application:load(crypto) -eval application:load(couch) -eval crypto:start() -eval ssl:start() -eval ibrowse:start() -eval couch_server:start([ "/etc/couchdb/default.i
adam      2424  0.0  0.0   3856   512 ?        Ss   17:33   0:00 heart -pid 2412 -ht 11
adam      2475  0.0  0.3 206008 13444 ?        S    17:34   0:00 update-notifier
adam      2479  0.0  0.0  20020  2904 ?        Ss   17:34   0:00 /usr/lib/erlang/lib/ssl-3.10.7/priv/bin/ssl_esock
adam      2480  0.0  0.0  10704   540 ?        Ss   17:34   0:00 inet_gethost 4
adam      2481  0.0  0.0  19084   788 ?        S    17:34   0:00 inet_gethost 4
adam      2501  0.0  0.0   4088   628 ?        S    17:35   0:00 /bin/sh /usr/lib/firefox-3.6.3/firefox
adam      2506  0.0  0.0   4088   652 ?        S    17:35   0:00 /bin/sh /usr/lib/firefox-3.6.3/run-mozilla.sh /usr/lib/firefox-3.6.3/firefox-bin
adam      2510  3.0  2.2 632048 90640 ?        Rl   17:35   0:14 /usr/lib/firefox-3.6.3/firefox-bin
adam      2565  0.0  0.0  15248  1212 pts/0    R+   17:43   0:00 ps -aux
adam@adam-desktop:~$ 

```

The system had not finished loading up yet.
[/LEFT]

---

### Post by J V on 2010-04-12
Don't know why there seems to be so much memory, but again, I don't think boot speed problems occur due to memory as you have more than enough.

Reprofile grub

---

### Post by outleradam on 2010-04-12
> **J V said:**
> Do you need that printer applet?

It looks like a whole bunch of small programs are using large amounts of memory... Nonetheless, why don't you reprofile grub, if you made any hardware changes (Or a plug fell out somewhere) the profile will be wrong so it will need to boot up once and fail then a second time extra slow while it tries to find your hardware again.
I will look up how to reprofile grub, then report back after performing the operation.  I do not *need* the printer, but I was trying to get it to work.  I will see about removing it for now.

---

### Post by outleradam on 2010-04-12
Holy hole in a donut Batman!!!!!   This revived my computer.  Firefox starts in a fraction of a second again and my terminal fires up about as fast as a double click.

```
adam@adam-desktop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3955       1123       2832          0        124        331
-/+ buffers/cache:        666       3289
Swap:         4416          0       4416

```
Solved... 666 used.

Thank you for the reprofiling tip.  I added the word profile to the end of the line starting with "linux".  Memory usage went way down and the computer booted much faster.  It was wasting time caching stuff instead of giving me the UI.

This newest version of ubuntu seems to load alot of junk though...  I may use Boot Up Manger (BUM) to stop some of those BS processes like Gwibber which was included in Ubuntu 10.4.   Thank you very much for all the help!

---

