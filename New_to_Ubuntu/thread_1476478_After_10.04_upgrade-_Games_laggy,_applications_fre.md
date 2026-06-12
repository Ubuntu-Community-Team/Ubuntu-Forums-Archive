---
title: "After 10.04 upgrade- Games laggy, applications freeze"
date: 2010-05-07
forum: New to Ubuntu
---

### Post by sodra on 2010-05-07
After I upgraded to 10.04, My 3d games are laggy (not the internet, it looses frames) and applications like Firefox and Pidgin freeze

I need help!

---

### Post by ubunterooster on 2010-05-07
Go to system>administration>system monitor.

Are CPU or RAM used up?

---

### Post by sodra on 2010-05-07
I have a Dual-Core Athlon

CPU1-96% used
CPU2-96% used

---

### Post by chuckyp on 2010-05-07
Use top and see what is using all your core thats a lot of cpu usage. My first thought would be video drivers aren't installed properly.

---

### Post by sodra on 2010-05-07
```
 6547 root      20   0  129m  59m  19m R   26  2.2   6:17.38 Xorg               
 1279 root      20   0 84048  62m  13m R   24  2.3 130:48.90 Xorg               
13992 edwin     20   0  283m  61m  25m S    7  2.2   1:03.93 chrome             
10976 pgrace    20   0  255m 111m  53m S    6  4.0  29:57.05 software-center    
18690 edwin     20   0 62400  21m  16m S    2  0.8   0:21.26 gnome-system-mo    
 6802 edwin     20   0 66544  46m  14m S    2  1.7   0:24.74 compiz             
 6845 edwin      9 -11  157m 5812 4540 S    2  0.2   0:24.42 pulseaudio         
21644 pgrace    20   0 49276  15m 5216 S    1  0.6   0:00.04 ica                
11754 edwin     20   0  246m  49m  25m S    1  1.8   0:28.71 chrome             
21645 edwin     20   0 39416  11m 5064 R    1  0.4   0:00.03 ica                
 3993 pgrace    20   0 55404  13m 9932 S    1  0.5   0:57.10 wnck-applet        
 6887 edwin     20   0 63708  15m  12m S    1  0.6   0:08.94 ica                
21410 edwin     20   0 54232  13m  10m S    1  0.5   0:00.33 gnome-terminal     
 3862 pgrace    20   0  120m  20m  14m S    0  0.8   0:20.29 nautilus           
 3863 pgrace    20   0 58492  44m  12m S    0  1.6   0:30.48 compiz             
 3928 pgrace    20   0 63452  15m  12m S    0  0.6   4:48.79 ica                
 3966 pgrace    20   0 16948 2328 1940 S    0  0.1   0:01.20 gvfs-afc-volume    
```
Xorg is using 24%???

---

### Post by ubunterooster on 2010-05-07
26+24=50 actually.
There are two Xorg entries.

---

### Post by sodra on 2010-05-07
Is that bad? and when I was on 9.1 It was barely any CPU at all

---

### Post by ubunterooster on 2010-05-07
> **chuckyp said:**
> Use top and see what is using all your core thats a lot of cpu usage. My first thought would be video drivers aren't installed properly.^ this :(

You need to  edit xorg.

---

### Post by sodra on 2010-05-07
```
edwin@wesley:~$  sudo apt-get install displayconfig-gtk
[sudo] password for edwin: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package displayconfig-gtk

```
...help?

---

### Post by ubunterooster on 2010-05-07
rats. that was removed from the repositories

---

### Post by sodra on 2010-05-07
> **ubunterooster said:**
> rats. that was removed from the repositories

now what?

---

### Post by sodra on 2010-05-07
...help me? The lag is killing me...and my CPU

---

### Post by ubunterooster on 2010-05-07
Okay, I don't know how to edit Xorg personally. Try going to system>administration>Hardware drivers. If the video-card proprietary drivers are enabled, disable them for now.

---

### Post by 00arthuryu on 2010-05-09
are you using the free ATI drivers that come default with ubuntu? i.e. X1xxx or X2xxx GPUs?

---

