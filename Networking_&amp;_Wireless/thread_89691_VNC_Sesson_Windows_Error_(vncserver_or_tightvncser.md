---
title: "VNC Sesson Windows Error (vncserver or tightvncserver)"
date: 2005-11-13
forum: Networking &amp; Wireless
---

### Post by SadaraX on 2005-11-13
Hello. I'm using Ubuntu/Kubuntu 5.10. When I start a vnc session on window 9, now a lot of the time the window-borders and buttons do not show up. The programs will still start, but the window-management does not seem to work. 

UPDATE: Also, the windows do not show up on the task bar. 

The same problem happens when I use tightvncserver or vnc4server

> 
Motherboard: EPOX EP-9NPA+Ultra NF4 ULTRA RT

Video Card: Geforce 6800GT 256MB DDR PCI Express x16 Video Card - ASUS EN6800/ TD/256
Type VGA XFX|
Model PVT45GUDF3

Sound: Built-in Sound on EPOX board - NVidia CK084

CPU: AMD Athlon 64 X2 4200+ Manchester 2000MHz FSB Socket 939 Dual Core
Processor Model ADA4200BVBOX

RAM: CORSAIR XMS 1GB 184-Pin DDR SDRAM DDR 400 (PC 3200) Unbuffered System
Memory Model CMX1024-3200C2PT
Model #:CMX1024-3200C2PT

Kernel: 2.6.12-9-686-smp

Distro: Ubuntu/Kubuntu 5.10, KDE 3.4.3.


---

### Post by SadaraX on 2006-06-27
I solved this problem by changing my ~/.vnc/xstartup file. Normally, most tutorials tell you to replace the line: 

  x-window-manager &

with your favorite windows-manager, like for KDE you would use 

  startkde &

However, I found that for some reason KDE does not always start the windows management properly. To solve this problem, do NOT remove the line "x-window-manager &", instead add right after it "startkde &"

Thus your xstartup file should look something like this:

```

#!/bin/sh

xrdb $HOME/.Xresources
xsetroot -solid grey
x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
x-window-manager &
startkde &

```

This should solve any problems you might be having with windows management.

---

