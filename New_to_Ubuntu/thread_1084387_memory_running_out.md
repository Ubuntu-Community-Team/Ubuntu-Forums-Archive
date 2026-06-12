---
title: "memory running out"
date: 2009-03-02
forum: New to Ubuntu
---

### Post by qvyang on 2009-03-02
I got this problem with my Ubuntu 8.04:
When I start up my system everything is fine, but eventually my memory runs out, so I have to log off and log in again just to adjust the memory. Is this a memory leak? 
This is what I got after I run top (now there is only 17% of memory left):
```

top - 00:44:02 up 1 day,  1:19,  5 users,  load average: 0.66, 0.61, 0.43
Tasks: 158 total,   1 running, 156 sleeping,   0 stopped,   1 zombie
Cpu(s):  3.1%us,  2.9%sy,  0.0%ni, 92.9%id,  0.0%wa,  0.0%hi,  1.1%si,  0.0%st
Mem:   2053660k total,  2006968k used,    46692k free,    53404k buffers
Swap:        0k total,        0k used,        0k free,   246808k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                         
30778 victor    20   0  274m  36m  12m S    4  1.8  10:29.21 python                                          
30573 root      20   0  566m 169m 8944 S    2  8.5  19:57.89 Xorg                                            
15524 victor    20   0 98600 9732 4452 S    1  0.5   3:07.53 npviewer.bin                                    
19531 victor    20   0  253m  34m  13m S    1  1.7   1:54.69 python                                          
 2751 victor    20   0  251m  25m  11m S    1  1.3   0:12.80 gnome-terminal                                  
 3036 root      20   0 1485m 504m  21m S    0 25.2   9:28.88 java                                            
 6362 root      20   0  127m 2400 1816 S    0  0.1   0:05.83 NetworkManager                                  
30773 victor    20   0  261m  44m 7640 S    0  2.2   2:18.56 compiz.real                                     
30777 victor    20   0  246m  28m  11m S    0  1.4   1:45.85 python                                          
31291 victor    20   0  670m 210m  23m S    0 10.5  11:50.88 firefox                                         
    1 root      20   0  4020  812  528 S    0  0.0   0:01.00 init                                            
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd                                        
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.88 migration/0                                     
    4 root      15  -5     0    0    0 S    0  0.0   0:25.26 ksoftirqd/0                                     
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0                                      
    9 root      15  -5     0    0    0 S    0  0.0   0:00.60 events/0                                        
   11 root      15  -5     0    0    0 S    0  0.0   0:00.00 khelper                                         

```

---

### Post by Sef on 2009-03-02
It looks like your problem is java and firefox and xorg.   Have you checked to make sure your ram is ok?  If not, then check out [memtest86]("http://memtest86.com/").

---

### Post by hyperyoda on 2009-03-02
> **qvyang said:**
> I got this problem with my Ubuntu 8.04:
When I start up my system everything is fine, but eventually my memory runs out, so I have to log off and log in again just to adjust the memory. Is this a memory leak? 
This is what I got after I run top (now there is only 17% of memory left):
```

top - 00:44:02 up 1 day,  1:19,  5 users,  load average: 0.66, 0.61, 0.43
Tasks: 158 total,   1 running, 156 sleeping,   0 stopped,   1 zombie
Cpu(s):  3.1%us,  2.9%sy,  0.0%ni, 92.9%id,  0.0%wa,  0.0%hi,  1.1%si,  0.0%st
Mem:   2053660k total,  2006968k used,    46692k free,    53404k buffers
Swap:        0k total,        0k used,        0k free,   246808k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                         
30778 victor    20   0  274m  36m  12m S    4  1.8  10:29.21 python                                          
30573 root      20   0  566m 169m 8944 S    2  8.5  19:57.89 Xorg                                            
15524 victor    20   0 98600 9732 4452 S    1  0.5   3:07.53 npviewer.bin                                    
19531 victor    20   0  253m  34m  13m S    1  1.7   1:54.69 python                                          
 2751 victor    20   0  251m  25m  11m S    1  1.3   0:12.80 gnome-terminal                                  
 3036 root      20   0 1485m 504m  21m S    0 25.2   9:28.88 java                                            
 6362 root      20   0  127m 2400 1816 S    0  0.1   0:05.83 NetworkManager                                  
30773 victor    20   0  261m  44m 7640 S    0  2.2   2:18.56 compiz.real                                     
30777 victor    20   0  246m  28m  11m S    0  1.4   1:45.85 python                                          
31291 victor    20   0  670m 210m  23m S    0 10.5  11:50.88 firefox                                         
    1 root      20   0  4020  812  528 S    0  0.0   0:01.00 init                                            
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd                                        
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.88 migration/0                                     
    4 root      15  -5     0    0    0 S    0  0.0   0:25.26 ksoftirqd/0                                     
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0                                      
    9 root      15  -5     0    0    0 S    0  0.0   0:00.60 events/0                                        
   11 root      15  -5     0    0    0 S    0  0.0   0:00.00 khelper                                         

```


Looks like you are using up your available memory but nothing looks crazy. I recommend you add some swap space. It will be a bit slower than regular physical memory but at least you can still run things when your physical memory runs out. Also you should really add more RAM to your system if possible.

Zach

---

