---
title: "Problem booting. System drops to a shell."
date: 2010-03-29
forum: New to Ubuntu
---

### Post by dablainester on 2010-03-29
Hello, I am a first time Linux user. I just finished installing Ubuntu 9.10 on a system I am attempting to make a server. The installation finished with no problems (as far as I could tell) and told me to reboot. When I rebooted the system, it brought me to a blank screen until I hit 'Enter'. It showed this message when I did:

Gave up waiting for root device. Common problems:
-Boot args (cat /proc/cmdline)
 -Check rootdelay= (did the system wait long enough?)
 -Check root= (did the system wait for the right device?)
-Missing modules (cat /proc/modules; ls /dev)
Alert! /dev/mapper/nvidia_ijcjecjf1 does not exist. Dropping to a shell.

I have tried the restart button a couple times on the system, with the same result. I tried the commands (cat /proc/cmdline; cat /proc/modules; ls /dev) and didn't see anything I knew what to do with. 

I'm not sure what to do. I hope someone here has some advice or can lead me to a solution. Thanks in advance. 

p.s. I have written down what comes up when I enter the cat /proc commands. The ls dev went off the screen.

---

### Post by readycarpenter on 2010-03-29
did you install ubuntu server edition? it has no desktop, you can add ubuntu desktop via terminal
```

sudo apt-get install ubuntu-desktop
```

---

### Post by dablainester on 2010-03-29
I don't believe so. I have gotten to a desktop screen before (when I was using the 'demo' to install the OS). So I assumed I was not using the Server edition. I could be mistaken though.

---

### Post by matt_mccarron on 2010-03-30
I have just had the same problem.  (except i'm not in a fresh install, i've been using 9.10 for months...)

I put ubuntu netbook remix on a usb drive and ran it, but I don't know how to view my hard drive to determine if it is still even there and all of my data...

Help!

---

