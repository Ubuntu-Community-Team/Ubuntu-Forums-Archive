---
title: "extremely slow ubuntu."
date: 2009-01-18
forum: New to Ubuntu
---

### Post by pankirk on 2009-01-18
Hello people of Ubuntu forums! I recently installed a fresh version of ubuntu 8.10 and I really like it! The only draw back is that it's so darn slow! I'm not trying to talk trash or flame here, but even windows 7 bets is faster then this. It takes far longer to boot then windows ever did, and it takes even longer for firefox to start up. When I drag a window across the screen, it bugs out a little bit and I hav to wait for it to calm down before I can use my computer again. And when browsing the web in Firefox, each page renders so unbelievably slow I cant stand it. Im desperately seeking help and serously contemplating scrapping linux jsut for this ridiculousness! Are there any tweak guides or something at all? even using my third mouse wheel to scroll between desktops, it lags so much.

Computer specs:
CPU: AMD athlon 6400 3.0ghzs
RAM: PQI turbo 800mhz (2gigs)
Video card: Nvidia 8800GT (Yes, I have the proper drivers...)


And if you're goign to ask me what the output of "top" is then well, here:

> top - 23:17:58 up  1:15,  2 users,  load average: 0.19, 0.18, 0.22
Tasks: 133 total,   1 running, 132 sleeping,   0 stopped,   0 zombie
Cpu(s):  6.2%us,  0.8%sy,  0.0%ni, 92.9%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   2071772k total,   735964k used,  1335808k free,    27140k buffers
Swap:  5992204k total,        0k used,  5992204k free,   339060k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                      
 5740 root      20   0  345m  45m  11m S    9  2.3   8:55.50 Xorg                                         
 8645 patrick   20   0  243m  99m  27m S    4  4.9   1:45.29 firefox                                      
 6124 patrick   20   0 74688  43m  20m S    1  2.1   0:33.78 compiz.real                                  
 9069 patrick   20   0 98.6m  24m  13m S    1  1.2   0:01.26 gnome-terminal                               
 6121 patrick   20   0 21248 4236 2884 S    1  0.2   0:08.36 gnome-screensav                              
    1 root      20   0  3056 1888  564 S    0  0.1   0:01.24 init                                         
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd                                     
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0                                  
    4 root      15  -5     0    0    0 S    0  0.0   0:00.16 ksoftirqd/0                                  
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0                                   
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1                                  
    7 root      15  -5     0    0    0 S    0  0.0   0:00.48 ksoftirqd/1                                  
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1                                   
    9 root      15  -5     0    0    0 S    0  0.0   0:00.04 events/0                                     
   10 root      15  -5     0    0    0 S    0  0.0   0:00.04 events/1                                     
   11 root      15  -5     0    0    0 S    0  0.0   0:00.00 khelper                                      
   51 root      15  -5     0    0    0 S    0  0.0   0:00.00 kintegrityd/0                                
   52 root      15  -5     0    0    0 S    0  0.0   0:00.00 kintegrityd/1                                
   54 root      15  -5     0    0    0 S    0  0.0   0:00.00 kblockd/0                                    
   55 root      15  -5     0    0    0 S    0  0.0   0:00.00 kblockd/1                                    
   57 root      15  -5     0    0    0 S    0  0.0   0:00.00 kacpid                                       
   58 root      15  -5     0    0    0 S    0  0.0   0:00.00 kacpi_notify                                 
  180 root      15  -5     0    0    0 S    0  0.0   0:00.00 cqueue                                       
  184 root      15  -5     0    0    0 S    0  0.0   0:00.00 kseriod                                      
  229 root      20   0     0    0    0 S    0  0.0   0:00.00 pdflush                                      
  230 root      20   0     0    0    0 S    0  0.0   0:00.12 pdflush                                      
  231 root      15  -5     0    0    0 S    0  0.0   0:00.00 kswapd0                                      
  273 root      15  -5     0    0    0 S    0  0.0   0:00.00 aio/0                                        
  274 root      15  -5     0    0    0 S    0  0.0   0:00.00 aio/1                                        
 1384 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksuspend_usbd                                
 1415 root      15  -5     0    0    0 S    0  0.0   0:00.00 khubd                                        



If you have any questions about my predicament or comments on how to fix this lag please tell me! Thanks so much in advance!

---

### Post by Muffinabus on 2009-01-18
Hmm, after reading of your problems I immediately thought "video drivers" but you claim to have them properly installed.

---

### Post by pankirk on 2009-01-18
Yes, I claim to have them installed. I'm not sure if they're the right version or what not, but I go to system>Administration>NVIDIA X settings and it brings me to my nvidia driver program that I got from the restricted drivers application. Should I try getting different drivers from envy?

---

