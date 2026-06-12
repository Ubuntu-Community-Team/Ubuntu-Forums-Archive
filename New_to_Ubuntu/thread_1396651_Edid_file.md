---
title: "Edid file"
date: 2010-02-02
forum: New to Ubuntu
---

### Post by agmath on 2010-02-02
I am dual booting with Window 7(64 bit) in my Vaio laptop VPCCW16FG.My laptop has NVIDIA® GeForce® GT 230M graphics processing unit with 512 Mb dedicated video memory.After successful installation of Ubuntu I installed Nvidia Accelerated Graphix Driver from update option.After that whenever I boot the machine the monitor becomes black and everything stops working
I need to extract Extract the EDID file from within windows 7 to solve the problem.I downloaded the software softmccs.After successful installation whenever I am clicking the Desktop icon,it is giving the message
"MCCS Test Utility has stopped working.A problem caused the program to stop working correctly,Window will close the program and notify you if a solution is available"

CAN ANYBODY TELL ME ANOTHER SOFTWARE TO EXTRACT THE EDID FILE FROM 
WINDOW 7(64 bit)?
Please help me and tell me how to extract EDID file using suitable software.

---

### Post by cariboo on 2010-02-03
Start Ubuntu in recovery mode, once at the menu, use the arrow keys to select drop to root prompt. Once at the prompt type:

```
nvidia-xconfig
```

this will create a new /etc/X11/xorg.conf file. Once the process has finished type:

```
exit
```

at the prompt, use the arrow keys to select resume, and you should be taken to your working desktop.

---

