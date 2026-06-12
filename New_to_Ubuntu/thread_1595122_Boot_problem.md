---
title: "Boot problem"
date: 2010-10-12
forum: New to Ubuntu
---

### Post by bigal1932flying on 2010-10-12
Tried to upgrade from 10.04 to 10.10 using Synaptic package manager.
After some hours most of it seemed to be OK but it did not boot on Reboot.
What happens is that the normal black screen appears with "Starting up" in the top left corner, then a command line type screen appears which asks for my login and Password after I enter those a line appears saying:
"afrancis@afrancis-desktop:~$ " don't know what to do there.
If I press "Esc" during startup I am presented with a screen which says:
Ubuntu 10.10, kernel 2.6.35-22- generic
Ubuntu 10.10, kernel 2.6.35-22- generic (recovery mode)
Ubuntu 10.10, kernel 2.6.32-25- generic
Ubuntu 10.10, kernel 2.6.32-25- generic (recovery mode)
Ubuntu 10.10, kernel 2.6.28-16- generic
Ubuntu 10.10, kernel 2.6.28-16- generic (recovery mode)
Ubuntu 10.10, kernel 2.6.24-21- generic
Ubuntu 10.10, kernel 2.6.24-21- generic (recovery mode)
memtest86+ 
Please note that this is NOT a dual boot system, Ubuntu is the only system on this hard drive.

I have tried starting the 2.6.35-22 generic (recovery mode) it goes through downloading etc. but still does not fix the problem.
Can anyone help me to fix this problem? PLEASE!

---

### Post by JackNocturne on 2010-10-12
Hi Bigal,
It seems you boot into shell prompt [HTML]afrancis@afrancis-desktop:~$[/HTML] for some reason.

Try at the shell prompt to type ```
startx
``` to see if it brings up GUI.

---

### Post by bigal1932flying on 2010-10-13
Tried "startx"
Received the following:
(EE) Failed to load module "nvidia" (loader failed, 7)
(EE) No drivers available
Fatal server error.
no screens found.
giving up
xinit: No such file or directory (error 2): unable to connect to xserver
xinit: No such process (error 3): Server error.

---

### Post by bigal1932flying on 2010-10-13
Tried loading an Nvidia driver (not sure what I was doing or what I did) and now it seems to work. Booted in OK.
Thanks.

---

### Post by JackNocturne on 2010-10-13
Ok good it works now:)   Dont forget to mark thread as **solved**.

Cheers mate.

---

### Post by gatorbrit on 2010-10-13
> **bigal1932flying said:**
> Tried loading an Nvidia driver (not sure what I was doing or what I did) and now it seems to work. Booted in OK.
Thanks.


I think I have the same issue - how did you load the nvidia driver?

---

