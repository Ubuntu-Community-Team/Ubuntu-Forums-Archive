---
title: "Screen Blanks"
date: 2010-10-24
forum: New to Ubuntu
---

### Post by tb75252 on 2010-10-24
Absolute Linux beginner here...

Using Ubuntu 10.10 (32-bit).
Every x minutes my screen blanks out for about five-ten seconds.  This happens when I am using the computer, so I do not think that it is the screen saver.  I had the same problem with Ubuntu 10.04 LTS.
My BIOS has no "green" settings (computer is ten years old!).
Is this a bug or a setting in Ubuntu?  I've looked everywhere...

---

### Post by amjjawad on 2010-10-24
> **tb75252 said:**
> Absolute Linux beginner here...

Using Ubuntu 10.10 (32-bit).
Every x minutes my screen blanks out for about five-ten seconds.  This happens when I am using the computer, so I do not think that it is the screen saver.  I had the same problem with Ubuntu 10.04 LTS.
My BIOS has no "green" settings (computer is ten years old!).
Is this a bug or a setting in Ubuntu?  I've looked everywhere...

Perhaps you need to provide us with more details :)
When exactly this is happening? are you doing something specifically? are you listening to Music? watch a Movie? typing? chatting? browsing?

I can't tell what exactly the problem is but most likely it's either your screen or something wrong could be with the driver. We need more details so that we could find a solution together :)

---

### Post by tb75252 on 2010-10-24
> **amjjawad said:**
> Perhaps you need to provide us with more details :)
When exactly this is happening? are you doing something specifically? are you listening to Music? watch a Movie? typing? chatting? browsing?

I can't tell what exactly the problem is but most likely it's either your screen or something wrong could be with the driver. We need more details so that we could find a solution together :)

This behavior appears to be happening no matter what I do.  Yesterday evening I was browsing the Internet and it happened intermittently.  But it also happens intermittently when I am using OpenOffice or Thunderbird.  It does not do it immediately after I start Ubuntu.  It happens after about 15 minutes or so of usage.  (I have not really timed it.)

So, after an x amount of minutes, the screen freeze and dims to a light gray color, Underneath I can still see text and images of the application that I am using at the moment but for  a five- and sometimes ten-second moment I cannot do anything although I can move the mouse on the screen.  The mouse moves but the icons etc are not responsive; also, typing does not output anything to the screen.

My video card is **EVGA NVIDIA GeForce 6200**.  Going into System -> Administration I can see that there is a driver installed called **NVIDIA X-Server Settings**.  I do not know if this driver is the correct one for my card and how to tweak that driver.  It installed itself when I loaded Ubuntu, I guess.

My display is **HannStar HNC iX191**.

I should also add that when I was using Microsoft Windows XP SP3 none of this was happening.

---

### Post by amjjawad on 2010-10-24
> **tb75252 said:**
> So, after an x amount of minutes, the screen freeze and dims to a light gray color, Underneath I can still see text and images of the application that I am using at the moment but for  a five- and sometimes ten-second moment I cannot do anything although I can move the mouse on the screen.  

It happened with me when one of the programs stops responding and I do nothing but wait for it to back to normal.

> 
The mouse moves but the icons etc are not responsive; also, typing does not output anything to the screen.

You mean it (mouse) does move while the screen is gray, right?
Or you can't do anything even after the screen is back to normal?

> 
My video card is **EVGA NVIDIA GeForce 6200**.  Going into System -> Administration I can see that there is a driver installed called **NVIDIA X-Server Settings**.  I do not know if this driver is the correct one for my card and how to tweak that driver.  It installed itself when I loaded Ubuntu, I guess.


I'm not very sure about this ... you may check the forum as there are lots of threads about Nvidia.

> 
I should also add that when I was using Microsoft Windows XP SP3 none of this was happening.
Yes, I thought your screen turns to BLACK and then back to normal.
Do you still have XP? can you double check? just to make sure everything is fine with your monitor.

---

### Post by tb75252 on 2010-10-24
> **amjjawad said:**
> It happened with me when one of the programs stops responding and I do nothing but wait for it to back to normal.


You mean it (mouse) does move while the screen is gray, right?
Or you can't do anything even after the screen is back to normal?



I'm not very sure about this ... you may check the forum as there are lots of threads about Nvidia.


Yes, I thought your screen turns to BLACK and then back to normal.
Do you still have XP? can you double check? just to make sure everything is fine with your monitor.

Yes, the mouse moves while the light of the screen dims and the screen takes a grayish tint.  After this screen dimming etc. is over, I can resume normal operations with mouse and keyboard.

I temporarily reinstalled my old Windows XP hard drive to make sure that everything was ok.  The screen does not dim or have a grayish tint with Windows XP!  It's got to be some setting or incompatibility within Ubuntu.

I'll poke around the forums to see what kind of problems people have with the Nvidia Linux driver and if somebody has found a way around it.

---

### Post by amjjawad on 2010-10-24
> **tb75252 said:**
> Yes, the mouse moves while the light of the screen dims and the screen takes a grayish tint.  After this screen dimming etc. is over, I can resume normal operations with mouse and keyboard.

I temporarily reinstalled my old Windows XP hard drive to make sure that everything was ok.  The screen does not dim or have a grayish tint with Windows XP!  It's got to be some setting or incompatibility within Ubuntu.

I'll poke around the forums to see what kind of problems people have with the Nvidia Linux driver and if somebody has found a way around it.

It happens with me but not frequently, only when one of the programs stops responding.

Please, would you list your machine's specifications and how did you install Ubuntu, partitions, etc?

Thank you!

---

### Post by tb75252 on 2010-10-24
> **amjjawad said:**
> It happens with me but not frequently, only when one of the programs stops responding.

Please, would you list your machine's specifications and how did you install Ubuntu, partitions, etc?

Thank you!

The motherboard is a Tyan Trinity 400 (S1854).  The microprocessor is a Pentium III 1100 MHz.  The computer has 1.5 GB of Crucial ram (that's the max for this PC!).  The HD is an 80 GB Western Digital EIDE.  The video card is EVGA Nvidia GeFoce 6200 (AGP bus type, 512MB DDR).  The LCD is an HNC iX-191APB.  I think I've mentioned the most important specs...

I've installed Ubuntu using the whole HD and accepted the default installation for partitions.  (I do not know how to check what partitions I have but I can assure you that it is the default suggested by Ubuntu.)  There is no other OS installed on the HD.

---

### Post by cariboo on 2010-10-24
It sounds like a process is using all you resources, you can check resource usage with System->Administration->System Monitor, be aware that the System Monitor creates it's own overhead, so you won't get a truly accurate reading, but it should be good enough to help diagnose the problem. To get a more accurate reading of resource usage, you can open an Applications->Accessories->Terminal and type:

```
top
```

---

### Post by tb75252 on 2010-10-24
> **cariboo907 said:**
> It sounds like a process is using all you resources, you can check resource usage with System->Administration->System Monitor, be aware that the System Monitor creates it's own overhead, so you won't get a truly accurate reading, but it should be good enough to help diagnose the problem. To get a more accurate reading of resource usage, you can open an Applications->Accessories->Terminal and type:

```
top
```

I am showing below the output of command "top".  Being an inexperienced computer user, I am not quite sure what it is telling me...

tb@Tb-caabc42553dc:~$ top

top - 14:00:44 up  2:24,  2 users,  load average: 1.41, 1.42, 1.43
Tasks: 126 total,   1 running, 125 sleeping,   0 stopped,   0 zombie
Cpu(s): 18.4%us,  4.9%sy,  0.0%ni, 76.7%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   1543336k total,   802008k used,   741328k free,    48372k buffers
Swap:  3227644k total,        0k used,  3227644k free,   302352k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                                                                              
 1456 tb        20   0  204m 149m  19m S 16.3  9.9  21:04.83 plugin-containe                                                                                                                                      
  859 root      20   0  125m  54m  12m S  5.9  3.6   9:38.21 Xorg                                                                                                                                                 
 1408 tb        20   0  452m 130m  29m S  5.5  8.7  19:39.24 firefox-bin                                                                                                                                          
 1629 tb        20   0 88040  12m 9.8m S  2.9  0.8   0:02.13 gnome-terminal                                                                                                                                       
 1179 tb        20   0 72500  43m  10m S  1.6  2.9   5:01.18 compiz                                                                                                                                               
 1652 tb        20   0  2620 1116  824 R  0.7  0.1   0:00.22 top                                                                                                                                                  
    1 root      20   0  2892 1648 1180 S  0.0  0.1   0:00.64 init                                                                                                                                                 
    2 root      20   0     0    0    0 S  0.0  0.0   0:00.00 kthreadd                                                                                                                                             
    3 root      20   0     0    0    0 S  0.0  0.0   0:00.19 ksoftirqd/0                                                                                                                                          
    4 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 migration/0                                                                                                                                          
    5 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 watchdog/0                                                                                                                                           
    6 root      20   0     0    0    0 S  0.0  0.0   0:00.90 events/0                                                                                                                                             
    7 root      20   0     0    0    0 S  0.0  0.0   0:00.00 cpuset                                                                                                                                               
    8 root      20   0     0    0    0 S  0.0  0.0   0:00.00 khelper                                                                                                                                              
    9 root      20   0     0    0    0 S  0.0  0.0   0:00.00 netns                                                                                                                                                
   10 root      20   0     0    0    0 S  0.0  0.0   0:00.00 async/mgr                                                                                                                                            
   11 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pm                                                                                                                                                   
   12 root      20   0     0    0    0 S  0.0  0.0   0:00.02 sync_supers                                                                                                                                          
   13 root      20   0     0    0    0 S  0.0  0.0   0:00.04 bdi-default                                                                                                                                          
   14 root      20   0     0    0    0 S  0.0  0.0   0:00.00 kintegrityd/0                                                                                                                                        
   15 root      20   0     0    0    0 S  0.0  0.0   0:00.13 kblockd/0                                                                                                                                            
   16 root      20   0     0    0    0 S  0.0  0.0   0:00.00 kacpid                                                                                                                                               
   17 root      20   0     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify                                                                                                                                         
   18 root      20   0     0    0    0 S  0.0  0.0   0:00.00 kacpi_hotplug                                                                                                                                        
   19 root      20   0     0    0    0 S  0.0  0.0   0:00.00 ata_aux                                                                                                                                              
   20 root      20   0     0    0    0 S  0.0  0.0   0:00.64 ata_sff/0                                                                                                                                            
   21 root      20   0     0    0    0 S  0.0  0.0   0:00.00 khubd                                                                                                                                                
   22 root      20   0     0    0    0 S  0.0  0.0   0:00.01 kseriod                                                                                                                                              
   23 root      20   0     0    0    0 S  0.0  0.0   0:00.00 kmmcd                                                                                                                                                
   25 root      20   0     0    0    0 S  0.0  0.0   0:00.00 khungtaskd                                                                                                                                           
   26 root      20   0     0    0    0 S  0.0  0.0   0:00.00 kswapd0                                                                                                                                              
   27 root      25   5     0    0    0 S  0.0  0.0   0:00.00 ksmd                                                                                                                                                 
   28 root      20   0     0    0    0 S  0.0  0.0   0:00.00 aio/0                                                                                                                                                
   29 root      20   0     0    0    0 S  0.0  0.0   0:00.00 ecryptfs-kthrea                                                                                                                                      
   30 root      20   0     0    0    0 S  0.0  0.0   0:00.00 crypto/0                                                                                                                                             
   37 root      20   0     0    0    0 S  0.0  0.0   0:00.00 kstriped                                                                                                                                             
   38 root      20   0     0    0    0 S  0.0  0.0   0:00.00 kmpathd/0                                                                                                                                            
   39 root      20   0     0    0    0 S  0.0  0.0   0:00.00 kmpath_handlerd                                                                                                                                      
   40 root      20   0     0    0    0 S  0.0  0.0   0:00.00 ksnapd                                                                                                                                               
   41 root      20   0     0    0    0 S  0.0  0.0   0:00.00 kondemand/0                                                                                                                                          
   42 root      20   0     0    0    0 S  0.0  0.0   0:00.00 kconservative/0                                                                                                                                      
  177 root      20   0     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_0                                                                                                                                            
  179 root      20   0     0    0    0 S  0.0  0.0   0:01.42 scsi_eh_1                                                                                                                                            
  198 root      20   0     0    0    0 S  0.0  0.0   0:00.29 jbd2/sda1-8                                                                                                                                          
  199 root      20   0     0    0    0 S  0.0  0.0   0:00.00 ext4-dio-unwrit                                                                                                                                      
  261 root      20   0  2392  604  460 S  0.0  0.0   0:00.15 upstart-udev-br                                                                                                                                      
  265 root      16  -4  2636  968  340 S  0.0  0.1   0:00.16 udevd                                                                                                                                                
  403 root      18  -2  2632  872  248 S  0.0  0.1   0:00.00 udevd                                                                                                                                                
  408 root      20   0     0    0    0 S  0.0  0.0   0:00.00 kpsmoused                                                                                                                                            
  415 root      18  -2  2632  876  252 S  0.0  0.1   0:00.00 udevd                                                                                                                                                
  532 syslog    20   0 33572 1164  972 S  0.0  0.1   0:00.20 rsyslogd                                                                                                                                             
  567 messageb  20   0  3448 1684  856 S  0.0  0.1   0:00.72 dbus-daemon                                                                                                                                          
  590 avahi     20   0  3012 1320 1088 S  0.0  0.1   0:00.08 avahi-daemon                                                                                                                                         
  592 root      20   0 19128 3968 3332 S  0.0  0.3   0:00.13 NetworkManager                                                                                                                                       
  594 avahi     20   0  3012  436  216 S  0.0  0.0   0:00.00 avahi-daemon                                                                                                                                         
  603 root      20   0  4432 2480 2004 S  0.0  0.2   0:00.07 modem-manager                                                                                                                                        
  627 root      20   0  4900 1504 1244 S  0.0  0.1   0:00.00 wpa_supplicant                                                                                                                                       
  629 root      20   0  2300  972  848 S  0.0  0.1   0:00.00 dhclient                                                                                                                                             
  632 root      20   0     0    0    0 S  0.0  0.0   0:00.00 kgameportd                                                                                                                                           
  702 root      20   0  1856  548  468 S  0.0  0.0   0:00.00 getty                                                                                                                                                
  707 root      20   0  1856  552  472 S  0.0  0.0   0:00.00 getty                                                                                                                                                
  715 root      20   0  1856  548  472 S  0.0  0.0   0:00.00 getty                                                                                                                                                
  717 root      20   0  1856  548  472 S  0.0  0.0   0:00.00 getty                                                                                                                                                
  720 root      20   0  1856  544  472 S  0.0  0.0   0:00.00 getty                                                                                                                                                
  723 root      20   0  2116  892  532 S  0.0  0.1   0:00.00 acpid                                                                                                                                                
  726 root      20   0  2460  872  688 S  0.0  0.1   0:00.01 cron                                                                                                                                                 
  727 daemon    20   0  2316  352  224 S  0.0  0.0   0:00.00 atd                                                                                                                                                  
  741 root      20   0 19544 3192 2672 S  0.0  0.2   0:00.07 gdm-binary                                                                                                                                           
  763 root      20   0  7176 2660 1732 S  0.0  0.2   0:00.05 cupsd                                                                                                                                                
  767 root      20   0 19984 2956 2348 S  0.0  0.2   0:00.16 console-kit-dae

---

### Post by gwmelchi on 2010-11-11
I am having exactly the same problem and my computer is not old (Its a white box with an Intel D975XBX2 system board, Intel Core2Duo E 6400 2.1Ghz and a ton of DDR2 RAM).  The problem is most noticeable when I am in OpenOffice and retrieve an odt document; but it happens with other programs as well.  System monitor does not indicate heavy resource use.

---

