---
title: "Help installing NVIDIA driver"
date: 2009-02-18
forum: New to Ubuntu
---

### Post by DFord425 on 2009-02-18
I need help installing an NVIDIA driver. I need to exit X Window, how do i do this? And then again how would i restart it?

---

### Post by taurus on 2009-02-18
Have you looked in System -> Administration -> Hardware Drivers to see if your card is on the list and whether there is a nvidia driver for it?

---

### Post by DFord425 on 2009-02-18
Yes i checked. I have an NVIDIA GeForce 9 Series, and there is no driver listed in the Hardware Drivers list.

---

### Post by Shazaam on 2009-02-18
First things first...
You need build-essential, dkms and the kernel headers for Ubuntu-
```
sudo apt-get install build-essential dkms linux-headers-$(uname -r)
```

1. Make sure the nvidia driver is on your desktop.
2. Restart. When the grub boot screen starts hit your ESC key. The kernel/os screen shoud pop up. Choose "Recovery Mode"
3. It will boot to a list of actions, choose to drop to a command line interface (console). Log in.
4. Enter this...
```
sudo /etc/init.d/gdm stop
```
(stops the display manager)
5. cd (change directory) to the desktop...```
cd Desktop
```
(capitol D is mandatory)
6. Type in ls (el-es), this will list everything. If your nvidia driver is listed you are in the right place. If not try this...
```
cd /home/yourusername/Desktop
```
(where yourusername is your user name)
7. Enter this (use your driver name/numbers instead of mine)...
```
sudo sh NVIDIA-Linux-x86-180.22-pkg1.run
```
8. It will ask you about compiling a kernel module, answer yes to both questions.
9. It will ask you if you want to it configure X, answer yes.
10. It should finish without errors, enter...
```
sudo reboot
```

---

### Post by DFord425 on 2009-02-18
I tried that and when i enter the command > sudo /etc/init.d/gdm stop I get an error saying its not recongnized. I also replaced gdm with kde and its not recognized either. I then went on the acually installing the driver and it says that i was in some type of Level 1 and i should be in Level 3 and i it doesnt recomend that i install the driver so i did not. Can anyone give me some more info about either the Level 1 compared to Level 3 or the ```
sudo /etc/ini.d/gdm stop
```

---

### Post by SonicSteve on 2009-02-18
Whenever I re-install on my laptop I have trouble installing Nvidia drivers too. I find for those stubborn Nvidia cards envyNG from alberto milone always works.

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

It will likely have you up and running in a few minutes

---

### Post by DFord425 on 2009-02-20
I tried installing ENVY but i couldnt. I get this error:
```
dford@DMoney:~$ sudo apt-get install envyg-qt
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package envyg-qt
```

Here is my sources.list file for the universe repository:
```
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy universe
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe
```

Also when i run ```
sudo apt-get update
``` I get this error, could this be part of the problem?
```
Fetched 14.4kB in 1s (7977B/s)
Reading package lists... Done
W: GPG error: http://dl.google.com stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A040830F7FAC5991
W: GPG error: http://packages.medibuntu.org hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: You may want to run apt-get update to correct these problems

```

---

### Post by DFord425 on 2009-02-20
bump

---

### Post by DFord425 on 2009-02-21
anyone have any ideas??

---

### Post by 4Orbs on 2009-02-21
> I also replaced gdm with kde and its not recognized either
You should have replaced gdm with kdm, not kde. Post #4 should work for you, but first deactivate the driver you now have and uninstall it using Envy (if you still have the Envy driver version installed). If you're not using the Envy driver, then deactivate the driver from the Hardware Drivers manager and uninstall the driver using Synaptic Package Mgr (Complete Removal). Then follow the steps in Post #4 (substituting kdm) to compile and install the driver from nVidia website. Don't try to activate the driver after installing because its already activated, even though the Hardware Drivers Mgr says its not. You'll know it's activated if you see the green nVidia logo for a moment at bootup or login.

After installing and rebooting, you can go to the nVidia Settings Mgr and change your default resolution, which affects user accounts AND the login screen. Then each user can select their preferred resolution with xrandr.

Also, future kernel updates might force you to uninstall the driver and re-install after the update completes.

---

### Post by JerichoKru on 2009-02-21
> **DFord425 said:**
> I tried that and when i enter the command  I get an error saying its not recongnized. I also replaced gdm with kde and its not recognized either. I then went on the acually installing the driver and it says that i was in some type of Level 1 and i should be in Level 3 and i it doesnt recomend that i install the driver so i did not. Can anyone give me some more info about either the Level 1 compared to Level 3 or the ```
sudo /etc/ini.d/gdm stop
```

Have you tried:

```
su -
```
then
```
init 3
```

If it gives you an authentication failure, you probably need to set a password for the root.

I don't know where it is in KDE...but in Gnome it's:

System --> Administration --> Users and Groups


Then follow Shazaam's tut, replacing the ```
sudo /etc/init.d/gdm stop
``` with what I typed above.

---

### Post by DFord425 on 2009-02-21
I tried installing and during the process, it gave me the message > Unable to open /usr/lib/nvidia/libglx.so.xserver-xorg_core then it said it finished and when i reboot, i get this message > Cannot launch graphical configuration tool because displayconfig_gtk is not installed. ...must manually configure Xorg
What do i have to do to fix this? Has anyone had this problem before?

---

### Post by 4Orbs on 2009-02-21
You are using Kubuntu (KDE), and not Ubuntu (Gnome). Don't type gdm anything, because gdm works with gnome and not kde. Any reference to gdm should be changed to kdm. Don't know if this is the problem, but you need to understand the difference.

---

### Post by DFord425 on 2009-02-21
> **4Orbs said:**
> You are using Kubuntu (KDE), and not Ubuntu (Gnome). Don't type gdm anything, because gdm works with gnome and not kde. Any reference to gdm should be changed to kdm. Don't know if this is the problem, but you need to understand the difference.

No i have been using kdm the whole time. I tried gdm and found it didnt work, then figured it was for gnome

---

### Post by 4Orbs on 2009-02-21
Are you using Kubuntu on a wubi install, or a physical install on a real partition?

Looking back through the posts, I am wondering: Did you resolve the update that wasn't completed because of the medibuntu repository error? Is your desktop usable at this time although the driver isn't working?

I suggest before continuing you should go to the Multimedia & Video section of this forum and follow the Comprehensive Multimedia How-to all the way through, then update with Update Mgr. Then resume trying to install the driver from the nVidia website. That's assuming your desktop is sufficiently usable now.

---

### Post by DFord425 on 2009-02-21
I cant get to the desktop, all i can do is boot into recovery mode and get to the command line. There is an option of fix Xorg, i think, i could try that and then if that works i will take a look at what you mentioned, thanks

---

### Post by SonicSteve on 2009-02-22
from the command prompt you could try,

sudo dpkg-reconfigure xserver-xorg 

I believe that should still work even though xserver has been revamped.

---

### Post by AlCarmon on 2009-02-22
> **DFord425 said:**
> I need help installing an NVIDIA driver. I need to exit X Window, how do i do this? And then again how would i restart it?
Do yourself a favor and look at this post:

[http://ubuntuforums.org/showthread.php?p=5086971&](http://ubuntuforums.org/showthread.php?p=5086971&)

I have used it for both 8.04 and 8.10 with no problems.  IMHO step 13 is not really optional.
Al

---

