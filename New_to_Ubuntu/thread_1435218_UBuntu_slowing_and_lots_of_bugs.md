---
title: "UBuntu slowing and lots of bugs"
date: 2010-03-21
forum: New to Ubuntu
---

### Post by mike101 on 2010-03-21
Hello

I'm new to Linux.

I installed ubuntu 9.10 about a week ago. It was fast at first but has been slowing down gradually over the last week. Now the  windows keep seizing up - so there's no repsonse when I click on them ( that's for applications and firefox windows). 

And now the minimze /maxmize buttons keep disapearing from the top of each window as well.

I've installed quite a few programs nearly all through synaptic package manager or ubuntu software manager. 

The exception was Arachnophilia.jar  (html editor). I've also got the amazon download manager, and wine/crossover. But I've just uninstalled wine.

Anyone got any ideas how I could sort it out. Is it best to reinstall Ubuntu and then be v careful with software or is there something else I can do?

Thanks in advance..
MIke

---

### Post by yazmonium on 2010-03-21
This sounds like a video driver problem.  Are you using NVidia hardware?  If so, download the updated drivers from the website and follow the install instructions.  Make sure you remember to uninstall any old drivers.

---

### Post by Trandre on 2010-03-21
If your computer is slow

open terminal and insert ```
top
```

then display it on this site.


Trandre

---

### Post by mike101 on 2010-03-21
> **Trandre said:**
> If your computer is slow

open terminal and insert ```
top
```then display it on this site.


Trandre

When I try to open a terminal window by clicking on an appelet in the toolbar  the  I get a blank white box. 

I've checked my NVIDIA driver (clicking on , administration then NVIDIA X server settings . It says I have this driver version: 94.43.13.

THe NVIDIA website says no "say no certified downloads for this configuration" when I use their search tool.

Any idea what I can do?

---

### Post by mike101 on 2010-03-21
> **yazmonium said:**
> This sounds like a video driver problem.  Are you using NVidia hardware?  If so, download the updated drivers from the website and follow the install instructions.  Make sure you remember to uninstall any old drivers.

Ok I've changed my NVIDIA driver tot he Ubuntu recommended one
(185.18.36) and I cna now see the terminal screen and the minimize/maximize buttons on all windows. 

I'm not sure if this will improve speed (back to what it was).

---

### Post by mike101 on 2010-03-21
> **Trandre said:**
> If your computer is slow

open terminal and insert ```
top
```then display it on this site.


Trandre

THis is what I can now see when I type TOP into a terminal 

mike@mike-desktop:~$ top

top - 16:10:31 up 8 min,  2 users,  load average: 0.72, 0.31, 0.17
Tasks: 168 total,   2 running, 166 sleeping,   0 stopped,   0 zombie
Cpu(s):  7.3%us,  3.0%sy,  0.2%ni, 89.6%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   2966440k total,   726288k used,  2240152k free,   117252k buffers
Swap:  8731288k total,        0k used,  8731288k free,   293872k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 1621 root      20   0  119m  41m  10m R    8  1.4   1:00.50 Xorg               
 2594 mike      20   0 85088  38m  10m S    6  1.3   0:06.33 compiz.real        
 2610 mike      20   0 18884 7468 5840 S    3  0.3   0:13.08 tracker-applet     
 2821 mike      20   0 40128  14m  10m S    2  0.5   0:01.91 gnome-terminal     
 2595 mike      20   0 45280  21m  15m S    1  0.7   0:05.01 gnome-panel        
 2474 mike      20   0  3176 1476  644 S    0  0.0   0:00.59 dbus-daemon        
 2608 mike      32  12 57908  13m 4460 S    0  0.5   0:01.21 trackerd           
 2632 mike      20   0 29440  14m 8184 S    0  0.5   0:00.41 python             
 2842 mike      20   0  2472 1192  884 R    0  0.0   0:01.81 top                
    1 root      20   0  2664 1548 1128 S    0  0.1   0:00.99 init               
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1        
    7 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksoftirqd/1        
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1

---

### Post by yazmonium on 2010-03-21
You can turn on and off start-up application in system->preferences->startup applications.  turning off unnecessary stuff will help a little.

You can also turn off the desktop effects.  system->preferences->appearance then the visual effects tab.  I have a geforce 8300 and it sucks with the visual effects turned on.

---

### Post by Trandre on 2010-03-21
Your CPU is not overloaded as I can see it, but then again you didnt have so many programs running.

I had a problem myself with my nvidia and the drive Xorg.

Just to check if you have the same problem as I had. Try to open the terminal and run sudo apt-get update

```
sudo apt-get update
```
Does it return a conflict?

You could also open some browsers and other programs and then run top to see if something is eating on your cpu, 

Trandre

---

### Post by mike101 on 2010-03-30
thanks all for the advice updating the NVDIA driver seems to have done the trick!

---

