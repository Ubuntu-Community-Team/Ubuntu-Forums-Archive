---
title: "Laptop Running really hard... Help"
date: 2010-09-23
forum: New to Ubuntu
---

### Post by sammyjo on 2010-09-23
Ok guys so I just set up ubuntu yesterday on my laptop and the hard drive seems to be running really hard now, I can hear the high pitch whirring and it gets really hot like it is overloading and this is at rest, this is on all three of my laptops. I have two Hps and one Acer netbook. Is there anything that I can do to get this to calm down and quit running so hard?

---

### Post by bradleypariah on 2010-09-23
Not sure this is the solution, but try this:

Pull your battery out.  While the battery is out, hold down your power button for at least five seconds.
Put the battery back in.
Start it up.

Lemme know if that works.   :-)

---

### Post by sammyjo on 2010-09-23
Yeah I did that and it didnt seem to do anything any other ideas?

---

### Post by Jesus_Valdez on 2010-09-23
Check the "system monitor" (Administration -> System) to see if there's something out of the ordinary.

Also, what the model and or specifications of your laptop?

---

### Post by sammyjo on 2010-09-23
Well this one is a Hp Pavillian Entertainment PC and the spu usage is anywhere from 15 to 30 percent when at rest and that seems high to me. But its making the noise like its running like crazy now would it have anything to do with the wubi install that I did?

---

### Post by NightwishFan on 2010-09-23
I bet the 30% usage is just the System Monitor itself. It is a bit odd that way. Still to be sure open a terminal and run:
```
top
```

Push q to exit and post here surrounded by CODE (# symbol in the post message toolbar) tags.

---

### Post by sammyjo on 2010-09-23
```
top - 21:10:02 up 33 min,  2 users,  load average: 0.58, 0.55, 0.70
Tasks: 158 total,   1 running, 157 sleeping,   0 stopped,   0 zombie
Cpu(s):  3.3%us,  1.0%sy,  0.0%ni, 95.4%id,  0.2%wa,  0.0%hi,  0.2%si,  0.0%st
Mem:   3798384k total,  2782388k used,  1015996k free,   794940k buffers
Swap:   261112k total,        0k used,   261112k free,   985276k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 1121 root      20   0  228m  78m  32m S    4  2.1   7:11.22 Xorg               
 1578 sethring  20   0  465m  48m  24m S    1  1.3   1:02.10 chrome             
 1917 sethring  20   0  847m  46m  15m S    1  1.3   0:27.88 chrome             
 2009 sethring  20   0  197m  14m  10m S    1  0.4   0:00.82 gnome-terminal     
 1419 sethring  20   0  246m  34m 7708 S    1  0.9   0:34.84 compiz             
 8402 sethring  20   0 19220 1408 1028 R    1  0.0   0:00.05 top                
 1476 sethring  20   0  327m  15m  11m S    0  0.4   0:00.38 indicator-apple    
    1 root      20   0 23700 1920 1248 S    0  0.1   0:00.52 init               
    2 root      20   0     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      20   0     0    0    0 S    0  0.0   0:02.07 ksoftirqd/0        
    5 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/1        
    7 root      20   0     0    0    0 S    0  0.0   0:00.30 ksoftirqd/1        
    8 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      20   0     0    0    0 S    0  0.0   0:00.04 events/0           
   10 root      20   0     0    0    0 S    0  0.0   0:00.02 events/1           
   11 root      20   0     0    0    0 S    0  0.0   0:00.00 cpuset           
```

---

### Post by sammyjo on 2010-09-23
Now quick question do you think it has anything to do with the wubi installer?

---

### Post by Jesus_Valdez on 2010-09-23
What's your Video card? Do you have the proper driver installed?

I don't think that wubi is related to thie.

---

### Post by sandyd on 2010-09-23
doesn't look like a xorg leak either...
maybe overheat?
run
```

sensors
```

---

### Post by NightwishFan on 2010-09-24
Quite, it is not the cpu.  I assumed it was not, especially if the disk is loud. I do not see why it would be wubi, so you are probably safe there.

---

### Post by sammyjo on 2010-09-25
Actually guys I do believe that it was the Wubi installer. I partitioned my drive last night and reinstalled from a usb stick and the problem has thus been fixed. Thank you all for looking into this one for me!

---

