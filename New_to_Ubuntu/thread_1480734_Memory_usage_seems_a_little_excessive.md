---
title: "Memory usage seems a little excessive"
date: 2010-05-11
forum: New to Ubuntu
---

### Post by Legendary_Bibo on 2010-05-11
I know that firefox and compiz take up quite a bit of ram, but why is xorg, clock applet, and the gnome germinal taking up so much ram? Also for some reason even though I closed gwibber it would sometimes show two gwibbers running.

```
top - 19:03:01 up  1:10,  2 users,  load average: 0.60, 0.49, 0.55
Tasks: 177 total,   2 running, 175 sleeping,   0 stopped,   0 zombie
Cpu(s):  6.2%us,  1.7%sy,  0.0%ni, 92.1%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0
Mem:   3798408k total,  2063000k used,  1735408k free,   156328k buffers
Swap: 11126776k total,        0k used, 11126776k free,   929688k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND       
 1097 root      20   0  326m 177m  29m S   10  4.8   8:49.29 Xorg          
 5290 bibo      20   0  619m  89m  30m S    3  2.4   1:10.57 firefox-bin   
 5323 bibo      20   0 71264  13m 9668 S    1  0.4   0:09.22 npviewer.bin  
 5679 bibo      20   0  212m  15m  10m S    1  0.4   0:00.21 gnome-terminal
 5698 bibo      20   0 19216 1424 1028 R    1  0.0   0:00.05 top           
 1437 root      20   0 46684  932  576 S    0  0.0   0:03.33 udisks-daemon 
 1514 bibo      20   0 29096 1212  944 S    0  0.0   0:02.63 syndaemon     
 1532 bibo      20   0  296m  15m  11m S    0  0.4   0:01.05 clock-applet  
 1844 bibo      20   0  278m  51m 9920 S    0  1.4   0:42.57 compiz        
    1 root      20   0 23704 1928 1264 S    0  0.1   0:00.54 init          
    2 root      20   0     0    0    0 S    0  0.0   0:00.00 kthreadd      
    3 root      RT   0     0    0    0 S    0  0.0   0:00.02 migration/0   
    4 root      20   0     0    0    0 S    0  0.0   0:00.05 ksoftirqd/0   
    5 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/0    
    6 root      RT   0     0    0    0 S    0  0.0   0:00.02 migration/1   
    7 root      20   0     0    0    0 S    0  0.0   0:00.74 ksoftirqd/1   
    8 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/1 
```

---

### Post by admiralspark on 2010-05-11
I'm going to guess you're using 10.04. It's been discussed many times on the forums recently, 10.04 seems to be bloated much more than 9.04/9.10, in the same way as comparing bloated Vista to XP Professional. Xorg is the basics of what makes the desktop viewable and navigable, gnome terminal....I can't really explain, maybe because it's running Top, and as for firefox: do you have any addons installed?

---

### Post by ubunterooster on 2010-05-11
```
top - 22:14:01 up  1:35,  2 users,  load average: 0.54, 0.42, 0.52
Tasks: 190 total,   1 running, 189 sleeping,   0 stopped,   0 zombie
Cpu(s):  1.8%us,  1.6%sy,  0.0%ni, 96.6%id,  0.0%wa,  0.0%hi,  0.0%si,  0
Mem:   7674856k total,  1524196k used,  6150660k free,    11564k buffers
Swap:        0k total,        0k used,        0k free,   894592k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND     
 1860 root      20   0  230m  82m  24m S    2  1.1   7:17.54 Xorg        
 6256 ubuntero  20   0  214m  14m  10m S    1  0.2   0:00.68 gnome-termin 4782 ubuntero  20   0  702m 111m  43m S    1  1.5   1:38.76 firefox-bin 
  336 root      20   0     0    0    0 S    1  0.0   0:12.72 usb-storage  2072 ubuntero  20   0  177m 9756 7296 S    1  0.1   0:19.25 parcellite  
    4 root      20   0     0    0    0 S    0  0.0   0:02.53 ksoftirqd/0  1047 root      20   0 21068 1012  768 S    0  0.0   0:00.02 cron        
 1960 root      20   0 24428 1292 1080 S    0  0.0   0:01.22 hald-addon-s 2105 ubuntero  20   0  258m  15m  11m S    0  0.2   0:09.28 wnck-applet 
 6274 ubuntero  20   0 19216 1436 1028 R    0  0.0   0:00.25 top             1 root      20   0 23788 1952 1244 S    0  0.0   0:00.51 init        
    2 root      20   0     0    0    0 S    0  0.0   0:00.00 kthreadd        3 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/0 
    5 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/0      6 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/1 
    7 root      20   0     0    0    0 S    0  0.0   0:00.49 ksoftirqd/1     8 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/1  
```My install is a minimalistic one. Nothing looks out of place on yours.

---

### Post by Legendary_Bibo on 2010-05-11
I'm just using firefox as it came. The only thing I changed was the theme, but I doubt that's a problem. I always heard that firefox and Compiz are memory hogs so I can live with that. I'm just trying to figure out why my linux is using a little more memory than Vista did. I'm guessing it'll be patched. It doesn't bother me as long as it's not a critical issue, it's never slowed down on me.

---

### Post by admiralspark on 2010-05-11
```
 PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 2322 admirals  20   0  350m  83m  27m S  0.3  6.7   2:03.95 firefox-bin        
 2525 admirals  20   0  2544 1212  908 R  0.3  0.1   0:00.03 top                
    1 root      20   0  2800 1616 1164 S  0.0  0.1   0:00.32 init               
    2 root      20   0     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      20   0     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0        
    5 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    6 root      20   0     0    0    0 S  0.0  0.0   0:00.17 events/0           
    7 root      20   0     0    0    0 S  0.0  0.0   0:00.00 cpuset             
    8 root      20   0     0    0    0 S  0.0  0.0   0:00.00 khelper            
    9 root      20   0     0    0    0 S  0.0  0.0   0:00.00 netns              
   10 root      20   0     0    0    0 S  0.0  0.0   0:00.00 async/mgr          
   11 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pm                 
   12 root      20   0     0    0    0 S  0.0  0.0   0:00.00 sync_supers        
   13 root      20   0     0    0    0 S  0.0  0.0   0:00.00 bdi-default        
   14 root      20   0     0    0    0 S  0.0  0.0   0:00.00 kintegrityd/0      
   15 root      20   0     0    0    0 S  0.0  0.0   0:00.03 kblockd/0        
```

I usually notice that Ubuntu One uses alot of memory at startup, even though it's broken..

---

### Post by Legendary_Bibo on 2010-05-11
> **ubunterooster said:**
> ```
top - 22:14:01 up  1:35,  2 users,  load average: 0.54, 0.42, 0.52
Tasks: 190 total,   1 running, 189 sleeping,   0 stopped,   0 zombie
Cpu(s):  1.8%us,  1.6%sy,  0.0%ni, 96.6%id,  0.0%wa,  0.0%hi,  0.0%si,  0
Mem:   7674856k total,  1524196k used,  6150660k free,    11564k buffers
Swap:        0k total,        0k used,        0k free,   894592k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND     
 1860 root      20   0  230m  82m  24m S    2  1.1   7:17.54 Xorg        
 6256 ubuntero  20   0  214m  14m  10m S    1  0.2   0:00.68 gnome-termin 4782 ubuntero  20   0  702m 111m  43m S    1  1.5   1:38.76 firefox-bin 
  336 root      20   0     0    0    0 S    1  0.0   0:12.72 usb-storage  2072 ubuntero  20   0  177m 9756 7296 S    1  0.1   0:19.25 parcellite  
    4 root      20   0     0    0    0 S    0  0.0   0:02.53 ksoftirqd/0  1047 root      20   0 21068 1012  768 S    0  0.0   0:00.02 cron        
 1960 root      20   0 24428 1292 1080 S    0  0.0   0:01.22 hald-addon-s 2105 ubuntero  20   0  258m  15m  11m S    0  0.2   0:09.28 wnck-applet 
 6274 ubuntero  20   0 19216 1436 1028 R    0  0.0   0:00.25 top             1 root      20   0 23788 1952 1244 S    0  0.0   0:00.51 init        
    2 root      20   0     0    0    0 S    0  0.0   0:00.00 kthreadd        3 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/0 
    5 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/0      6 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/1 
    7 root      20   0     0    0    0 S    0  0.0   0:00.49 ksoftirqd/1     8 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/1  
```My install is a minimalistic one. Nothing looks out of place on yours.

Your computer is using over 6gb of your ram, and that's a minimalistic install? :confused:

---

### Post by ubunterooster on 2010-05-11
I think that reads 6GB free of 8Gb total.

---

### Post by Legendary_Bibo on 2010-05-11
oh you're absolutely right. Still isn't 2gb or ram just for the basic function of the operating system quite a bit though?

---

### Post by ubunterooster on 2010-05-11
Before I went minimal, I was using up 5GB. Yes it is high but with this new computer it's fast enough to overlook any RAM usage

---

### Post by QIII on 2010-05-11
Why does the "Lucid is bloated" myth persist?  How is it "bloated"?
 
 I am running Firefox, have the system monitor open and one of the foster  kids is watching a DVD on one of the monitors.
 
 According to htop, I'm using 1.4GB.  That's less than Bibo is reporting.

---

### Post by Legendary_Bibo on 2010-05-11
My dad's computer only uses 1gb and he's running Windows 7. I thought linux was great at resource management.

---

### Post by ubunterooster on 2010-05-11
If I take out some of my RAM Ubuntu uses less of what is left; it seems to adapt for what it has to use

---

### Post by Legendary_Bibo on 2010-05-11
hmmm according to htop I'm using about 1gb, but according to top I'm using over 2gb. Errr...what is the most truthful system monitor?

---

### Post by lavinog on 2010-05-11
To anyone that thinks they are using a lot of ram look at what free reports.

Using top:
```

top - 21:41:28 up  1:00,  3 users,  load average: 0.62, 0.61, 0.66
Tasks: 150 total,   1 running, 149 sleeping,   0 stopped,   0 zombie
Cpu(s): 16.0%us,  3.2%sy,  0.0%ni, 78.3%id,  2.3%wa,  0.2%hi,  0.0%si,  0.0%st
Mem:   1413384k total,   835784k used,   577600k free,    53996k buffers
Swap:   522072k total,        0k used,   522072k free,   509436k cached

```
It looks like I am using 835Mb of ram.  I am, but it isn't like you think.  509Mb is disk cache (used to boost performance)

using free:
```

free -m
             total       used       free     shared    buffers     cached
Mem:          1380        816        563          0         52        497
-/+ buffers/cache:        **266**       1114
Swap:          509          0        509

```
The bold 266 is the number you should look at.  That shows that the system and programs are using 266Mb of memory.

many users recommend using htop over top because it gives you a colored bar graph.

---

### Post by ubunterooster on 2010-05-11
htop is very optimistic in comparison for me also...

Watching the two together while starting programs, I am inclined to trust htop which agrees with free


Edit: free= ```
ubunterooster@Rooster:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          7494        852       6642          0         43        315
-/+ buffers/cache:        493       7001
Swap:            0          0          0
ubunterooster@Rooster:~$
```

---

### Post by QIII on 2010-05-11
_Bibo --

*nix systems use memory differently than Windows.

What appears to be "used" may actually be available.  The OS often  caches what is no longer being "used" to have it immediately available  as needed, say you start using an application again.

Try something like Solaris.  It looks like nearly all the memory is  being "used".  It's not.  "Unused memory is wasted memory."  If the OS  caches it for immediate use, it can be addressed more quickly.

Over time, that cache often gets larger as you do more and more.  It's cached, not tied up.  If the OS needs it for something else, it's there to use.

top is showing you cached.  htop isn't.  Neither is the System Monitor.

---

### Post by lavinog on 2010-05-11
A couple of other things to mention:
There was a memory leak found in xorg.  I don't have the bug report in front of me, but I think a fix was rolled out so make sure you applied the latest updates.
Edit: found bug report: [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/565981](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/565981)  It looks like this is fixed now.

npviewer.bin is adobe flash.  If you are using a 64bit version of ubuntu, you should install the 64bit flash instead of the one provided in the repos.  Here is a link for more info: [http://ubuntuforums.org/showthread.php?t=1358591](http://ubuntuforums.org/showthread.php?t=1358591)

Occasionally ureadahead does a trace during a boot (usually after updates are applied)  When this happens, the system will use about 128Mb more than normal until the next boot.  More info here: [http://ubuntuforums.org/showthread.php?t=1363165](http://ubuntuforums.org/showthread.php?t=1363165)

There is a saying amoung linux users: "unused memory is wasted memory"
Edit: ha, QIII beat me to it.

---

### Post by Legendary_Bibo on 2010-05-11
hmmm...yeah I probably won't use top anymore if it's that off

my free -m
```
             total       used       free     shared    buffers     cached
Mem:          3709       2208       1500          0        152        924
-/+ buffers/cache:       1131       2577
Swap:        10865          0      10865

```

my htop says 1140MB are being used

and top is saying
```
top - 19:54:34 up  2:01,  2 users,  load average: 0.58, 0.45, 0.45
Tasks: 177 total,   2 running, 175 sleeping,   0 stopped,   0 zombie
Cpu(s): 10.3%us,  4.7%sy,  0.3%ni, 84.7%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0
Mem:   3798408k total,  2271444k used,  1526964k free,   156360k buffers
Swap: 11126776k total,        0k used, 11126776k free,   946368k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND       
 1097 root      20   0  326m 177m  29m R   19  4.8  13:27.52 Xorg          
 1398 bibo      20   0  279m  25m  13m S    3  0.7   0:15.85 gnome-panel   
 5851 bibo      20   0  617m 103m  30m S    3  2.8   2:05.66 firefox-bin   
 1844 bibo      20   0  278m  51m 9920 S    2  1.4   1:00.52 compiz        
 5886 bibo      20   0  104m  15m  10m S    2  0.4   0:51.96 npviewer.bin  
 6168 bibo      20   0  212m  15m  10m S    2  0.4   0:00.26 gnome-terminal
 1690 bibo      30  10 98.6m  15m 2468 S    1  0.4   0:28.41 desktopcouch-s
 6187 bibo      20   0 19216 1420 1028 R    1  0.0   0:00.06 top           
 1588 bibo      20   0 98288  16m 4392 S    0  0.4   0:25.09 desktopcouch-s
    1 root      20   0 23704 1928 1264 S    0  0.1   0:00.54 init          
    2 root      20   0     0    0    0 S    0  0.0   0:00.00 kthreadd      
    3 root      RT   0     0    0    0 S    0  0.0   0:00.02 migration/0   
    4 root      20   0     0    0    0 S    0  0.0   0:00.11 ksoftirqd/0   
    5 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/0    
    6 root      RT   0     0    0    0 S    0  0.0   0:00.02 migration/1   
    7 root      20   0     0    0    0 S    0  0.0   0:01.18 ksoftirqd/1   
    8 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/1    

```

So is some of that memory my hard disk space or is it just trying to reserve that RAM for it's uses?

---

### Post by ubunterooster on 2010-05-11
> **QIII said:**
> What appears to be "used" may actually be available.  The OS often  caches what is no longer being "used" to have it immediately available  as needed, say you start using an application again.

Try something like Solaris.  It looks like nearly all the memory is  being "used".  It's not.  "Unused memory is wasted memory."  If the OS  caches it for immediate use, it can be addressed more quickly.

Over time, that cache often gets larger as you do more and more.  It's cached, not tied up.  If the OS needs it for something else, it's there to use.

top is showing you cached.  htop isn't.  Neither is the System Monitor.
> **ubunterooster said:**
> If I take out some of my RAM Ubuntu uses  less of what is left; it seems to adapt for what it has to useCool! so it _is_ adapting!

---

### Post by Legendary_Bibo on 2010-05-11
> **QIII said:**
> _Bibo --

*nix systems use memory differently than Windows.

What appears to be "used" may actually be available.  The OS often  caches what is no longer being "used" to have it immediately available  as needed, say you start using an application again.

Try something like Solaris.  It looks like nearly all the memory is  being "used".  It's not.  "Unused memory is wasted memory."  If the OS  caches it for immediate use, it can be addressed more quickly.

Over time, that cache often gets larger as you do more and more.  It's cached, not tied up.  If the OS needs it for something else, it's there to use.

top is showing you cached.  htop isn't.  Neither is the System Monitor.

Ahh I see what you're saying, it uses as much RAM as possible to run faster, and frees it up for anything else that needs it.

---

### Post by WinterRain on 2010-05-12
> **Legendary_Bibo said:**
> My dad's computer only uses 1gb and he's running Windows 7. I thought linux was **great at resource management**.

It is. Unused memory is wasted memory. I'll never understand why people get 4gb+ of ram, then want it to use as little as possible. Plus, if you are using 64bit ubuntu, it will use more than 32bit. 

Secondly, if you go to system>administration>system monitor>resources tab, it will give you an accurate reading of memory being used. Using more memory means better performance.

---

### Post by Legendary_Bibo on 2010-05-12
Well yeah you bring up a valid point, but come to think of I think why I thought it should be that way is I'm used to having to check if Windows had enough ram free for me to play a game or do some other task.

---

### Post by lavinog on 2010-05-12
> **WinterRain said:**
> It is. Unused memory is wasted memory. I'll never understand why people get 4gb+ of ram, then want it to use as little as possible. Plus, if you are using 64bit ubuntu, it will use more than 32bit. 


I suspect (but have no knowledge of) that there could be a way to save power by not using all available memory.
Since memory needs to be refreshed constantly, it would make sense to avoid refreshing memory addresses not in use when the system needs to conserve power.

If it doesn't already exist, I can see utilizing a way to lock out memory addresses to conserve power. If a system has 4g of memory, turn off 2g when on battery.  It would be like how some cars can turn off a cylinder or two when cruising to conserve fuel.

I guess implementing this when the technology is available could be as simple as flushing the cache and turning off the unused memory.

Just thought I mention this as a future reason to minimize memory usage.

---

### Post by ubunterooster on 2010-05-12
> **lavinog said:**
> I suspect (but have no knowledge of) that there could be a way to save power by not using all available memory.
Since memory needs to be refreshed constantly, it would make sense to avoid refreshing memory addresses not in use when the system needs to conserve power.

If it doesn't already exist, I can see utilizing a way to lock out memory addresses to conserve power. If a system has 4g of memory, turn off 2g when on battery.  It would be like how some cars can turn off a cylinder or two when cruising to conserve fuel.

I guess implementing this when the technology is available could be as simple as flushing the cache and turning off the unused memory.

Just thought I mention this as a future reason to minimize memory usage.
True; I have a really fast PC underclocked to use only 45 watts. It's all about power to me

---

### Post by Legendary_Bibo on 2010-05-12
oh yeah that would explain why my laptop's battery drains so quickly. Meh I'm about the performance anyways.

---

### Post by Papa.Coen on 2010-05-13
Returning to npviewer.bin: this seems to be a 64bit wrapper for the Firefox flash plugin (still 32 bit) next to claiming lots of memory I suspect the plugin of crashing/freezing (beyond alt/prtscn/RESUB) my computer.

I've disabled the plugin in Firefox, uninstalled the Flash installer script (just in case) and currently waiting for a crash. Or not.

---

