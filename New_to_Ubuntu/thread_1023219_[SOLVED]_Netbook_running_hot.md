---
title: "[SOLVED] Netbook running hot"
date: 2008-12-27
forum: New to Ubuntu
---

### Post by greenleaves123 on 2008-12-27
I have a Dell Inspiron Mini 9 with Ubuntu 8.04. I got the temperature monitoring on the advice of someone here. My netbook was in the green, but now it's in the orange. It's running at around 53 Celsius.

I searched for this problem and did typed top in the terminal. I can't cut and paste the results for some reason. The programs keep changing too.

I copied a bit of it:

22% cpu java
8% cpu firefox
2% cpu xorg
1% cpu python

There were others, again, I couldn't copy and paste or cut and paste and it kept changing. I am worried about my netbook running hot as it overheated yesterday, so much so that it was too hot to touch.

How do I stop some of these applications from running and which ones should I stop?

---

### Post by jrusso2 on 2008-12-27
If its still under warranty I would talk to Dell while it is still covered.

---

### Post by Michael.Godawski on 2008-12-27
hey greenleaves123, 

usually overheating is caused by bad hardware not bad software.

To copy and paste from the terminal either select the passage you want with the mouse, highlighting it, and then press the middle mouse button to paste it here;

or copy with ctrl+shift+c and paste with ctrl+v.

---

### Post by greenleaves123 on 2008-12-27
I pressed ctr+shift+c then it make the words stop changing and then I could copy and paste.

Here is what I got from top:

top - 18:23:19 up  6:44,  2 users,  load average: 0.06, 0.14, 0.24
Tasks: 114 total,   1 running, 113 sleeping,   0 stopped,   0 zombie
Cpu(s):  5.1%us,  1.6%sy,  0.0%ni, 90.9%id,  0.0%wa,  0.0%hi,  2.4%si,  0.0%st
Mem:    904380k total,   892688k used,    11692k free,     4248k buffers
Swap:        0k total,        0k used,        0k free,   529216k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                         
 3914 root      20   0  341m  30m 8268 S    6  3.4  12:29.29 Xorg                                                            
10810 jenny     20   0  695m 101m  18m S    4 11.5  26:53.68 java                                                            
22065 jenny     20   0 99.6m  21m  11m S    2  2.5   0:02.06 gnome-terminal                                                  
22147 jenny     20   0  2268 1096  832 R    2  0.1   0:00.14 top                                                             
 4454 jenny     20   0 40988  15m   9m S    1  1.8   0:48.59 nm-applet                                                       
21958 jenny     20   0  185m  75m  23m S    1  8.6   0:32.27 firefox                                                         
    1 root      20   0  1932  900  540 S    0  0.1   0:00.82 init                                                            
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd                                                        
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.08 migration/0                                                     
    4 root      15  -5     0    0    0 S    0  0.0   0:48.73 ksoftirqd/0                                                     
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0                                                      
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.08 migration/1                                                     
    7 root      15  -5     0    0    0 S    0  0.0   0:00.16 ksoftirqd/1                                                     
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1                                                      
    9 root      15  -5     0    0    0 S    0  0.0   0:00.34 events/0                                                        
   10 root      15  -5     0    0    0 S    0  0.0   0:00.40 events/1                                                        
   11 root      15  -5     0    0    0 S    0  0.0   0:00.00 khelper                                                         
   68 root      15  -5     0    0    0 S    0  0.0   0:00.28 kblockd/0                                                       
   69 root      15  -5     0    0    0 S    0  0.0   0:00.32 kblockd/1                                                       
   72 root      15  -5     0    0    0 S    0  0.0   0:00.00 kacpid                                                          
   73 root      15  -5     0    0    0 S    0  0.0   0:00.00 kacpi_notify                                                    
  157 root      15  -5     0    0    0 S    0  0.0   0:00.00 ata/0                                                           
jenny@jenny:~$ 

Right now the netbook is at 44C and is back to blue, but for a while there it went into the red, like 64C. I am calling Dell right now, been waiting for a long time.

---

### Post by w4ett on 2008-12-27
Well I have an Asus 701 4G model(with 32 Gb SSD installed)..when I ran Eeexubuntu (7.10)  I had sensor readings from the CPU @ 32C....I then tried EEEBuntu 8.04 (Array kernel) and it went to 48C...then I tried Eeebuntu 8.10 also with the array kernel with full Gnome desktop and it is running @ 50C.....guess which version I am running now!

---

### Post by greenleaves123 on 2008-12-27
I finally got through to Dell and I am sending the netbook to them for them to fix. Thanks for letting me know it is a hardware problem.

---

