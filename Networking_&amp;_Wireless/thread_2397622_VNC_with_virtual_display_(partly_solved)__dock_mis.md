---
title: "VNC with virtual display (partly solved) / dock missing"
date: 2018-08-01
forum: Networking &amp; Wireless
---

### Post by steeflemmens on 2018-08-01
Hello

I have a Ubuntu machine that I use as a Plex and data server. There is no monitor connected to it. This wasn't a problem with Ubuntu 16.04, but now, with 18.04, it is and it shows a black screen whenever I connect using VNC.

I've already created the virtual display using the answer to this question: [https://unix.stackexchange.com/questions/378373/add-virtual-output-to-xorg](https://unix.stackexchange.com/questions/378373/add-virtual-output-to-xorg)

Then I made a script that's executed bij Startup Applications:

#! /bin/bash

/usr/bin/xrandr -d :0 --output VIRTUAL1 --primary --auto
/usr/bin/xrandr --newmode "1600x900_60.00"  118.25  1600 1696 1856 2112  900$
/usr/bin/xrandr --addmode VIRTUAL1 "1600x900_60.00"

After this, it still shows a black screen when I connect using VNC. BUT, when I run this with SSH:

$ export DISPLAY=:0
$ xrandr

After that, I can see my desktop in VNC... Any ideas on how to fix this? Also, when I see my desktop after all this, the dock is missing and all the icons are in the same spot.

[EDIT]
Adding the line "/usr/bin/xrandr" at the end of my script made sure that VIRTUAL1 is active at reboot. 

Dock is still missing though.

---

### Post by HermanAB on 2018-08-01
Note that VNC is mostly a Windows thing.  If your local machine is a Linux machine and you are connecting to a remote Linux machine, then there is not much point in using VNC.  

Rather use SSH and run the programs that you want to run remotely, transparently on your local desktop.  SSH is secure, while VNC is a very reliable way to get a machine hacked and serving spam.

---

### Post by steeflemmens on 2018-08-01
Thanks for your answer!

I'm using VNC (vino) so I can connect to my server using my tablet and iPad over vnc and remmina on my laptop.

---

### Post by slickymaster on 2018-08-01
*Thread moved to **Networking & Wireless**.*

---

### Post by steeflemmens on 2018-08-06
This is how I solved it:

I've created the virtual display using the answer to this question: [https://unix.stackexchange.com/questions/378373/add-virtual-output-to-xorg](https://unix.stackexchange.com/questions/378373/add-virtual-output-to-xorg)

Create a 20-intel.conf file:
  
sudo vi /usr/share/X11/xorg.conf.d/20-intel.conf
  
Add the following configuration information into the file:
  
```
Section "Device"
    Identifier "intelgpu0"
    Driver "intel"
    Option "VirtualHeads" "2"
EndSection
```
  
This tells the Intel GPU to create 2 virtual displays. You can change the number of VirtualHeads to your needs.



Then I made a shell script (don't forget to set executable) and put that in Startup Applications:

    ```
#! /bin/bash
    
/usr/bin/xrandr -d :0 --output VIRTUAL1 --primary --auto
/usr/bin/xrandr --newmode "1600x900_60.00" 118.25 1600 1696 1856 2112 900$
/usr/bin/xrandr --addmode VIRTUAL1 "1600x900_60.00"
/usr/bin/xrandr

```
That way, VIRTUAL1 is set as output and connected. At boot, a new mode (found using "cvt 1600 900") is being created and appointed to VIRTUAL1. 

Only issue with this is: dock is missing at reboot... Haven't solved that yet.

---

