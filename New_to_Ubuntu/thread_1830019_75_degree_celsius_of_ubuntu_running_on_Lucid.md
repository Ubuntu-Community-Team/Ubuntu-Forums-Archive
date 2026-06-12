---
title: "75 degree celsius of ubuntu running on Lucid"
date: 2011-08-21
forum: New to Ubuntu
---

### Post by alfa_80 on 2011-08-21
Hi, 

I would like to know your opinions guys about temperature of my machine running ubuntu 10.04. I'm a bit worried regarding high temperature of my machine, as shown by the output of "sensors" (one of them is 75 degree).

Output of "sensors" command:
```

applesmc-isa-0300
Adapter: ISA adapter
Left side  :3248 RPM  (min = 2000 RPM)
Right side :3259 RPM  (min = 2000 RPM)
TB0T:        +38.5°C                                    
TB1T:        +38.5°C                                    
TB2T:        +36.8°C                                    
TC0C:        +58.8°C                                    
TC0D:        +63.0°C                                    
TC0P:        +61.5°C                                    
TC1C:        +66.0°C                                    
TG0D:        +61.5°C                                    
TG0P:        +56.2°C                                    
TG0T:        +60.8°C                                    
TMCD:        +66.0°C                                    
TP0P:        +64.8°C                                    
TPCD:        +75.0°C                                    
Th1H:        +52.2°C                                    
Th2H:        +51.5°C                                    
Tm0P:        +58.5°C                                    
Ts0P:        +36.0°C                                    
Ts0S:        +48.0°C                                    


``` 

The following is output of "top" command:

```

top - 12:17:35 up 2 days,  1:46,  4 users,  load average: 1.18, 1.05, 1.05
Tasks: 219 total,   2 running, 216 sleeping,   1 stopped,   0 zombie
Cpu(s):  9.6%us,  3.1%sy,  0.0%ni, 85.6%id,  0.6%wa,  0.1%hi,  0.9%si,  0.0%st
Mem:   8119332k total,  6527524k used,  1591808k free,   459364k buffers
Swap: 15625208k total,        0k used, 15625208k free,  3596624k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                                 
 2017 shah      20   0  397m 180m  21m S   15  2.3 330:04.49 npviewer.bin                                                                                            
 1352 root      20   0  359m 220m  31m R    8  2.8  93:58.97 Xorg                                                                                                    
 2944 shah      20   0 1056m 376m  35m S    7  4.7 131:44.80 firefox-bin                                                                                             
14895 shah      20   0  956m  80m  36m S    6  1.0   4:25.13 rhythmbox                                                                                               
 1595 shah      20   0  343m  19m  16m S    4  0.2  40:24.88 pulseaudio                                                                                              
 1603 shah      20   0  296m  63m  21m S    2  0.8  37:59.59 compiz                                                                                                  
 1590 shah      20   0  353m  22m  13m S    1  0.3  27:47.41 gnome-panel                                                                                             
14519 shah      20   0  309m  21m  11m S    1  0.3   0:03.97 gnome-terminal                                                                                          
14697 shah      20   0  744m  48m  24m S    1  0.6   1:11.05 nautilus                                                                                                
16014 shah      20   0  749m  44m  24m S    1  0.6   0:12.96 pidgin                                                                                                  
 5427 shah      20   0  580m 132m  14m S    1  1.7  15:49.37 evince                                                                                                  
11685 shah      20   0  461m  33m  17m S    1  0.4   9:26.18 gedit                                                                                                   
14493 shah      20   0 98.2m  31m  14m S    1  0.4   1:07.30 npviewer.bin                                                                                            
 1578 shah      20   0  469m  14m 9952 S    1  0.2  21:26.43 gnome-settings-                                                                                         
 1761 shah      20   0  349m 108m  23m S    1  1.4  50:50.13 skype                                                                                                   
 5011 shah      20   0  452m  49m  14m S    1  0.6  16:14.65 evince                                                                                                  
 5493 shah      20   0  543m 143m  16m S    1  1.8  15:49.35 evince                                                                                                  
 1701 shah      20   0  142m 5808 4552 S    1  0.1  14:58.47 indicator-me-se                                                                                         
 1260 root      20   0 83100 3676 2936 S    1  0.0  12:06.10 gdm-binary                                                                                              
 3410 shah      20   0  425m  16m  11m S    1  0.2  10:42.33 gnome-volume-co                                                                                         
 1094 root      20   0 89704 1408  740 S    0  0.0  10:41.82 pommed                                                                                                  
 6636 shah      20   0 1397m 454m  25m S    0  5.7   4:31.29 java                                                                                                    
15813 shah      20   0 19332 1508 1068 R    0  0.0   0:04.56 top                                                                                                     
   74 root      20   0     0    0    0 S    0  0.0   1:10.29 scsi_eh_1                                                                                               
   83 root      20   0     0    0    0 S    0  0.0   1:13.28 kondemand/0                                                                                             
  342 root      20   0     0    0    0 S    0  0.0   0:37.54 usb-storage                                                                                             
 1568 shah      20   0 24604 2124  668 S    0  0.0   0:22.07 dbus-daemon                                                                                             
 1642 root      20   0 46700 1064  704 S    0  0.0   0:35.40 udisks-daemon                                                                                           
 1654 shah      20   0  224m  10m 8828 S    0  0.1   3:04.92 multiload-apple                                                                                         
 1660 shah      20   0  434m  20m  12m S    0  0.3   0:16.94 indicator-apple                                                                                         
 1723 shah      20   0  223m  20m 9.8m S    0  0.3   0:13.20 python                                                                                                  
13090 root      20   0     0    0    0 S    0  0.0   0:14.00 kondemand/1                                                                                             
13104 root      20   0     0    0    0 S    0  0.0   0:11.66 kondemand/2                                                                                             
13113 root      20   0     0    0    0 S    0  0.0   0:13.03 ksoftirqd/3                                                                                             
13118 root      20   0     0    0    0 S    0  0.0   0:10.57 kondemand/3                                                                                             
13125 root      20   0     0    0    0 S    0  0.0   0:00.23 events/3                                                                                                
15154 shah      20   0  391m  22m  13m S    0  0.3   0:02.74 totem-plugin-vi                                                                                         
    1 root      20   0 23700 1956 1276 S    0  0.0   0:01.15 init                                                                                                    
    2 root      20   0     0    0    0 S    0  0.0   0:00.01 kthreadd                                                                                                
    3 root      RT   0     0    0    0 S    0  0.0   0:00.01 migration/0                                                                                             
      


```

Any comments or advice?

Thanks in advance..

---

### Post by LowSky on 2011-08-23
What model PC is it?
Is it a desktop or a laptop? If its a desktop you might want to add some fans.

---

### Post by alfa_80 on 2011-08-23
> **LowSky said:**
> What model PC is it?
Is it a desktop or a laptop? If its a desktop you might want to add some fans.

It is a Mac Book Pro 6,2.

---

### Post by kaldor on 2011-08-23
Have you installed the proprietary graphics driver?

---

### Post by 3rdalbum on 2011-08-23
Firstly, I've never met a computer where all the 'sensors' read realistic values.

Someone has told me that laptop CPUs run at 75 celcius normally, so that's probably no cause for alarm. They don't have room for the big coolers and airflow that you would have in a desktop case.

---

### Post by alfa_80 on 2011-08-24
> **kaldor said:**
> Have you installed the proprietary graphics driver?

Hi,

I have "nvidia current". Is it a  proprietary one? What is its problem?

---

