---
title: "slow performance issues"
date: 2010-09-16
forum: New to Ubuntu
---

### Post by kschumake83 on 2010-09-16
im very new to ubuntu. i just installed it yesterday.  well my issue is that ubuntu 10.4 on my dell desktop with a celeron d processor 2.somthing ghz runs like an old 386sx. it is so slow its almost useless.  im dual booting so i still have windows xp on the computer so if i have do do something important i can.  so i guess what im asking is there any performance modifications that i should do or is my computer just too slow for ubuntu 10.4.  it was even verry slow when i had it as my only operating system last night, so i installed windows with a partition for ubuntu.

---

### Post by sikander3786 on 2010-09-16
How much amount of RAM do you have in your system? And which GPU? Run the following command in a terminal and post the output so we can have a look at all the running processes.

```

top

```

I think your PC should be capable of running Ubuntu. Still it'll be better to try out some light DEs e.g, XFCE or LXDE. You can install them on already install XFCE in existing Ubuntu install by using the following command and then swithc between GNOME and XFCE at the GDM Login Screen.

```

sudo apt-get update && sudo apt-get install xubuntu-desktop

```

---

### Post by kschumake83 on 2010-09-16
i think i have 256 mb ram and here is the "top" you wanted



top - 14:23:55 up 14 min,  2 users,  load average: 2.63, 2.79, 1.95
Tasks: 137 total,   2 running, 135 sleeping,   0 stopped,   0 zombie
Cpu(s): 28.7%us, 12.0%sy,  0.0%ni, 48.3%id, 11.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:    248936k total,   244804k used,     4132k free,    16984k buffers
Swap:   261112k total,    62084k used,   199028k free,    89284k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 9149 owner     20   0  292m  46m  16m S 14.3 19.0   0:13.38 firefox-bin        
  853 root      20   0 38104 9644 5252 R 12.3  3.9   0:23.66 Xorg               
 1348 owner     20   0 46308 7856 5024 S  5.0  3.2   0:07.93 gnome-terminal     
 1288 owner     20   0 39564 7648 5356 S  4.6  3.1   0:00.91 wnck-applet        
 1238 owner     20   0 42968 9420 4892 S  1.7  3.8   0:05.72 gnome-panel        
  199 root      20   0  2860  920  648 S  1.0  0.4   0:45.87 mount.ntfs         
 1235 owner     20   0 62808 8880 2680 S  1.0  3.6   0:06.68 compiz             
  208 root       0 -20     0    0    0 S  0.7  0.0   0:10.83 loop0              
 1219 owner     20   0 89236 3756 2240 S  0.3  1.5   0:00.79 gnome-settings-    
 1239 owner     20   0 69288 6948 4052 S  0.3  2.8   0:02.13 nautilus           
 1272 root      20   0  5176  536  440 S  0.3  0.2   0:00.28 udisks-daemon      
 9136 owner     20   0  2544  928  648 R  0.3  0.4   0:00.56 top                
    1 root      20   0  2792  820  484 S  0.0  0.3   0:00.62 init               
    2 root      20   0     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      20   0     0    0    0 S  0.0  0.0   0:00.04 ksoftirqd/0        
    5 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 watchdog/0

---

### Post by kschumake83 on 2010-09-16
oh sorry about the double post but i just wanted to say thank you for the quick reply and for your help

edit...  i tried installing the updates on the desktop and my computer crashed in the middle of it, now when i  restart the computer it goes to the login screen but my keyboard and mouse do not work.  if i go into the other thing i forget what its called in the kernel selection screen, it locks up. i dont know enough about grub commands to do anything about it. any help would be appreciated

---

### Post by Claus7 on 2010-09-16
Hello,

from what I can get, your pc is so slow cause the memory is not enough. Xubuntu might be a nice alternative to such specifications. 

You can go also to System->Administration->System monitor and check out some applications you might get rid of, yet your memory is not enough nowadays.

Regards!

---

### Post by Claus7 on 2010-09-16
Hello,

> **kschumake83 said:**
> oh sorry about the double post but i just wanted to say thank you for the quick reply and for your help

edit...  i tried installing the updates on the desktop and my computer crashed in the middle of it, now when i  restart the computer it goes to the login screen but my keyboard and mouse do not work.  if i go into the other thing i forget what its called in the kernel selection screen, it locks up. i dont know enough about grub commands to do anything about it. any help would be appreciated

it would be nice to start a new thread since that way you are messing things up by mixing problems.

Now concerning your new problem, are you able to start on recovery mode? This is the other thing you say? In case you do then choose command line mode and type the following commands:
[http://ubuntuforums.org/showpost.php?p=7903838&postcount=5](http://ubuntuforums.org/showpost.php?p=7903838&postcount=5)

Hope this helps you to solve the problem you are facing.

Regards!

---

### Post by sandyd on 2010-09-16
> **kschumake83 said:**
> i think i have 256 mb ram and here is the "top" you wanted



top - 14:23:55 up 14 min,  2 users,  load average: 2.63, 2.79, 1.95
Tasks: 137 total,   2 running, 135 sleeping,   0 stopped,   0 zombie
Cpu(s): 28.7%us, 12.0%sy,  0.0%ni, 48.3%id, 11.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:    248936k total,   244804k used,     4132k free,    16984k buffers
Swap:   261112k total,    62084k used,   199028k free,    89284k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 9149 owner     20   0  292m  46m  16m S 14.3 19.0   0:13.38 firefox-bin        
  853 root      20   0 38104 9644 5252 R 12.3  3.9   0:23.66 Xorg               
 1348 owner     20   0 46308 7856 5024 S  5.0  3.2   0:07.93 gnome-terminal     
 1288 owner     20   0 39564 7648 5356 S  4.6  3.1   0:00.91 wnck-applet        
 1238 owner     20   0 42968 9420 4892 S  1.7  3.8   0:05.72 gnome-panel        
  199 root      20   0  2860  920  648 S  1.0  0.4   0:45.87 mount.ntfs         
 1235 owner     20   0 62808 8880 2680 S  1.0  3.6   0:06.68 compiz             
  208 root       0 -20     0    0    0 S  0.7  0.0   0:10.83 loop0              
 1219 owner     20   0 89236 3756 2240 S  0.3  1.5   0:00.79 gnome-settings-    
 1239 owner     20   0 69288 6948 4052 S  0.3  2.8   0:02.13 nautilus           
 1272 root      20   0  5176  536  440 S  0.3  0.2   0:00.28 udisks-daemon      
 9136 owner     20   0  2544  928  648 R  0.3  0.4   0:00.56 top                
    1 root      20   0  2792  820  484 S  0.0  0.3   0:00.62 init               
    2 root      20   0     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      20   0     0    0    0 S  0.0  0.0   0:00.04 ksoftirqd/0        
    5 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 watchdog/0

> **Claus7 said:**
> Hello,

from what I can get, your pc is so slow cause the memory is not enough. Xubuntu might be a nice alternative to such specifications. 

You can go also to System->Administration->System monitor and check out some applications you might get rid of, yet your memory is not enough nowadays.

Regards!
No. Xubuntu is already too heavy for 256.
Would reccomend that you use something like crunchbang or puppy

---

### Post by Claus7 on 2010-09-16
Hello,

> **sandyd said:**
> No. Xubuntu is already too heavy for 256.
Would reccomend that you use something like crunchbang or puppy

having tested it in a machine with similar specs, it was not "flying", yet the performance was boosted a lot. The comparison to windows was just...incomparable. No objection that there might be even lighter versions, yet this is what xubuntu is famous of.

Regards!

---

### Post by sandyd on 2010-09-16
> **Claus7 said:**
> Hello,



having tested it in a machine with similar specs, it was not "flying", yet the performance was boosted a lot. The comparison to windows was just...incomparable. No objection that there might be even lighter versions, yet this is what xubuntu is famous of.

Regards!
xubuntu has been growing heavier with every release of xubuntu.
Crunchbang (Ubuntu) uses openbox, which is EXTREMELY light and will likely run on 256 without any lag.

---

### Post by kschumake83 on 2010-09-16
well i got things sorted out... i just uninstalled ubuntu and installed xubuntu but the karmic koala version.  its about 3000000X faster i can actually do something with it now.  and i have  1gb memory on order hope it gets here soon then i hope it flies

---

### Post by Claus7 on 2010-09-16
Hello,

very nice you have a machine fitting your needs. And with a 1gb memory on the way things are shaping to be even better. Just a note: keep your root directory separate from the home one, so as to make easier the transfer from version to version in case you consider ubuntu is fitting better. Always take a backup first.

Nice xubuntuing,
Regards!

---

### Post by sikander3786 on 2010-09-17
That was the RAM causing slow performance. 256MB is too low for GNOME but reasonable for XFCE. You might once again want to try out standard Ubuntu once 1GB flies to you. In that case keep your home partition separate as Claus7 mentioned.

Regards.

---

