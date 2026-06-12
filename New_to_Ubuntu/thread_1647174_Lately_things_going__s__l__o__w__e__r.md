---
title: "Lately things going  s  l  o  w  e  r"
date: 2010-12-16
forum: New to Ubuntu
---

### Post by jbocean on 2010-12-16
I've been using my first full install of 10.04 for about 4 months now. W/in the past 2 wks or so, it seems my computer and the internet are moving much slower. I regularly use update manager and something called '2-Click Update'. But even w/ almost daily maintaince the slowness problem persists.

When I had Windows XP - there was a Norton's Utility thing I could use to 
a) check for any viruses or malware and eliminate them if I had any. 
b) defragment the hard drive 
c) clean things up behind the scenes to make the computer faster. 


What is there for Ubuntu which might do the same things?

Thanks

---

### Post by NightwishFan on 2010-12-16
"Things going slower" does not aid us helper robots on here much, can you be more specific or give us hard data?

Also, what you describe as maintenance is not needed for a Linux system. Updates give you a few bug fixes and security updates however they are not needed on a daily basis, even a weekly basis might be better to run updates. Disk defragging is not needed and cleaning old files is handled by the OS. Linux systems on servers typically run for years, and your machine running Ubuntu at home is not much different than the server OS.

---

### Post by Wim Sturkenboom on 2010-12-17
Open a terminal and run the command 'free'.
```

wim@desktop-01:~$ **free**
             total       used       free     shared    buffers     cached
Mem:       1023784     985664      38120          0      43924     473424
-/+ buffers/cache:     468316     555468
Swap:      4179960        436    4179524
wim@desktop-01:~$ 

```
Check if the system uses a lot of swap.

And run the command top to see what eats CPU and memory
```

top - 07:21:18 up 19:42,  2 users,  load average: 0.10, 0.14, 0.17
Tasks: 151 total,   1 running, 150 sleeping,   0 stopped,   0 zombie
Cpu(s):  1.7%us,  0.8%sy,  0.0%ni, 97.2%id,  0.2%wa,  0.1%hi,  0.0%si,  0.0%st
Mem:   1023784k total,   987072k used,    36712k free,    44132k buffers
Swap:  4179960k total,      436k used,  4179524k free,   473572k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 8406 root      20   0  242m  71m  19m S  3.9  7.2   0:42.67 Xorg               
 8648 wim       20   0  296m  51m  19m S  2.0  5.1   0:11.38 compiz             
 8902 wim       20   0  209m  15m  10m S  2.0  1.5   0:01.02 gnome-terminal     
    1 root      20   0 23700 1852 1268 S  0.0  0.2   0:00.61 init               
    2 root      20   0     0    0    0 S  0.0  0.0   0:00.01 kthreadd           
...
...

```
'top' runs in an endless loop; you can stop it by pressing 'q' (without the quotes).

Both programs can help in the analysis of this problem.

PS I'm not the one that can really help further might the output of the programs might help others to help you.

PPS you can use the command *top -d 10* to only refresh every 10 seconds and select and copy the results

---

### Post by jbocean on 2010-12-18
I read something about Flash Cookies, so I installed the Firefox Addon BetterPrivacy - deleted all flash cookies and my internet seems to be back up to speed.

---

### Post by Myglaren on 2010-12-18
I have been experiencing some atypical slowdowns.
Noticed on the Docky icon that the CPU was at 100% - most unusual.
"Top" indicates that apt-get is usin 99% CPU!
Kill won't work, action disallowed.

Only way out seems to be a reboot, not the end of the world but I would appreciate a more elegant fix.

---

