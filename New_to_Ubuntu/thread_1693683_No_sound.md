---
title: "No sound"
date: 2011-02-23
forum: New to Ubuntu
---

### Post by legend_gibby on 2011-02-23
hay fokes....

ive managed to get my screen rev and video play back working so good news o that front...

so i now have the problem of no sound and the built i mic is still not working..... i tried to update the alsa driver to 1.0.23 but think i messed up the setting on the alsamixer too..

[http://www.linuxant.com/alsa-driver/downloads-ubuntu-x86.php](http://www.linuxant.com/alsa-driver/downloads-ubuntu-x86.php)

which of these setting should i pick for ubuntu netbook remix 10.10

this apears to be my only problem now!!

Spec is below

Processor Name
Intel Atom Z520
Operating System
MS Windows XP Home
Processor Speed
1.33 GHz
RAM
1 GB
Weight
3 lb
Screen Size
11.6 inches
Screen Size Type
widescreen
Graphics Card
Intel Graphics Media Accelerator 500
Storage Capacity (as Tested)
160 GB
Networking Options
802.11g
Primary Optical Drive
External

---

### Post by legend_gibby on 2011-02-23
i have just looked at this....

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

i have followed the instructions and to no joy with the mic....but i do have sound now!!

i followed part A but at the end i got this message

Setting up alsa-driver-linuxant (1.0.23.1-k2.6.31-17-generic-1) ...
No pre-built modules for the 2.6.35-25-generic kernel. Please use a generic package
or the right pre-compiled package for your kernel.
dpkg: error processing alsa-driver-linuxant (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 alsa-driver-linuxant
E: Sub-process /usr/bin/dpkg returned an error code (1)

then it says to run the command $ pulseaudio & pavucontrol

which i did then got this

[1] 2917
E: socket-server.c: bind(): Address already in use
E: module.c: Failed to load  module "module-esound-protocol-unix" (argument: ""): initialization failed.
E: main.c: Module load failed.
E: main.c: Failed to initialize daemon.

(pavucontrol:2918): Gtk-CRITICAL **: IA__gtk_main_quit: assertion `main_loops != NULL' failed
[1]+  Exit 1                  pulseaudio


Any help!!!
cheers

---

### Post by Aquila99 on 2011-02-23
Interesting ... I am having exactly the same sound problems with my new eeePC 1001PX running 10.10
Still playing trying to get sound working.
Can I ask what you did do to get the sound working, since you said the instructions that you followed failed.  I see that they are for 8.04 and 8.10, which I guess is a bit old by now and may not be valid.
Cheers,
Peter

---

