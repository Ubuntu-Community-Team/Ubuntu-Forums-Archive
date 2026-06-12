---
title: "[SOLVED] updates and version conflicts"
date: 2009-01-07
forum: New to Ubuntu
---

### Post by maddragon on 2009-01-07
hi im very new to linux and ubunto so things are stil new to me things been goin pretty well from start until i started updating nvidia drivers for graphics and kernel and so on.

the updates has come automaticaly through ubuntos update manager and hardware 

the problem im having is that the latest drivers dosn match in kernel and the common the graphic version is 177.82 and for some weird reason the lernel is only 177.80

is that a mistake or whas it intensional to make the versions difrent ? as i can understand that both cant work if the versions dosn match with my real problem comes in i cant use wine any more :(

as im quit new at this os can one help me to fix this or do i realy have to reinstall ubuntu and then never update nvidia drivers again ?

is there a fix for this ?

Maddragon
regards

---

### Post by Elfy on 2009-01-07
I have nvidia-177-kernel-source and nvidia-glx-177 both at .82

Did the updates come from the update manager?

Check in your software sources - System > Admin menu that you don't have proposed and backports enabled in the update tab.

Maybe try a 

```
sudo apt-get update
sudo apt-get upgrade
```

See if it gives you any new updates.

---

### Post by maddragon on 2009-01-07
yah they did 

hwo ever i did one mistake as the hardware drivers suggested 3 versios 173,xx,177

i choose 173 in the start then cancled it then choose 177 im not sure if that screwed up a few things

but else yah they came from teh update manager


i tryed u suggestion dosn help 

it only dos the same it usaly dos checks and finds no update

heres what it says in teh console :

fixme:win:EnumDisplayDevicesW ((null),0,0x39edbc,0x00000000), stub!
Error: API mismatch: the NVIDIA kernel module has version 177.80,
but this NVIDIA driver component has version 177.82.  Please make
sure that the kernel module and all NVIDIA driver components
have the same version.



Mad
regards

---

### Post by Elfy on 2009-01-07
Ok can you open a terminal and run this please, paste the output for me. 

```
apt-cache madison nvidia-177-kernel-source &&apt-cache madison nvidia-glx-177
```

---

### Post by maddragon on 2009-01-07
sure can 

heres the output :

nvidia-177-kernel-source | 177.82-0ubuntu0.1 | [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) intrepid-updates/restricted Packages
nvidia-177-kernel-source | 177.80-0ubuntu2 | [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) intrepid/restricted Packages
nvidia-graphics-drivers-177 | 177.80-0ubuntu2 | [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) intrepid/restricted Sources
nvidia-graphics-drivers-177 | 177.82-0ubuntu0.1 | [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) intrepid-updates/restricted Sources
nvidia-glx-177 | 177.82-0ubuntu0.1 | [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) intrepid-updates/restricted Packages
nvidia-glx-177 | 177.80-0ubuntu2 | [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) intrepid/restricted Packages
nvidia-graphics-drivers-177 | 177.80-0ubuntu2 | [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) intrepid/restricted Sources
nvidia-graphics-drivers-177 | 177.82-0ubuntu0.1 | [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) intrepid-updates/restricted Sources

it looks to me it has the packages just not updated the kernel :S

mad 
Regards

---

### Post by Elfy on 2009-01-07
Open synaptic - search for 177 and install whichever the right version of whichever package still shows as .80

If that fails to work then as I don't know if you've changed your xorg at all so back it up first.

```
sudo cp /etcX11/xorg.conf /etc/X11/xorg.conf.0701
```

Open Hardware Drivers - disable the 177 driver. Once it's finished, check xorg - it will say it needs to restart, don't do that yet.

```
cat /etc/X11/xorg.conf
```

It should be a basic file now - the driver section shouldn't look like

> Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"

Reboot now and it will start without the nvidia driver.

If however xorg.conf does show a nvidia driver, reboot into recovery mode and then from the root menu

xfix
resume

Go back to Hardware Drivers and re-enable the suggested driver - it should use the most recent ones

---

### Post by maddragon on 2009-01-07
hi mate k i bet it was teh mistake i made with choosing the 173 first then cancel in the midle 

your solution to remove the drive totaly and then reboot reinstall it worked and solved it

i wont make that mistake again lol

thanks lot for taking the time to help 


Mad 

regards

---

### Post by Elfy on 2009-01-07
Excellent - can you mark thread solved please.

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

