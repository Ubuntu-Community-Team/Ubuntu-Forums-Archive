---
title: "CPU usage really high with no running process"
date: 2008-12-15
forum: New to Ubuntu
---

### Post by dman535 on 2008-12-15
When I view system resources  tab in the system monitor my CPU is showing between 50% and 80% - spikes to 100 with no significant applications running. When I go to the process tab I see gnome system monitor at 5% and an occasional xorg at 20% - but nothing to indicate a process that is maxing out the CPU. I do notice that this O/S seems to run slower than XP did on my laptop (Dell D600)

Any ideas on what is wrong?

Thanks

Derek.-

---

### Post by howefield on 2008-12-15
run the top command in a terminal, might give you some clues.

---

### Post by Michael.Godawski on 2008-12-15
hi dman535, 

pls run top as suggested above.
You are not alone with this high cpu usage behavior, as it seems:
[http://ubuntuforums.org/showthread.php?t=804201](http://ubuntuforums.org/showthread.php?t=804201)

This might be related to your graphic card. Please post the output from
```
sudo lshw -C display
```

---

### Post by dman535 on 2008-12-15
> **howefield said:**
> run the top command in a terminal, might give you some clues.

top - 09:12:27 up  1:43,  2 users,  load average: 0.71, 0.54, 0.47
Tasks: 120 total,   2 running, 118 sleeping,   0 stopped,   0 zombie
Cpu(s): 41.2%us,  3.7%sy,  0.0%ni, 54.8%id,  0.0%wa,  0.3%hi,  0.0%si,  0.0%st
Mem:   1033308k total,   866676k used,   166632k free,    56516k buffers
Swap:  1646620k total,        0k used,  1646620k free,   379532k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 4894 root      20   0  219m 116m  14m R 29.9 11.5  13:39.44 Xorg               
 9396 derek     20   0  250m 116m  26m S 12.6 11.5   2:18.02 firefox            
 5309 derek     20   0 22172  14m 5980 S  1.3  1.4   0:40.08 compiz.real        
 5648 derek     20   0 59692  35m  17m S  0.7  3.5   0:23.40 pidgin             
10628 derek     20   0 97728  22m  12m S  0.7  2.2   0:00.82 gnome-terminal     
10652 derek     20   0  2416 1152  884 R  0.7  0.1   0:00.28 top                
    1 root      20   0  3056 1888  564 S  0.0  0.2   0:01.64 init

---

### Post by sdennie on 2008-12-15
My guess is the thing that is causing the very high CPU usage is the gnome-system-monitor itself.  This has been a bug since the new system monitor was introduced in Hardy and the larger the system monitor window, the more CPU it will use.  As suggested above, use top or htop in a terminal instead of gnome-system-monitor to get more accurate CPU usage.

---

### Post by dman535 on 2008-12-15
> **Michael.Godawski said:**
> hi dman535, 

pls run top as suggested above.
You are not alone with this high cpu usage behavior, as it seems:
[http://ubuntuforums.org/showthread.php?t=804201](http://ubuntuforums.org/showthread.php?t=804201)

This might be related to your graphic card. Please post the output from
```
sudo lshw -C display
```

  *-display UNCLAIMED     
       description: VGA compatible controller
       product: Radeon RV250 [Mobility FireGL 9000]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 32 bits
       clock: 66MHz
       capabilities: agp agp-2.0 pm bus_master vga_palette cap_list
       configuration: latency=32 mingnt=8

---

### Post by Michael.Godawski on 2008-12-15
vor so true :neutral:
[https://bugs.launchpad.net/ubuntu/+source/gnome-system-monitor/+bug/187383](https://bugs.launchpad.net/ubuntu/+source/gnome-system-monitor/+bug/187383)

---

### Post by dman535 on 2008-12-15
I do notice that when things like the root password prompt comes up and the whole display is greyed out - it seems like the machine struggles. Should I be doing something different with the display driver?

D.-

---

### Post by tkawa6 on 2008-12-15
> 4894 root 20 0 219m 116m 14m R 29.9 11.5 13:39.44 Xorg 
9396 derek 20 0 250m 116m 26m S 12.6 11.5 2:18.02 firefox 
5309 derek 20 0 22172 14m 5980 S 1.3 1.4 0:40.08 compiz.real

I think compiz and desktop effects is what's causing xorg to eat up your system recourses. I have the same laptop and the same issues until I  switched off desktop effects and stayed away from compiz. My xorg CPU usage went from averaging on the 30%-60% (when watching videos) to 2.5%-20%.

---

