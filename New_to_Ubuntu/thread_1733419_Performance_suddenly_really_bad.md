---
title: "Performance suddenly really bad"
date: 2011-04-19
forum: New to Ubuntu
---

### Post by bthomson100 on 2011-04-19
My EEE PC 1005 running ubuntu 10.10 has suddenly slowed to a crawl. I suspect it might have something to do with cache space, but I'm a real newbie with Linux and haven't been able to find anything in the Forums here that would help me. I typed "top" in a terminal and it showed only 32% of the 1gb RAM/CPU being used by 15 applications. It really grinds to a halt when printing. This is new as I had no such problems up until about a week ago.

Can anyone suggest where I can look to resolve this? Is there a way to create or enlarge a hard drive cache space that might help?

Bob Thomson
Ottawa, Canada

---

### Post by mikewhatever on 2011-04-19
Can you post the outputs of the following commands:

```
free -m
df -h
top
sudo fdisk -l
```

Is there any pattern to the slowdowns, or do they only happen when printing?

---

### Post by bthomson100 on 2011-04-20
Here are the results from those commands
free -m
df -h
top
sudo fdisk -l

They mean nothing to me I'm afraid since I'm a complete Linux newbie.

Bob

bob@bob-1005HA:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           993        957         35          0        132        380
-/+ buffers/cache:        445        548
Swap:         2997          5       2992

bob@bob-1005HA:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5              89G   25G   60G  30% /
none                  492M  284K  491M   1% /dev
none                  497M   12K  497M   1% /dev/shm
none                  497M  392K  497M   1% /var/run
none                  497M     0  497M   0% /var/lock
/dev/sdb1             233G  229G  4.4G  99% /media/FreeAgent Drive__

bob@bob-1005HA:~$ top

***[Note: When I run "top", it goes into a continuous process which I can't stop. The display keeps changing, I suppose because the programmes running are changing in their use of memory etc. all the time.]***

top - 07:51:30 up 45 min,  2 users,  load average: 0.01, 0.63, 0.70
Tasks: 157 total,   1 running, 155 sleeping,   0 stopped,   1 zombie
Cpu(s):  5.3%us,  2.6%sy,  0.0%ni, 91.9%id,  0.0%wa,  0.0%hi,  0.3%si,  0.0%st
Mem:   1017216k total,   946440k used,    70776k free,   135776k buffers
Swap:  3069948k total,     5208k used,  3064740k free,   372108k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 1877 bob       20   0  181m  41m  11m S    6  4.1   3:04.03 plugin-containe    
 1811 bob       20   0  315m  88m  26m S    2  8.9   3:22.79 firefox-bin        
  850 messageb  20   0  3716 2116 1004 S    1  0.2   0:05.30 dbus-daemon        
 1020 root      20   0 20632 5032 4328 S    1  0.5   0:03.55 NetworkManager     
 1571 bob       20   0 84648  12m   9m S    1  1.3   0:03.80 metacity           
 1127 root      20   0 41572  18m 9484 S    1  1.9   2:20.46 Xorg               
 1821 bob       20   0 78144  21m 9696 S    1  2.2   0:29.40 jpilot             
 3559 bob       20   0  2620 1136  840 R    1  0.1   0:01.60 top                
  744 root      20   0     0    0    0 S    1  0.0   0:01.47 phy0               
 1025 root      20   0  4900 1884 1784 S    1  0.2   0:01.02 wpa_supplicant     
 3525 bob       20   0 95032  13m  10m S    1  1.4   0:03.37 gnome-terminal     
    3 root      20   0     0    0    0 S    0  0.0   0:00.17 ksoftirqd/0        
   51 root      20   0     0    0    0 S    0  0.0   0:05.43 kondemand/0        
   52 root      20   0     0    0    0 S    0  0.0   0:04.87 kondemand/1        
  708 root      20   0     0    0    0 S    0  0.0   0:00.11 hd-audio0          

Help for Interactive Commands - procps version 3.2.8
Window 1:Def: Cumulative mode Off.  System: Delay 3.0 secs; Secure mode Off.
top - 07:52:27 up 46 min,  2 users,  load average: 0.01, 0.52, 0.66
Tasks: 157 total,   2 running, 154 sleeping,   0 stopped,   1 zombie
Cpu(s): 10.2%us,  2.5%sy,  0.0%ni, 86.2%id,  1.1%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   1017216k total,   947092k used,    70124k free,   135856k buffers
Swap:  3069948k total,     5208k used,  3064740k free,   372556k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 3525 bob       20   0 95164  14m  10m S    8  1.4   0:05.81 gnome-terminal     
 1877 bob       20   0  181m  41m  11m S    6  4.1   3:07.31 plugin-containe    
 1127 root      20   0 41852  18m 9488 S    3  1.9   2:22.80 Xorg               
 1811 bob       20   0  299m  88m  26m S    1  8.9   3:24.71 firefox-bin        
 1821 bob       20   0 78144  21m 9696 R    1  2.2   0:29.96 jpilot             
 3559 bob       20   0  2620 1136  840 R    1  0.1   0:05.45 top                
 1557 bob       20   0  141m  12m 9652 S    1  1.3   0:06.65 gnome-settings-    
   51 root      20   0     0    0    0 S    0  0.0   0:05.55 kondemand/0        
  950 root      20   0 20704 2868 2600 S    0  0.3   0:00.54 gdm-binary         
 1574 bob       20   0 84752  18m  10m S    0  1.9   0:05.52 gnome-panel        
 1575 bob       20   0  132m  19m  14m S    0  2.0   0:08.27 nautilus           
 1759 bob       20   0  370m  81m  23m S    0  8.2   4:37.87 thunderbird-bin    
 1793 bob       20   0 35076  18m 3928 S    0  1.9   0:15.30 ubuntuone-syncd    
    1 root      20   0  2880 1676 1200 S    0  0.2   0:01.01 init               
    2 root      20   0     0    0    0 S    0  0.0   0:00.00 kthreadd           

bob@bob-1005HA:~$ sudo fdisk -l
[sudo] password for bob: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x17351429

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5990    48113462+   7  HPFS/NTFS
/dev/sda2            5991       18150    97672193    5  Extended
/dev/sda3           18150       19456    10485760   1b  Hidden W95 FAT32
/dev/sda4           19456       19457       15712+  1b  Hidden W95 FAT32
/dev/sda5            5991       17768    94601216   83  Linux
/dev/sda6           17768       18150     3069952   82  Linux swap / Solaris

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa4b57300

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001    7  HPFS/NTFS
bob@bob-1005HA:~$

---

### Post by Locke_99GS on 2011-04-20
> **bthomson100 said:**
> ```

bob@bob-1005HA:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           993        957         35          0        132        380
-/+ buffers/cache:        445        548
Swap:         2997          5       2992

bob@bob-1005HA:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5              89G   25G   60G  30% /
none                  492M  284K  491M   1% /dev
none                  497M   12K  497M   1% /dev/shm
none                  497M  392K  497M   1% /var/run
none                  497M     0  497M   0% /var/lock
/dev/sdb1             233G  229G  4.4G  99% /media/FreeAgent Drive__

```

You're consuming a lot of your RAM. I'd imagine in certain situation you are swapping out, which is a slow process. Get more RAM, or use less RAM (run fewer apps concurrently)

Also, your external harddrive is full. Writing to it will be slower than normal.

> 
[Note: When I run "top", it goes into a continuous process which I can't stop. The display keeps changing, I suppose because the programmes running are changing in their use of memory etc. all the time.

The program "top", like many other terminal programs (such as "less" and "man") are exited with the 'q' key. 'Q' for Quit.

I'm assuming you have a very modest CPU, according to the usage info given by top. While, in those output at least, you don't seem to be maxxing out your CPU time, you may want to consider using lighter applications, such as Midori webbrowser instead of firefox, and Abiword instead of OpenOffice, and that sort. There are versions of Ubuntu specifically designed to use less resources, which of course is of most benefit to people with dated hardware. Consider switching to Lubuntu, which uses the LXDE interface and a much lighter application stack out-of-box.

If you're able to (capable) you may want to look into running the 2.6.38+ kernel if you're not already, which amongst other improvements, adds autogroups. This is a method for CFS which helps a bit in determining which process group to devote CPU time to. It helps keep your environment responsive under heavier loads.




I am not an expert - these are my opinions and suggestions.

---

### Post by bthomson100 on 2011-04-20
Many thanks [Locke_99GS]("http://ubuntuforums.org/member.php?u=543645"). 

*You're consuming a lot of your RAM. I'd imagine in certain situation you  are swapping out, which is a slow process. Get more RAM, or use less  RAM (run fewer apps concurrently)*

I'll look into that. It doesn't look like the RAM slot has an extra space so I'd likely have to buy a larger chip vs just adding a cheaper extra one. 

Where does it swap to? Aside from the slower speed of swapping, I imagine the size of the cache would matter as well.

*Also, your external hard drive is full. Writing to it will be slower than normal.*

I don't write to the external drive that much but I guess if I were editing something form it that would make a difference. I'll try to document what's going on next time it slows to a crawl.

I'll look into the alternative programmes that use less resources as well.

Many thanks for the tips. Maybe I'll be less of a newbie sooner than later.

Bob

---

### Post by mikewhatever on 2011-04-20
I see nothing wrong in the outputs. Contrary to what Locke_99GS says, RAM is not heavily used, in fact, more then half of the RAM is free. There is also not a lot of swapping (only 5MB). 

445MB - used RAM
548MB - free RAM
5MB   - swaped

```

ob@bob-1005HA:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           993        957         35          0        132        380
-/+ buffers/cache:        445        548
Swap:         2997          5       2992

```

Is there any pattern to slowdowns?

---

### Post by Locke_99GS on 2011-04-20
I didn't say he was swapping out *right now* - I'm fully able to interpret the output of 'free'. What I alluded to was that in certain situations he would be. Considering he has 5meg swapped at all **infers** that he has at some point consumed all of his RAM, or at least reached the point where mm decided to swap out.

---

