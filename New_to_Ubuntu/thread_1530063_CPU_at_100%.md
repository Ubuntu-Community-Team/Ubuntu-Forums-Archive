---
title: "CPU at 100%"
date: 2010-07-13
forum: New to Ubuntu
---

### Post by dragon574444 on 2010-07-13
I'm very new to Ubuntu, been using Windows previously. I really like Ubuntu, I'm still getting over the learning curve. Installing apps is mind blowing quite frankly. 

I'm having a problem though, my CPU is at 100%. Fans blasting and I'm kinda worried about it overheating. My PC isn't that great, an Emachines pos. 2.0 GHz Intel Celeron  440 Processor, 1 GB of Ram. Hey, it was free. I have Ubuntu on an 80 GB IDE HDD with a 40 GB slave, and I have a 160 GB SATA HDD with Windows 7. I'm running empathy, FireFox, and RhythmBox. Here's my results of typing top into the terminal.
    
  PID   USER   PR   NI  VIRT  RES  SHR S %CPU%Mem  Time+  COMMAND
  5288 root      20   0  8052 4332 2048 R 74.2  0.4  20:04.57 backend            
5429 joshua    20   0  280m  59m  32m S  6.6  6.0   0:54.15 rhythmbox           
5514 joshua    20   0 44336  13m 9996 S  6.6  1.3   0:01.71 gnome-terminal     
5500 joshua    20   0 52748  19m  15m S  5.3  2.0   0:38.34 gnome-system-mo    
    916 root      20   0 50660  21m  10m R  5.0  2.1  19:38.97 Xorg               
 2004 joshua    20   0  235m  40m  21m S  1.3  4.1   2:23.30 empathy            
 1002 joshua    20   0  107m  12m 9000 S  0.7  1.2   0:28.17 metacity           
 5251 joshua    20   0  330m  95m  27m S  0.7  9.6   2:42.51 firefox-bin        
        1 root      20   0  2796 1548 1112 S  0.0  0.2   0:00.30 init               
        2 root      20   0     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
        3 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 migration/0        
        4 root      20   0     0    0    0 S  0.0  0.0   0:01.03 ksoftirqd/0        
        5 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
        6 root      20   0     0    0    0 S  0.0  0.0   0:00.10 events/0           
        7 root      20   0     0    0    0 S  0.0  0.0   0:00.00 cpuset             
        8 root      20   0     0    0    0 S  0.0  0.0   0:00.00 khelper            
        9 root      20   0     0    0    0 S  0.0  0.0   0:00.00 netns      

So, what is backend, why is it running in root, and why does it take up 70+%? And what is Xorg and Metacity?

Thanks!

---

### Post by firbolg on 2010-07-13
Have you recently used the System Testing app? There was a bug - keeps backend running. You can see that backend is the one causing you the issue.

There was a fix released - are you completely updated? 

You can kill the process in a terminal 

```
sudo kill -9 5288
```

[https://bugs.launchpad.net/ubuntu/+source/checkbox/+bug/556636](https://bugs.launchpad.net/ubuntu/+source/checkbox/+bug/556636)

---

### Post by yossell on 2010-07-13
metacity is the windows manager that gnome runs as default when no effects are enabled. When effects are enabled, it's compiz.

---

### Post by dragon574444 on 2010-07-13
Thanks guys, these forums are very active. That did the trick, and it is definitely the system testing that did it, I'm able to make it do that again. I'm pretty sure I have all my updates, the update manager...thing popped up when I first installed Ubuntu, I let it do what it needed.

---

### Post by Excedio on 2010-07-13
Check to be sure there is nothing else in there waiting to be updated. Once in a while it does not appear automatically.
 
System -> Administration -> Update Manager

---

