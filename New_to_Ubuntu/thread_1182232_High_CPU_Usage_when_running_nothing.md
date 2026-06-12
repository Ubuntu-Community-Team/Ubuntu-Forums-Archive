---
title: "High CPU Usage when running nothing"
date: 2009-06-08
forum: New to Ubuntu
---

### Post by THEREQUI3M on 2009-06-08
I've been running Ubuntu for a while and everything works great, however yesturday when I turned on the pc my system monitor icon on my panel was reporting 98-100% usage all the time (even when I was running nothing!). It wasn't like this before and I'm starting to think maybe I have a virus or something. Does anyone know whats wrong?

---

### Post by Celauran on 2009-06-08
This is Linux. You don't have a virus. Have you taken a look at top to see what's eating your CPU cycles?

---

### Post by philinux on 2009-06-08
Have you got mozilla-acroread installed. i.e adobe reader plugin for firefox

---

### Post by THEREQUI3M on 2009-06-08
I don't have the Firefox plugin installed and I also can see whats eating up my memory. Here is all that I can see in top and a print screen of what is shown in the system monitor.
[INDENT][LEFT] top - 19:57:00 up  1:24,  2 users,  load average: 6.34, 5.31, 4.61
Tasks: 143 total,   3 running, 140 sleeping,   0 stopped,   0 zombie
Cpu(s): 77.6%us, 21.8%sy,  0.0%ni,  0.0%id,  0.0%wa,  0.3%hi,  0.3%si,  0.0%st
Mem:   1026668k total,   811020k used,   215648k free,    18568k buffers
Swap:  3004112k total,   230788k used,  2773324k free,   581108k cached
 
 3984 emmanuel  20   0 66696  13m 6348 S  2.0  1.3   1:49.53 compiz.real                                                     
19537 emmanuel  20   0     0    0    0 Z  1.3  0.0   0:00.04 vino-server <defunct>                                           
 3976 emmanuel  20   0 29924 5492 4676 S  1.0  0.5   0:38.06 gnome-settings-                                                 
 3985 emmanuel  20   0 48096  18m  10m S  1.0  1.8   0:38.91 gnome-panel                                                     
 4016 emmanuel  20   0 27984 5636 4852 S  1.0  0.5   0:30.95 python                                                          
 4375 emmanuel  20   0 16676 2168 1688 S  1.0  0.2   0:37.04 gnome-screensav                                                 
 3435 emmanuel  20   0 65492  18m  13m S  0.7  1.9   0:04.63 knotify4                                                        
 4057 emmanuel  20   0 27756 9668 6656 S  0.7  0.9   0:25.03 indicator-apple                                                 
19538 emmanuel  20   0 22456 6204 4816 R  0.7  0.6   0:00.02 vino-server                                                     
 2733 emmanuel  20   0 69704  17m  12m S  0.3  1.7   0:03.36 kded4                                                           
 3037 root      20   0 98712 1060  900 S  0.3  0.1   0:01.00 avgtcpd                                                         
 3345 root      20   0  5180 1004  916 S  0.3  0.1   0:01.43 hald-addon-stor                                                 
 4012 emmanuel  20   0 33016  11m 6444 S  0.3  1.2   0:06.05 update-notifier                                                 
 4018 emmanuel  20   0 26776 8952 5784 S  0.3  0.9   0:07.22 nm-applet                                                       
 2729 emmanuel  20   0 36412 9808 8484 S  0.3  1.0   0:02.17 klauncher                                                       
 2733 emmanuel  20   0 69704  17m  12m S  0.3  1.7   0:03.35 kded4                                                           
 4016 emmanuel  20   0 27984 5636 4852 S  0.3  0.5   0:30.92 python                                                          
 4025 emmanuel  20   0 91628  13m 8212 S  0.3  1.4   0:12.33 pidgin                                                          
 4026 emmanuel  20   0 16660 5060 4776 S  0.3  0.5   0:05.33 bluetooth-apple                                                 
 4032 emmanuel  20   0 25852 4712 4132 S  0.3  0.5   0:08.81 gnome-power-man                                                 
 4051 emmanuel  20   0 27644 9840 7196 S  0.3  1.0   0:09.61 fast-user-switc                                                 
 4148 emmanuel  20   0 20804 8296 6384 S  0.3  0.8   0:05.91 gtk-window-deco                                                 
29926 emmanuel  20   0 26264  11m 7672 S  0.3  1.2   0:02.51 multiload-apple                                                 
    1 root      20   0  3084  528  472 S  0.0  0.1   0:01.12 init                                                            
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd                                                        
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0                                                     
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.07 ksoftirqd/0                                                     
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0                                                      
    6 root      15  -5     0    0    0 S  0.0  0.0   0:00.04 events/0                                                        
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khelper                                                         
    8 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 kstop/0                                                         
    9 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kintegrityd/0                                                   
   10 root      15  -5     0    0    0 S  0.0  0.0   0:00.12 kblockd/0[/LEFT]
[/INDENT]

---

### Post by Anzan on 2009-06-08
I cannot see it in your top (I use htop) but gnome-appearance-properties and sometimes seahorse-agent can get bunched up and eat my CPU. You can just kill the former, the latter can require not just logging out but (egad) a reboot.

---

### Post by THEREQUI3M on 2009-06-08
No dice. I even searched through top, my system processes in system manager, and htop; If I add up all the process' cpu usage its only about 15%. I have no idea why all three programs are reporting a cpu usage of around 100%. (restarting didn't work either)

---

### Post by lovinglinux on 2009-06-08
I'm almost sure it is the remote desktop.

Go to "System >>> Preferences >>> Startup Applications (aka Session) " and untick "Remote Desktop" then restart.

---

### Post by THEREQUI3M on 2009-06-08
> **lovinglinux said:**
> I'm almost sure it is the remote desktop.

Go to "System >>> Preferences >>> Startup Applications (aka Session) " and untick "Remote Desktop" then restart.
Yes! It works... thanks man you are awsome :D

---

### Post by lovinglinux on 2009-06-08
> **THEREQUI3M said:**
> Yes! It works... thanks man you are awsome :D

You are welcome, but actually I took the idea from [http://ubuntuforums.org/showthread.php?t=1175009](http://ubuntuforums.org/showthread.php?t=1175009) :) 

I thought this might be your problem too, due to the defunct vino-server on your top output.

---

