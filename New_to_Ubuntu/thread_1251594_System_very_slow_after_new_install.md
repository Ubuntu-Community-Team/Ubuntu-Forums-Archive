---
title: "System very slow after new install"
date: 2009-08-27
forum: New to Ubuntu
---

### Post by tim1970 on 2009-08-27
I just installed 9.04, and my laptop is running very slow.  I installed on a Dell, 1.66MHZ with 1GB of memory.  When I look at system monitor, it shows the CUP at between 90 and 100%.  I ran top for about 5 minutes and it seemed to only show about 20% of CPU being used, with xorg using most of that.  Every now and then xorg would pop up to around 60% but then immediately go back down. Then I killed top, and ran it again, and manage to catch this..

 4736 root      20   0  2064  508  436 R 56.0  0.0   0:00.29 hal-system-smbi    
 2491 root      20   0  148m  42m 7772 S 34.7  4.2   7:25.26 Xorg               
 3378 play      20   0  140m  55m  21m S  1.9  5.6   0:40.04 firefox            
    1 root      20   0  1908  780  564 S  0.0  0.1   0:01.44 init               
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 R  0.0  0.0   0:00.02 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    6 root      15  -5     0    0    0 S  0.0  0.0   0:00.01 events/0           
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khelper            
    8 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 kstop/0            
    9 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kintegrityd/0      
   10 root      15  -5     0    0    0 S  0.0  0.0   0:00.01 kblockd/0          
   11 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid             
   12 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify       
   13 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 cqueue             
   14 root      15  -5     0    0    0 S  0.0  0.0   0:00.11 ata/0     

Then when I ran it again it only shows xorg using 15%.  at the same time system monitor is showing 98%  I have also done a hard reset and it didn't change anything.

Any ideas?


Tim


:edit
When I have system monitor running beside a terminal window running the top command, then the top command shows xorg is using 90% or better of the CPU.

---

### Post by ptn107 on 2009-08-28
If your using desktop effects turn them off (System -> Preferences -> Appearance -> Visual Effects: None.

---

### Post by tim1970 on 2009-08-28
I switched visual effects to none.  While this did help some, it is still running slow.  While the computer is fast enough and has enough memory (1GB) I believe the built in video processor is just not up to par.  (When I go into my bios setup it only shows 32mb of video memory).  I think I am going to try Xubuntu.  Does this seem like my best alternative?

---

### Post by QIII on 2009-08-28
Do you have Vino (desktop sharing) enabled?

Sometimes Vino flogs the CPU and doesn't show in top.

---

### Post by st33med on 2009-08-28
What GPU do you have?

```
lspci | grep 'VGA'
```

---

