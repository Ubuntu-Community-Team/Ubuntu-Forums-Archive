---
title: "python reboot"
date: 2010-03-20
forum: New to Ubuntu
---

### Post by Yitzach on 2010-03-20
I've taken to leaving my computer on for long periods of time under the assumption that Linux/Ubuntu doesn't have enough memory leaks to be a concern. As far as I can tell, that is true, but not for python. When I boot the computer, python is ~9% of RAM. This morning, after being on for 12 hours, python now takes up ~20% of RAM preventing me from running VirtualBox. My research indicates to me that python is an interpreter for programs written in Python. As such, a good many programs may depend on it. Is there a way to reload python without rebooting the computer and causing all oblivion to break loose?

---

### Post by n0dix on 2010-03-20
Strange do you ask for. I don't think exists this reboot of python on the fly. Many apps depends on it, usually graphics stuffs. How do you know python get that amount of memory ram?

---

### Post by asmoore82 on 2010-03-20
I'm currently up and running with Gnome/nautilus/calculator/Firefox/rhythmbox/terminals
and have very little python running, see exactly what's using python:
```
ps -eo pid,command | grep -i python
```

---

### Post by Yitzach on 2010-03-20
"top" told me the percent of RAM committed to python.

```
user@User~$ top

top - 19:37:35 up  9:36,  2 users,  load average: 0.90, 0.29, 0.22
Tasks: 172 total,   5 running, 167 sleeping,   0 stopped,   0 zombie
Cpu(s): 10.1%us, 51.7%sy,  0.2%ni, 38.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   1925496k total,  1909996k used,    15500k free,     6512k buffers
Swap:  4803392k total,    29496k used,  4773896k free,   419516k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND              
 4860 user      20   0 1116m 577m  51m S   99 30.7   0:54.66 VirtualBox           
 2410 user      20   0  621m 306m  10m R    8 16.3  59:22.62 python               
 2757 user      20   0 1051m 151m  36m R    7  8.0  47:28.77 firefox              
 2035 root      20   0  166m  65m 9.9m R    4  3.5  48:42.33 Xorg                 
 2224 user      20   0  265m  11m  10m S    4  0.6  14:49.76 pulseaudio           
   52 root      15  -5     0    0    0 S    0  0.0   0:19.35 scsi_eh_4            
 1042 root      20   0 22180 1144 1028 S    0  0.1   0:09.85 hald-addon-stor      
 4839 user      20   0  203m 8108 4796 S    0  0.4   0:00.81 VBoxSVC              
    1 root      20   0 19452 1440 1088 S    0  0.1   0:00.76 init                 
.
.
.
user@User:~$ ps -eo pid,command | grep -1 python
 2298 gnome-volume-control-applet
 2300 python /usr/share/system-config-printer/applet.py
 2305 update-notifier --startup-delay=60
--
 2358 /usr/lib/indicator-applet/indicator-applet --oaf-activate-iid=OAFIID:GNOME_IndicatorApplet_Factory --oaf-ior-fd=23
 2410 python /usr/lib/gdesklets/gdesklets-daemon --no-tray-icon
 2432 /usr/lib/gvfs/gvfsd-burn --spawner :1.9 /org/gtk/gvfs/exec_spaw/1
--
 4890 ps -eo pid,command
 4891 grep --color=auto -1 python

```

---

