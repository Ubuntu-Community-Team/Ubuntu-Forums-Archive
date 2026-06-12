---
title: "Slow running"
date: 2009-07-15
forum: New to Ubuntu
---

### Post by to25 on 2009-07-15
First off I am a complete noob That is learning quiet a bit. Secondly I have noticed that my ubuntu is running quiet slower than before. I don't know what to look for, because Windows always had malware, but I wouldn't put it pas my family of downloaders. So i figured I would try out AVG. But if this doesn't work and you guy have any other remidies please let e know thanks.

---

### Post by renkinjutsu on 2009-07-15
need to know what's making it slow.. listen to your computer, can you hear the harddrive constantly reading and writing? .. should sound sort of like static..

also can your hear your fanspeeds changing? what's your cpu usage? post the output of `top` in the terminal

---

### Post by to25 on 2009-07-15
Yeah, That happens quiet often but not all the time and it still is sluggish.

---

### Post by metiosarius on 2009-07-15
> also can your hear your fanspeeds changing? what's your cpu usage? post the output of `top` in the terminal

Can you try his suggestion? 

Applications>Accessories>Terminal

At the prompt, type "top" (w/o quotes) and press enter/return.

Copy and paste the output here.

---

### Post by to25 on 2009-07-15
For some reason I can't copy it. I tried to highlight it but it just r turns to normal. I does have things that look suspect even to me. Well just mainly this " 2 users" is that normal.

---

### Post by wojox on 2009-07-15
Yes you and root are the two users.

Try:

```
top > top.txt
```

This will send it to a file for you.

---

### Post by lovinglinux on 2009-07-15
Anti-virus is useless.

Go to "System >> Administration >> Hardware Drivers" and make sure you have the proper driver installed. 

Also go to "System >> Preferences >> Startup Applications" and disable the "Remote Desktop, then reboot. This should improve things considerably.

If you have Intel Graphics card visit [http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)

Also check [Tips: Things that might improve Jaunty performance](http://ubuntuforums.org/showthread.php?t=1152095)

---

### Post by CompizDoDo on 2009-07-15
like he said go to terminal and type top just type in what the highest amount of cpu usage a program is using and the program and we can help;)

---

### Post by to25 on 2009-07-19
Sorry for the delayed post, I haven't been around to test things out. Well I tried "> top > top.txt" but nothing came up. Was a screen supposed to pop up or it sent the file elsewhere? As for what I can tell you, the %id stays around 89 to 95 %. the %us jumps around between 4 and 18 %. main usage is by Xorg using 12 %cpu and firefox with 1 to 5 % and metacity, gnome-panel, gnome-settings and python with about 1 to 4 percent. Hope you guys still can help.

 Before all else I would like to clarify my issue just in case it is some weird phase or it pertains to a different issue affecting my desktop. My computer is not running super slow but noticably slower. When moving the windows, especially when minimizing them you can see their movements simular to that of an infected pc running windows(hence the virus question). I'm not  sure whats that called but it leaves like a snake trale of the window being draged, but fades faster. Just incase this another issue.

---

### Post by bboston7 on 2009-07-19
Just do this

1. Open terminal
2. Type top
3. Wait a few seconds
4. Hit ctrl + c
5. Highlight the grid
6. Copy and paste it into a post

Then we can help you more...

---

### Post by to25 on 2009-07-20
top - 01:28:09 up  5:51,  2 users,  load average: 0.41, 0.22, 0.08
Tasks: 132 total,   2 running, 130 sleeping,   0 stopped,   0 zombie
Cpu(s): 32.5%us,  1.5%sy,  0.0%ni, 66.1%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   1931420k total,   546704k used,  1384716k free,    50392k buffers
Swap:  4104568k total,        0k used,  4104568k free,   292628k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 2630 root      20   0  172m  34m 8520 R   56  1.8  10:38.11 Xorg               
12308 family    20   0  174m  52m  22m S    4  2.8   0:08.37 firefox            
 3267 family    20   0 22396  12m 8736 S    4  0.7   0:14.26 metacity           
 3325 family    20   0 37728  20m  13m S    3  1.1   0:18.99 gnome-panel        
 3248 family    20   0 31536  11m 7720 S    1  0.6   0:04.36 gnome-settings-    
 3326 family    20   0 61192  24m  14m S    0  1.3   0:13.14 nautilus           
 3407 family    20   0 16644 5208 3964 S    0  0.3   0:07.91 gnome-screensav    
    1 root      20   0  3084 1888  564 S    0  0.1   0:01.23 init               
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.02 migration/0        
    4 root      15  -5     0    0    0 S    0  0.0   0:01.18 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.03 migration/1        
    7 root      15  -5     0    0    0 S    0  0.0   0:00.64 ksoftirqd/1        
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      15  -5     0    0    0 S    0  0.0   0:00.07 events/0           
   10 root      15  -5     0    0    0 S    0  0.0   0:00.00 events/1 

so what do you guys think?

---

