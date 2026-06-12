---
title: "CPU maxed out with nothing running"
date: 2011-03-23
forum: New to Ubuntu
---

### Post by tony.morse on 2011-03-23
Hi, so my cpu seems to be around 60% if the system monitor is minimised and around 90-100% if it's maximised, nothing else is running and all processes in the system monitor are at 0

Ubuntu 10.04
Athlon XP2200+ (yea I know...)

So I had an NVIDIA card in there but it died and I've now got an ATI HD 4600. I usually stay away from ATI but NVIDIA stopped making card for an agp port ages ago and so I thought this was a better bet. I might be wrong but it could be that the CPU is doing all the graphics and not using the card properly? is that plausible? I've got the ati restricted drivers installed and the ati catalyst centre seems to work fine and see the card etc.

So is it the graphics? or is something else running that I don't know about? What would you recommend doing to sort this out (perhaps with the exception of binning the computer and buying something from this decade).

Cheers
Tony

---

### Post by Hero1969 on 2011-03-23
Go to System>Preference>System Monitor and click on process.  That will tell you what is running and might give you a clue if you have a problem.

---

### Post by aaaaalex on 2011-03-23
Lets find out then...

What process is using up all the juice?

Open a commmand line and execute: top

It will most likely be something like UbuntuOne (beam) or some other service that is permanently doing something.

---

### Post by tony.morse on 2011-03-23
in the %CPU column, only system monitor itself is greater than 0 and that's bouncing around between 10-20% so processes doesn't account for the CPU usage

---

### Post by tony.morse on 2011-03-23
actually it seems that clicking on the resources tab takes up the CPU usage from 0-20% so it's the actual drawing of the graphs that eats up my CPU... is this right? should I be worried? is my GPU working or not, I would expect this to be a GPU issue right?

---

### Post by aaaaalex on 2011-03-23
> **tony.morse said:**
> in the %CPU column, only system monitor itself is greater than 0 and that's bouncing around between 10-20% so processes doesn't account for the CPU usage

Then who is? Paste the result of ```
top -n 10
``` so we can take a closer look.

---

### Post by cottfcfan on 2011-03-23
To see if its a graphics card problem type "fglrxinfo" in a terminal and if theres any sign of "mesa" there could be a problem.
If "ATI Technologies" is mentioned its probably installed ok.
Have you remembered to delete the radeon driver.
```
sudo apt-get remove --purge xserver-xorg-video-radeon
```
Sometimes they conflict.

---

### Post by tony.morse on 2011-03-23
top -n 10

Tasks: 134 total,   1 running, 133 sleeping,   0 stopped,   0 zombie
Cpu(s): 14.6%us,  3.2%sy,  0.0%ni, 82.2%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   1026484k total,   771808k used,   254676k free,   107204k buffers
Swap:  3004112k total,        0k used,  3004112k free,   367748k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                                                                                                         
 1009 root      20   0  133m  76m  16m S 10.4  7.6  10:56.71 Xorg                                                                                                                                                                            
 2618 tony      20   0 45936  13m 9860 S  4.2  1.3   0:01.17 gnome-terminal                                                                                                                                                                  
 2281 tony      20   0 29548   9m 8144 S  1.3  1.0   0:14.23 gkrellm                                                                                                                                                                         
    6 root      20   0     0    0    0 D  0.3  0.0   0:01.12 events/0                                                                                                                                                                        
 1387 tony      20   0 31788  18m 4148 S  0.3  1.8   0:07.79 ubuntuone-syncd                                                                                                                                                                 
 2638 tony      20   0  2544 1184  888 R  0.3  0.1   0:00.09 top                                                                                                                                                                             
    1 root      20   0  2808 1608 1164 S  0.0  0.2   0:00.42 init                                                                                                                                                                            
    2 root      20   0     0    0    0 S  0.0  0.0   0:00.00 kthreadd                                                                                                                                                                        
    3 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 migration/0                                                                                                                                                                     
    4 root      20   0     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0                                                                                                                                                                     
    5 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 watchdog/0                                                                                                                                                                      
    7 root      20   0     0    0    0 S  0.0  0.0   0:00.00 cpuset                                                                                                                                                                          
    8 root      20   0     0    0    0 S  0.0  0.0   0:00.00 khelper                                                                                                                                                                         
    9 root      20   0     0    0    0 S  0.0  0.0   0:00.00 netns                                                                                                                                                                           
   10 root      20   0     0    0    0 S  0.0  0.0   0:00.00 async/mgr                                                                                                                                                                       
   11 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pm                                                                                                                                                                              
   12 root      20   0     0    0    0 S  0.0  0.0   0:00.00 sync_supers                                                                                                                                                                     
   13 root      20   0     0    0    0 S  0.0  0.0   0:00.00 bdi-default                                                                                                                                                                     
   14 root      20   0     0    0    0 S  0.0  0.0   0:00.00 kintegrityd/0                                                                                                                                                                   
   15 root      20   0     0    0    0 S  0.0  0.0   0:00.02 kblockd/0                                                                                                                                                                       
   16 root      20   0     0    0    0 S  0.0  0.0   0:00.00 kacpid                                                                                                                                                                          
   17 root      20   0     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify                                                                                                                                                                    
   18 root      20   0     0    0    0 S  0.0  0.0   0:00.00 kacpi_hotplug                                                                                                                                                                   
   19 root      20   0     0    0    0 S  0.0  0.0   0:00.40 ata/0                                                                                                                                                                           
   20 root      20   0     0    0    0 S  0.0  0.0   0:00.00 ata_aux                                                                                                                                                                         
   21 root      20   0     0    0    0 S  0.0  0.0   0:00.00 ksuspend_usbd                                                                                                                                                                   
   22 root      20   0     0    0    0 S  0.0  0.0   0:00.00 khubd                                                                                                                                                                           
   23 root      20   0     0    0    0 S  0.0  0.0   0:00.00 kseriod                                                                                                                                                                         
   24 root      20   0     0    0    0 S  0.0  0.0   0:00.00 kmmcd                                                                                                                                                                           
   27 root      20   0     0    0    0 S  0.0  0.0   0:00.00 khungtaskd                                                                                                                                                                      
   28 root      20   0     0    0    0 S  0.0  0.0   0:00.00 kswapd0                                                                                                                                                                         
   29 root      25   5     0    0    0 S  0.0  0.0   0:00.00 ksmd                                                                                                                                                                            
   30 root      20   0     0    0    0 S  0.0  0.0   0:00.00 aio/0                                                                                                                                                                           
   31 root      20   0     0    0    0 S  0.0  0.0   0:00.00 ecryptfs-kthrea                                                                                                                                                                 
   32 root      20   0     0    0    0 S  0.0  0.0   0:00.00 crypto/0                                                                                                                                                                        
   38 root      20   0     0    0    0 S  0.0  0.0   0:00.00 kstriped                                                                                                                                                                        
   39 root      20   0     0    0    0 S  0.0  0.0   0:00.00 kmpathd/0                                                                                                                                                                       
   40 root      20   0     0    0    0 S  0.0  0.0   0:00.00 kmpath_handlerd                                                                                                                                                                 
   41 root      20   0     0    0    0 S  0.0  0.0   0:00.00 ksnapd                                                                                                                                                                          
   42 root      20   0     0    0    0 S  0.0  0.0   0:00.00 kondemand/0                                                                                                                                                                     
   43 root      20   0     0    0    0 S  0.0  0.0   0:00.00 kconservative/0                                                                                                                                                                 
  200 root      20   0     0    0    0 S  0.0  0.0   0:00.00 usbhid_resumer                                                                                                                                                                  
  203 root      20   0     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_0                                                                                                                                                                       
  204 root      20   0     0    0    0 S  0.0  0.0   0:00.75 scsi_eh_1                                                                                                                                                                       
  225 root      20   0     0    0    0 S  0.0  0.0   0:00.18 kjournald                                                                                                                                                                       
  258 root      20   0     0    0    0 S  0.0  0.0   0:00.03 flush-8:0                                                                                                                                                                       
  285 root      20   0  2312  836  640 S  0.0  0.1   0:00.10 upstart-udev-br                                                                                                                                                                 
  287 root      16  -4  2656  944  316 S  0.0  0.1   0:00.07 udevd                                                                                                                                                                           
  578 syslog    20   0 33520 1480 1012 S  0.0  0.1   0:00.09 rsyslogd                                                                                                                                                                        
  603 messageb  20   0  3204 1564  756 S  0.0  0.2   0:00.58 dbus-daemon

---

### Post by tony.morse on 2011-03-23
fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 4600 Series  
OpenGL version string: 3.2.9756 Compatibility Profile Context


This is a fresh install with the new hardware so no old graphics drives around

---

### Post by tony.morse on 2011-03-23
delete the radeon driver? but this is a radeon HD 4600, should I really do that?

---

### Post by cottfcfan on 2011-03-23
No. This is the open source Radeon Driver, that will automatically be installed because of your card. Not the fglrx proprietary driver that you installed.
Although I notice you're running 10.04, this is more a problem on 10.10 according to the official ATI page.
[http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide)
But it won't harm to try.

---

### Post by aaaaalex on 2011-03-23
Looking at your initial post and your paste of the output of top i really don't see your problem. :-D 

If i open the gnome-system-monitor on the system i am currently sitting on (also an older computer it immediatly eats about 18% CPU. Thats the trade off of having all those fancy graphs i guess.

---

