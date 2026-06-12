---
title: "100% CPU Usage"
date: 2009-08-05
forum: New to Ubuntu
---

### Post by mutesounds on 2009-08-05
I can't figure out what is taking it all up, but the computer is running excruciatingly slow.  I haven't installed anything prior to when it started.  I need help to find out what it is and stop it.  Thank you.

---

### Post by pedro3005 on 2009-08-05
What is the version of ubuntu installed and what are your PC specs? Maybe ubuntu is too heavy for you, then you could try xubuntu or another light distro.

---

### Post by mutesounds on 2009-08-05
I am running Ubuntu 9.04 32-bit.  I have an AMD Phenom triple core processor @ 2.2ghz, 4gb ram, 500gb HD, and ATI HD 3200 graphics.

---

### Post by credobyte on 2009-08-05
Open terminal, run this command and post the output ( copy/paste ):
```
top
```

---

### Post by mutesounds on 2009-08-05
```
brandon@brandon-ubuntu:~$ top

top - 12:38:31 up 22:39,  3 users,  load average: 1.56, 1.89, 1.95
Tasks: 154 total,   3 running, 151 sleeping,   0 stopped,   0 zombie
Cpu(s): 16.8%us, 23.2%sy,  0.0%ni, 59.7%id,  0.1%wa,  0.0%hi,  0.1%si,  0.0%st
Mem:   3355520k total,  3237876k used,   117644k free,    19836k buffers
Swap:  9823708k total,     4780k used,  9818928k free,  2724640k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 9219 root      20   0 30092  15m 1168 R  100  0.5 418:05.36 partimage          
22206 brandon   20   0  395m 148m  23m R    8  4.5   5:07.63 firefox            
23019 brandon   20   0 55816  15m   9m S    7  0.5   0:00.58 gnome-terminal     
21942 root      20   0  479m 150m  18m S    3  4.6   4:12.35 Xorg               
22126 brandon   20   0 69020  20m  11m S    3  0.6   0:20.79 gnome-panel        
22318 brandon   20   0 72784  19m 9912 S    3  0.6   0:50.54 transmission       
22202 brandon   20   0 16680 2932 1548 S    1  0.1   0:08.33 gnome-screensav    
    1 root      20   0  3084  528  476 S    0  0.0   0:01.29 init               
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S    0  0.0   0:01.38 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
   12 root      15  -5     0    0    0 S    0  0.0   0:00.13 events/0           
   15 root      15  -5     0    0    0 S    0  0.0   0:00.00 khelper            
   16 root      RT  -5     0    0    0 S    0  0.0   0:00.00 kstop/0            
   19 root      15  -5     0    0    0 S    0  0.0   0:00.00 kintegrityd/0      
   22 root      15  -5     0    0    0 S    0  0.0   0:00.01 kblockd/0          


```

---

### Post by ubudog on 2009-08-05
> **mutesounds said:**
> ```
brandon@brandon-ubuntu:~$ top

top - 12:38:31 up 22:39,  3 users,  load average: 1.56, 1.89, 1.95
Tasks: 154 total,   3 running, 151 sleeping,   0 stopped,   0 zombie
Cpu(s): 16.8%us, 23.2%sy,  0.0%ni, 59.7%id,  0.1%wa,  0.0%hi,  0.1%si,  0.0%st
Mem:   3355520k total,  3237876k used,   117644k free,    19836k buffers
Swap:  9823708k total,     4780k used,  9818928k free,  2724640k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 9219 root      20   0 30092  15m 1168 R  100  0.5 418:05.36 partimage          
22206 brandon   20   0  395m 148m  23m R    8  4.5   5:07.63 firefox            
23019 brandon   20   0 55816  15m   9m S    7  0.5   0:00.58 gnome-terminal     
21942 root      20   0  479m 150m  18m S    3  4.6   4:12.35 Xorg               
22126 brandon   20   0 69020  20m  11m S    3  0.6   0:20.79 gnome-panel        
22318 brandon   20   0 72784  19m 9912 S    3  0.6   0:50.54 transmission       
22202 brandon   20   0 16680 2932 1548 S    1  0.1   0:08.33 gnome-screensav    
    1 root      20   0  3084  528  476 S    0  0.0   0:01.29 init               
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S    0  0.0   0:01.38 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
   12 root      15  -5     0    0    0 S    0  0.0   0:00.13 events/0           
   15 root      15  -5     0    0    0 S    0  0.0   0:00.00 khelper            
   16 root      RT  -5     0    0    0 S    0  0.0   0:00.00 kstop/0            
   19 root      15  -5     0    0    0 S    0  0.0   0:00.00 kintegrityd/0      
   22 root      15  -5     0    0    0 S    0  0.0   0:00.01 kblockd/0          


```

It looks like the program "partimage" is using all that cpu.  Do you know what that program is?

---

### Post by credobyte on 2009-08-05
Try killing partimage ( CAREFULLY!! ):
```
sudo kill 9219

```

** Partimage is used to make some kind of backup copy of your HDD.

---

### Post by mutesounds on 2009-08-05
> **credobyte said:**
> Try killing partimage ( CAREFULLY!! ):
```
sudo kill 9219

```

** Partimage is used to make some kind of backup copy of your HDD.

That killed it, my fan quieted down.  Is this something I can safely remove or disable?  I don't remember downloading anything like this.

---

### Post by credobyte on 2009-08-05
> **mutesounds said:**
> That killed it, my fan quieted down.  Is this something I can safely remove or disable?  I don't remember downloading anything like this.

Yes, it's just an utility which *usually* shouldn't be running ( not a vital system process ).

---

### Post by mutesounds on 2009-08-05
> **credobyte said:**
> Yes, it's just an utility which *usually* shouldn't be running ( not a vital system process ).

Thank you.  I tried to uninstall but it says it is not on the system.

```
Package partimage is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

But when I search for it, that is the name.

```
p   partimage                       - backup partitions into a compressed image 

```

I just restarted and the process is not running, so all is well I suppose.  I really appreciate the help!!  Is there anywhere I can donate to help out the community?

---

### Post by ubudog on 2009-08-05
> **mutesounds said:**
> Thank you.  I tried to uninstall but it says it is not on the system.

```
Package partimage is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

But when I search for it, that is the name.

```
p   partimage                       - backup partitions into a compressed image 

```

I just restarted and the process is not running, so all is well I suppose.  I really appreciate the help!!  Is there anywhere I can donate to help out the community?

Anytime!  You can donate here:[http://www.ubuntu.com/community/donations](http://www.ubuntu.com/community/donations) :)

---

### Post by nhasian on 2009-08-16
you could also donate your time by helping other users resolve their problems here in the message forum if you are familiar with their problem :)

> **mutesounds said:**
> Is there anywhere I can donate to help out the community?

---

### Post by ubudog on 2009-08-16
> **nhasian said:**
> you could also donate your time by helping other users resolve their problems here in the message forum if you are familiar with their problem :)

Yes.  That is what I do. :guitar:

---

