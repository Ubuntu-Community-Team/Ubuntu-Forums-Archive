---
title: "I figured out a fix for nvidia driver issues"
date: 2008-12-30
forum: New to Ubuntu
---

### Post by quadcam on 2008-12-30
after trying to install drivers for my Nvidia card and having fail after fail, I found a working solution

#1 go to [http://www.nvidia.com/object/linux_display_ia32_180.06.html](http://www.nvidia.com/object/linux_display_ia32_180.06.html)
and download driver 180.06 to your desktop

#2 shutdown xserver by pressing ctrl+alt+f2
enter login and password 
then sudo /etc/init.d/gdm stop

#3 use the command sudo sh NVIDIA-Linux-x86-180.06-pkg1.run

that will start the nvidia driver install..it may as if you want nvidia to search for a display kernel and if you say yes it will respond with not found and ask if you would like it to complie one..just hit yes..a few moments later when it finishes you're new driver will be ready to go

exit the install and restart x by typing 
sudo /etc/init.d/gdm start

I couldnt find a fix so i just decided to give that a shot and it works great

---

### Post by sprinj76 on 2008-12-30
I may try this since I can't seem to get my system working again. Thanks for taking the time to type it out!

---

### Post by quadcam on 2008-12-30
no problem, i'm just really happy something worked

---

### Post by steveneddy on 2008-12-30
I thought that is what the Envy script does.

---

### Post by waltkerr on 2008-12-30
Thanks for your instructions; this came closer than anything else to helping me with the same problem. I made it all the way to the point of building the new kernel then it crashed with message "Unable to build NVIDIA kernel module." I checked the log file and it contains only a large number (big help!). Anyway, I now know how to start and stop the GDM and do some command line stuff so it was instructive. I'll keep plugging away. I post this only in case someone else had the same result I did, maybe we can collaborate on the next step. Thanks again.

---

### Post by quadcam on 2008-12-31
> **steveneddy said:**
> I thought that is what the Envy script does.

could be, I just installed ubuntu yesterday so i dont know what envy is or what it does

---

### Post by fooman on 2008-12-31
> **waltkerr said:**
> Thanks for your instructions; this came closer than anything else to helping me with the same problem. I made it all the way to the point of building the new kernel then it crashed with message "Unable to build NVIDIA kernel module." ....

open a terminal and run the following command before trying the instructions above:
```
sudo apt-get install build-essential linux-headers-`uname -r`
```

then try installing the drivers.

---

### Post by anewguy on 2008-12-31
envy, or in particular envyng for 8.04 and 8.10, will automatically install the driver for your nvidia or ati video card.  It doesn't work with all, but if you downloaded that driver that is the same one that envyng would have.  Envyng gets everything needed, compiles and installs the driver, and sets up your xorg configuration so everything should work.  It is in synaptic package manager.  Takes all the headaches out of what you are trying to do.

Dave

---

### Post by cb34 on 2008-12-31
> **quadcam said:**
> after trying to install drivers for my Nvidia card and having fail after fail, I found a working solution

#1 go to [http://www.nvidia.com/object/linux_display_ia32_180.06.html](http://www.nvidia.com/object/linux_display_ia32_180.06.html)
and download driver 180.06 to your desktop

#2 shutdown xserver by pressing ctrl+alt+f2
enter login and password 
then sudo /etc/init.d/gdm stop

#3 use the command sudo sh NVIDIA-Linux-x86-180.06-pkg1.run

that will start the nvidia driver install..it may as if you want nvidia to search for a display kernel and if you say yes it will respond with not found and ask if you would like it to complie one..just hit yes..a few moments later when it finishes you're new driver will be ready to go

exit the install and restart x by typing 
sudo /etc/init.d/gdm start

I couldnt find a fix so i just decided to give that a shot and it works great
this is exactly what works for me. good post! the way it's done.

the only thing i do different is after stopping gdm, i first purge all nvidia related stuff off the machine, including jockey*, then do exactly as above.

---

### Post by waltkerr on 2008-12-31
Thanks quadcam and fooman but I'm still stuck. I still get the message "Unable to build NVIDIA kernel module" after the driver download and unpack. I've also tried envyng which seems to complete OK but once I restart GDM, everything is sluggish and usually crashes after about a minute or so. Using the Hardware Driver detect and activate also leaves me with a system that is unstable. The best I've been able to do is a 800x600 resolution after the initial install of Ubuntu. I'm getting tired of re-installing.

---

### Post by quadcam on 2008-12-31
I'm not sure if this will work but maybe you can reset the gui

sudo dpkg-reconfigure xserver-xorg

and then try to install the driver the way I posted above. I never could get Nvidia 177 driver to work so i dont think it was installed when i tried to do the ver180.06 install, maybe thats causing the problem with the kernel complile

---

### Post by pushin50 on 2008-12-31
> **cb34 said:**
> this is exactly what works for me. good post! the way it's done.

the only thing i do different is after stopping gdm, i first purge all nvidia related stuff off the machine, including jockey*, then do exactly as above.

Thanks All. This looks like the right fix but I just cannot make it go.

First question - how do you "purge all nvidia-related stuff off the machnie including jockey"?

Second question - the response to my use of the sudo apt-get install build-essential linux-headers-'uname -r' commend is this:

dad@daddad-desktop:~$ sudo apt-get install build-essential linux-headers-'uname -r' 
[sudo] password for dad: 
Reading package lists... Done 
Building dependency tree       
Reading state information... Done 
build-essential is already the newest version. 
E: Couldn't find package linux-headers-uname -r

Any idea what's up there?

Have a copy of the /var/log/nvidia-installer.log file if anyone wants to see. Lots of messages about arithmetic pointing to "void" and, also, inability to create temp files.

Any help deeply appreciated - been struggling for a week now.

---

### Post by fooman on 2008-12-31
> **pushin50 said:**
> Thanks All. This looks like the right fix but I just cannot make it go.

First question - how do you "purge all nvidia-related stuff off the machnie including jockey"?

Second question - the response to my use of the sudo apt-get install build-essential linux-headers-'uname -r' commend is this:

dad@daddad-desktop:~$ sudo apt-get install build-essential linux-headers-'uname -r' 
[sudo] password for dad: 
Reading package lists... Done 
Building dependency tree       
Reading state information... Done 
build-essential is already the newest version. 
E: Couldn't find package linux-headers-uname -r

Any idea what's up there?


that command is not typed correctly ('uname -r' should be: `uname -r`) ...try copying and then pasting the following into a terminal:

```
sudo apt-get install build-essential linux-headers-`uname -r`
```good luck.

---

### Post by pushin50 on 2008-12-31
Done. Thanks. Working it again.

---

### Post by waltkerr on 2009-01-12
This was somewhat solved by the installation of a new graphics card (NVIDIA GeForce 6200) and a full install of Ubuntu. At least Ubuntu is finally out of "low graphics mode" and I'm able to get the resolution up higher than 800x600 using the "default" graphics driver. I cannot enable any of the 2D or 3D desktop stuff, however. I've tried multiple times to install every other NVIDIA driver out there but all fail.

---

