---
title: "Does ubuntu sometimes just &quot;think&quot;"
date: 2009-05-25
forum: New to Ubuntu
---

### Post by servicetech on 2009-05-25
My taskbar monitor is showing 55% CPU use with nothing running, system monitor shows about 10% use. HDD light is blinking so I'm thinking something is running that's not showing in system monitor. Does ubuntu cause computers just to "think" like windows machines?

---

### Post by Celauran on 2009-05-25
55% CPU usage? *Something* is running. Have you looked at top?

---

### Post by kpkeerthi on 2009-05-25
Open a terminal and enter **top**. Press 'q' to quit and post the output here.

---

### Post by Mornedhel on 2009-05-25
Unlike what you may see in movies, current AIs are so far from thinking, it's not even funny. (Yes, I know that's probably not what you meant.)

Maybe you have visual effects enabled, or you have an indexer tracking some files, or it's updating its package list, or pulling weather info for the weather applet, or synchronising on an NTP server, or a cron job started doing its thing, or, or...

Just like Windows, at any time there are many services running.

If you want to see what's consuming cycles, open a terminal and type top. Press Q to quit.

---

### Post by servicetech on 2009-05-25
bob@bob-desktop:~$ top

top - 12:01:01 up  2:46,  2 users,  load average: 4.29, 5.47, 3.26
Tasks: 143 total,   1 running, 142 sleeping,   0 stopped,   0 zombie
Cpu(s):  1.6%us,  4.3%sy,  0.0%ni, 63.1%id, 30.7%wa,  0.2%hi,  0.2%si,  0.0%st
Mem:   1801884k total,   767892k used,  1033992k free,   157324k buffers
Swap:  5277312k total,        0k used,  5277312k free,   341764k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 2819 root      20   0  638m  35m  12m S    8  2.0   1:36.34 Xorg               
  733 root      15  -5     0    0    0 D    1  0.0   1:29.05 kjournald          
 2756 mythtv    20   0 70884 7992 5180 D    1  0.4   0:27.73 mythbackend        
   42 root      15  -5     0    0    0 S    0  0.0   0:02.08 scsi_eh_4          
 3563 bob       20   0 27348  18m 6728 S    0  1.0   0:13.85 compiz.real        
 3564 bob       20   0 36888  19m  13m S    0  1.1   0:04.65 gnome-panel        
 3619 bob       20   0 24024  10m 8620 S    0  0.6   0:19.39 multiload-apple    
 5618 bob       20   0  2448 1196  912 R    0  0.1   0:00.42 top                
    1 root      20   0  3084 1884  564 S    0  0.1   0:01.09 init               
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S    0  0.0   0:00.10 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    9 root      15  -5     0    0    0 S    0  0.0   0:00.00 events/0           
   11 root      15  -5     0    0    0 S    0  0.0   0:00.00 khelper            
   12 root      RT  -5     0    0    0 S    0  0.0   0:00.00 kstop/0            
   14 root      15  -5     0    0    0 S    0  0.0   0:00.00 kintegrityd/0

---

### Post by cerealtx on 2009-05-25
> **servicetech said:**
> bob@bob-desktop:~$ top

top - 12:01:01 up  2:46,  2 users,  load average: 4.29, 5.47, 3.26
Tasks: 143 total,   1 running, 142 sleeping,   0 stopped,   0 zombie
Cpu(s):  1.6%us,  4.3%sy,  0.0%ni, 63.1%id, 30.7%wa,  0.2%hi,  0.2%si,  0.0%st
Mem:   1801884k total,   767892k used,  1033992k free,   157324k buffers
Swap:  5277312k total,        0k used,  5277312k free,   341764k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 2819 root      20   0  638m  35m  12m S    8  2.0   1:36.34 Xorg               
  733 root      15  -5     0    0    0 D    1  0.0   1:29.05 kjournald          
 2756 mythtv    20   0 70884 7992 5180 D    1  0.4   0:27.73 mythbackend        
   42 root      15  -5     0    0    0 S    0  0.0   0:02.08 scsi_eh_4          
 3563 bob       20   0 27348  18m 6728 S    0  1.0   0:13.85 compiz.real        
 3564 bob       20   0 36888  19m  13m S    0  1.1   0:04.65 gnome-panel        
 3619 bob       20   0 24024  10m 8620 S    0  0.6   0:19.39 multiload-apple    
 5618 bob       20   0  2448 1196  912 R    0  0.1   0:00.42 top                
    1 root      20   0  3084 1884  564 S    0  0.1   0:01.09 init               
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S    0  0.0   0:00.10 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    9 root      15  -5     0    0    0 S    0  0.0   0:00.00 events/0           
   11 root      15  -5     0    0    0 S    0  0.0   0:00.00 khelper            
   12 root      RT  -5     0    0    0 S    0  0.0   0:00.00 kstop/0            
   14 root      15  -5     0    0    0 S    0  0.0   0:00.00 kintegrityd/0

you have a mythbox dameon running, are u recording any shows???

---

### Post by servicetech on 2009-05-25
Myth was actually the issue. I tried installing it but could never get it to work. Uninstalling the 80+ individual packages corrected the problem. Hopefully I got everything.

---

### Post by lwvmobile on 2009-05-25
LOL, yes I have always wondered the same. But not just with Ubuntu, but 
Windows too. When it just sits idle for a while and then the HDD just starts up or the CPU usage starts up. Usually its easy to figure out what it is in Vista, except for when you turn off the AV, Windows Updates and Search Index then I have no clue. Same for Ubuntu, sometimes it just wants to 'think' I guess.:D:D:D

---

### Post by kpkeerthi on 2009-05-26
You CPU usage is only 1.6%. Looks normal to me. And... use [CODE] tags for posting command outputs so they are readable.

---

### Post by asmoore82 on 2009-05-26
... and there are lots of housekeeping tasks that run on a set schedule -
you can get a glimpse of them at "/etc/cron*"

---

### Post by Sarai the Geek on 2009-05-26
> **lwvmobile said:**
> LOL, yes I have always wondered the same. But not just with Ubuntu, but Windows too

I wonder that about people sometimes too...

---

