---
title: "system hang"
date: 2010-05-14
forum: New to Ubuntu
---

### Post by mohhas on 2010-05-14
hello every body 
I'm new user for "linux 10.04 desktop lts ", it is fine but l have problem
system hanging ( but still mouse move & some program active) & i can open any thing on desktop , but all other application &system&place ,date,shutdown,,,, all in the top of desktop ( tool bar panel) don't respond .it  always occur when playing videos with movie player
any help  thanks in advance

---

### Post by Sealbhach on 2010-05-14
How much memory (RAM) have you got?

Run "top" in a terminal to see if something is hogging all the resources.

.

---

### Post by mohhas on 2010-05-14
> **Sealbhach said:**
> How much memory (RAM) have you got?

Run "top" in a terminal to see if something is hogging all the resources.

.

thanks I'm very new . this is report
top - 10:15:26 up 8 min,  2 users,  load average: 0.45, 0.44, 0.24
Tasks: 147 total,   1 running, 146 sleeping,   0 stopped,   0 zombie
Cpu(s):  1.0%us,  0.5%sy,  0.0%ni, 98.5%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   1018348k total,   536084k used,   482264k free,    35872k buffers
Swap:   538616k total,        0k used,   538616k free,   261024k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 1427 mohhassa  20   0 77592  25m  11m S    1  2.5   0:18.76 operapluginwrap    
 1334 mohhassa  20   0  127m  59m  16m S    1  6.0   0:19.77 opera              
  828 root      20   0 45888  15m 9244 S    0  1.5   0:23.26 Xorg               
 1550 mohhassa  20   0 62932  14m  10m S    0  1.4   0:02.16 gnome-terminal     
 1569 mohhassa  20   0  2544 1192  908 R    0  0.1   0:00.35 top                
    1 root      20   0  2796 1632 1188 S    0  0.2   0:00.52 init               
    2 root      20   0     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      20   0     0    0    0 S    0  0.0   0:00.00 ksoftirqd/0        
    5 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/1        
    7 root      20   0     0    0    0 S    0  0.0   0:00.00 ksoftirqd/1        
    8 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      20   0     0    0    0 S    0  0.0   0:00.00 events/0           
   10 root      20   0     0    0    0 S    0  0.0   0:00.00 events/1           
   11 root      20   0     0    0    0 S    0  0.0   0:00.00 cpuset             
   12 root      20   0     0    0    0 S    0  0.0   0:00.00 khelper

---

### Post by Sealbhach on 2010-05-14
Right, nothing too unusual there. You said it only happens with movie player running? Maybe install VLC and play some movies and see if the problem is the same.

.

---

### Post by ukripper on 2010-05-14
can you post output of the following commands:
```
cat /var/log/messages | grep "ERROR"
```

```
dmesg
```

---

### Post by mohhas on 2010-05-14
thanks with vlc player ok

---

### Post by parn on 2010-05-14
Do you mind sharing the specs of your PC?

I am using a Acer TravelMate, 2GB RAM and ATI Radeon Mobility X700 with 128MB RAM.

My system did hang on me a few times (~3 times) while watching movies (using mplayer and flash plugin).

While running flash movies that are of high quality (spepisode.org South Park Season 14) the stupid flash object is using 60-70% of the CPU >.<" - click full screen - BOOM!

Same problem with playing HD movies in mplayer/smplayer but I dont get to see the top output because everything hangs all a sudden - turns grey and all.

I then played the movies with VLC from CLI and VLC reports problem with a comment that says (computer too slow?) - and I am not in full screen mode - yet. Switching movies to full screen usually amplifies the problem.

So, whenever I play a movie now, I make sure that nothing else is running >.<" - VLC is more stable, you should give it a try. It jerks but it doesnt hang my system - not yet (fingers crossed)

I think it is the xorg ati driver that is causing me all these problems... and video performance use to be better in karmic - maybe because lucid is actually using an older version of glx.

---

### Post by mohhas on 2010-05-14
> **parn said:**
> Do you mind sharing the specs of your PC?

I am using a Acer TravelMate, 2GB RAM and ATI Radeon Mobility X700 with 128MB RAM.

My system did hang on me a few times (~3 times) while watching movies (using mplayer and flash plugin).

While running flash movies that are of high quality (spepisode.org South Park Season 14) the stupid flash object is using 60-70% of the CPU >.<" - click full screen - BOOM!

Same problem with playing HD movies in mplayer/smplayer but I dont get to see the top output because everything hangs all a sudden - turns grey and all.

I then played the movies with VLC from CLI and VLC reports problem with a comment that says (computer too slow?) - and I am not in full screen mode - yet. Switching movies to full screen usually amplifies the problem.

So, whenever I play a movie now, I make sure that nothing else is running >.<" - VLC is more stable, you should give it a try. It jerks but it doesnt hang my system - not yet (fingers crossed)

I think it is the xorg ati driver that is causing me all these problems... and video performance use to be better in karmic - maybe because lucid is actually using an older version of glx.

thanks  the problem still occurring when i use " multimedia keyboard",, even with vlc .

---

### Post by Sealbhach on 2010-05-14
As parn has suggested, it might be the video driver. To find out what graphics card you have, pleasde do

```
sudo lshw -C display
```

and copy and paste the results here.

.

---

### Post by mohhas on 2010-05-14
> **Sealbhach said:**
> As parn has suggested, it might be the video driver. To find out what graphics card you have, pleasde do

```
sudo lshw -C display
```

and copy and paste the results here.

.

this is
 *-display               
       description: VGA compatible controller
       product: 82945G/GZ Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: msi pm bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:16 memory:d1200000-d127ffff ioport:c000(size=8) memory:c0000000-cfffffff(prefetchable) memory:d1280000-d12bffff

---

### Post by Sealbhach on 2010-05-14
Ok, well there's a thread here where a lot of people are experiencing freeze ups, I would join up with them if I were you, it looks like you're suffering from the same problem. See the thread here: [http://ubuntuforums.org/showthread.php?p=9299944](http://ubuntuforums.org/showthread.php?p=9299944)

.

---

### Post by mohhas on 2010-05-15
any help

---

### Post by Pluscom on 2010-05-15
When I installed Lucid on my laptop everything went well but with my desktop it was a different story.  Simple processes took minutes to happen or simply hung.

It turns out that Lucid uses at least 50% more RAM than the Hardy Heron I had been using.  That did not matter with my laptop (1.8 GB of RAM) but it was a big problem for my desktop (528 MB of RAM).

Is 10.4 going the way of Windows by using more resources than previous versions?  Will this trend continue as new releases come out?

---

### Post by mohhas on 2010-05-15
> **Pluscom said:**
> When I installed Lucid on my laptop everything went well but with my desktop it was a different story.  Simple processes took minutes to happen or simply hung.

It turns out that Lucid uses at least 50% more RAM than the Hardy Heron I had been using.  That did not matter with my laptop (1.8 GB of RAM) but it was a big problem for my desktop (528 MB of RAM).

Is 10.4 going the way of Windows by using more resources than previous versions?  Will this trend continue as new releases come out?

may be!!!!!

---

### Post by Sealbhach on 2010-05-15
> **Pluscom said:**
> 

Is 10.4 going the way of Windows by using more resources than previous versions?  Will this trend continue as new releases come out?

Yes, I think so. I'm finding Lucid with Gnome uses more RAM than any previous release. I wouldn't recommend it to anyone with only 512MB of RAM, I would recommend [Lubuntu]("http://lubuntu.net/") or [Peppermint OS]("http://peppermintos.com/").

Even Xubuntu is getting a little too heavy these days for a machine with 512MB. 

.

---

