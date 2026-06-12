---
title: "apt-get is eating all my cpu!"
date: 2010-10-14
forum: New to Ubuntu
---

### Post by dantakeoff on 2010-10-14
hey there...
i recently upgraded my lucid setup to maverick, and have had a few small issues, all of which seem to be sorting themselves out after updating, with the exception of this one: about once during every session, my cpu gets completely bogged down by apt-get. when i kill it with system monitor, it doesnt happen again during the same session. its not very important, but as i know im not using apt-get when it does this, i am a little concerned...
also, others who use this computer do not know how to kill it, so their session is over if it happens to them...
any suggestions?

---

### Post by jtarin on 2010-10-14
Do you have updates to download and install automatically?

---

### Post by dantakeoff on 2010-10-14
> **jtarin said:**
> Do you have updates to download and install automatically?

no, i select everything manually, but after the update to maverick, i installed every update, and then reverted to my old kernel,2.6.32-24-generic
because i have a wireless card configured specifically to that kernal. you think maybe thats the problem?
my system is up to date...
thanks for your help...

---

### Post by jtarin on 2010-10-14
No I don't think thas a problem.

---

### Post by thorin39 on 2010-10-15
Have same problem after update to 10.10.

```
Tasks: 182 total,   2 running, 180 sleeping,   0 stopped,   0 zombie
Cpu(s): 31.6%us, 38.2%sy, 30.2%ni,  0.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   1016096k total,   874440k used,   141656k free,    51332k buffers
Swap:  2975740k total,   100056k used,  2875684k free,   441712k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
13315 root      30  10  7876 2232 1872 R 86.3  0.2   7:02.59 apt-get            
 1207 root      20   0 69520  22m 9440 S  4.0  2.3  31:41.40 Xorg               
13853 thorin    20   0 94004  14m  10m S  3.7  1.4   0:00.88 gnome-terminal     
13413 thorin    20   0  446m 155m  33m S  1.7 15.6   0:49.01 firefox-bin        
 1947 thorin    20   0  187m  43m  19m S  1.3  4.3  13:40.55 skype              
 1494 thorin    20   0 60836 9340 6752 S  1.0  0.9   7:37.68 compiz             
13384 thorin    20   0 65676 3340 2368 S  1.0  0.3   0:03.47 conky              
13588 thorin    20   0 70848  19m  12m S  1.0  2.0   0:02.63 plugin-containe    
 1171 zabbix    25   5  6996  800  692 S  0.3  0.1   1:28.49 zabbix_agentd      
 1174 zabbix    25   5  6996  824  656 S  0.3  0.1   0:49.39 zabbix_agentd      
 1175 zabbix    25   5  6996  824  656 S  0.3  0.1   0:50.07 zabbix_agentd      
 1482 thorin    20   0  214m  12m 9076 S  0.3  1.2   0:19.47 gnome-settings-    
 1500 thorin    20   0  131m  27m  12m S  0.3  2.8   8:38.80 docky              
 1612 thorin    20   0 30976 9.8m 8060 S  0.3  1.0   0:05.63 gtk-window-deco    
13925 thorin    20   0  2624 1156  840 R  0.3  0.1   0:00.08 top                
    1 root      20   0  2884 1548 1168 S  0.0  0.2   0:00.50 init               
    2 root      20   0     0    0    0 S  0.0  0.0   0:00.00 kthreadd    
```

Other applications do same sometimes..

---

### Post by dantakeoff on 2010-10-15
> **jtarin said:**
> No I don't.

Help.<snip>

---

### Post by dantakeoff on 2010-10-20
ok...problem seems to have dissappeared...?! good thing too, cause you lot were useless!

---

### Post by linux-hack on 2010-10-20
if it comes agen try managing the cpu for tzhe command with **nice **and **renice**

---

### Post by jtarin on 2010-10-20
> **dantakeoff said:**
> ok...problem seems to have dissappeared...?! good thing too, cause you lot were useless!Your way of expressing yourself when someone has at least responded to your request leaves a little to be desired. Make an attempt to be a little more polite and refrain from using swear words and it will go far in your search for help.

---

### Post by NightwishFan on 2010-10-20
> **dantakeoff said:**
> ok...problem seems to have dissappeared...?! good thing too, cause you lot were useless!

Not interested in helping you ever. :roll:

Especially something so simple, and potentially easy to debug.

---

### Post by Elfy on 2010-10-20
Closed.

---

