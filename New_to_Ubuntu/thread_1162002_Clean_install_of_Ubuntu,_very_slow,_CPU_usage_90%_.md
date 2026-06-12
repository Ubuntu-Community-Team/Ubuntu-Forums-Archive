---
title: "Clean install of Ubuntu, very slow, CPU usage 90% - 100%"
date: 2009-05-17
forum: New to Ubuntu
---

### Post by watchmen77 on 2009-05-17
Hello:

I am new to ubuntu.
Just installed a clean copy of Ubuntu 9.04 on a dell D600 laptop.
After using for few hours, everything seem very slow.
I checked system monitor and seems CPU usage is always at 90-100%

you can view the attachment for a sample. (sorry the screen is in Chinese, you can still see CPU usage is at 90-100%. Any idea on how to fix this?
d600 is with a 1.8mhz cpu and 1gb ram plus raden9000 graphic card.

---

### Post by Didius Falco on 2009-05-17
Hi, welcome to the Ubuntu forums!

System Monitor grabs quite a bit of memory by itself. Open a Terminal shell from **Applications/Accessories/Terminal** and type ```
top
```

That will tell you what is using the most memory. Post the top 4-5 memory hogs and we can try to figure out the cause of the problem and solve it.

It'd be good if you could post your systems specs, too.

Regards,

Didius

---

### Post by watchmen77 on 2009-05-17
thank you for helping here.

PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 2846 root      20   0  159m  51m 9320 R 22.1  5.1  42:25.74 Xorg               
 5440 weij      20   0 61568  24m  15m S  3.6  2.4   0:22.77 sysinfo            
 3808 weij      20   0  203m  82m  27m S  2.0  8.2   0:47.89 firefox            
 6502 weij      20   0 44652  14m  10m S  1.3  1.5   0:00.56 gnome-terminal     
 2628 haldaemo  20   0  6656 4564 3784 S  0.7  0.4   0:01.12 hald               
 6532 weij      20   0  2448 1188  912 R  0.7  0.1   0:00.19 top                
 2505 messageb  20   0  3028 1396  840 S  0.3  0.1   0:00.84 dbus-daemon        
 3607 weij      20   0 52384  23m  13m S  0.3  2.3   0:01.63 python             
 3679 weij      20   0 17096 2984 1764 S  0.3  0.3   0:01.64 gnome-screensav    
    1 root      20   0  3216 2024  564 S  0.0  0.2   0:01.35 init         

please view above.

My system spec:
CPu: Intel 1.8 MHZ
Memory: 1gb
Graphic; ATI Radeon RV250 (Mobility FireGL 9000)
System:
Gnome:  2.26.1
Kernel:   2.6.28-11-generic

GCC version: 4.3.3
Xorg Version: Unknown


As I did some research online, seems may related to Xorg, graphic driver may not be correct but I am not sure how fix this. I tried get ATI driver from auto download/install but it crashes the whole system, I had to start in command mode and delete the whole ATI driver.

---

### Post by watchmen77 on 2009-05-17
More top:

weij@weij-laptop:~$ top
top - 22:05:31 up  1:05,  2 users,  load average: 0.29, 0.50, 0.74
Tasks: 130 total,   1 running, 128 sleeping,   0 stopped,   1 zombie
Cpu(s): 48.7%us,  3.0%sy,  0.0%ni, 48.0%id,  0.0%wa,  0.3%hi,  0.0%si,  0.0%st
Mem:   1026412k total,   667108k used,   359304k free,    30112k buffers
Swap:  2417708k total,        0k used,  2417708k free,   293648k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 2846 root      20   0  161m  52m 9452 S 42.7  5.2  46:33.97 Xorg               
 5440 weij      20   0 61568  24m  15m S  3.0  2.4   0:40.85 sysinfo            
 3808 weij      20   0  203m  81m  27m S  2.3  8.1   1:16.14 firefox            
 6502 weij      20   0 45120  15m  10m S  2.0  1.5   0:01.42 gnome-terminal     
 3376 weij      20   0 27620  18m 6760 S  1.0  1.9   0:12.79 compiz.real        
 3272 weij      20   0 40748 8012 5540 S  0.3  0.8   0:01.51 scim-panel-gtk     
 3605 weij      20   0 52704  23m  13m S  0.3  2.4   0:01.18 python             
 3607 weij      20   0 52384  23m  13m S  0.3  2.3   0:03.04 python             
 7025 weij      20   0  2448 1184  912 R  0.3  0.1   0:00.26 top                
    1 root      20   0  3216 2024  564 S  0.0  0.2   0:01.35 init               
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.03 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0

---

### Post by SunnyRabbiera on 2009-05-17
Jaunty has this kind of issue it seems, maybe an older version of Ubuntu will work.
Ubuntu Hardy is still quite viable, it still gets security updates but doesnt get latest software...
But meh if it works it works

---

### Post by Didius Falco on 2009-05-17
Please close System Monitor and let's have a look at another "top" output. I don't use System Monitor to check cpu or memory usage because it's such a memory/cpu hog itself that you get a distorted picture. 

I'm wondering if you still have some remnants of the ATI driver hanging around.  Let me look through my notes and I'll put together instructions on how to make sure all traces of it are gone.


Regards

Didius

---

