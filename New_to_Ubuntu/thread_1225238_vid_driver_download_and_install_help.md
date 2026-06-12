---
title: "vid driver download and install help"
date: 2009-07-28
forum: New to Ubuntu
---

### Post by pleasantashes on 2009-07-28
downloaded my vid driver.

instructions say

Type "sh NVIDIA-Linux-x86-185.18.14-pkg1.run" to install the driver.

where do i type this?
tried terminal and got

sh: Can't open NVIDIA-Linux-x86-185.18.14-pkg1.run

---

### Post by halitech on 2009-07-28
where did you download the file to? you need to cd to the correct directory and then run the command

---

### Post by pleasantashes on 2009-07-28
> **halitech said:**
> where did you download the file to?
my desktop

day 1
thread 2
post 2

---

### Post by halitech on 2009-07-28
ok, in the terminal type cd Desktop (Linux is case sensative so desktop is not the same as Desktop) then try running the command again

---

### Post by pleasantashes on 2009-07-28
> **halitech said:**
> ok, in the terminal type cd Desktop (Linux is case sensative so desktop is not the same as Desktop) then try running the command again

this started working and then the installer popped up saying

  ERROR: nvidia-installer must be run as root

how do i run it as root

---

### Post by ayenack on 2009-07-28
If the NVidia install is still the same as it used to be this won't work. You'll have to press ctrl_alt_F4 then log in at the command prompt and run the command again like this. Before you do this pleases back up your xorg.conf like this in Ubuntu 8.04. May not work in Jaunty.

**sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup**

If you need to restore do this.

[B]sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf
[/B]
Then to install the driver do this.

**cd ~/Desktop**

Then:-

**sudo sh NVIDIA-Linux-x86-185.18.14-pkg1.run**

Then when done type:-

**sudo reboot**

BTW.
Have you tried the restricted driver. System_Administration_Hardware Drivers

---

### Post by pleasantashes on 2009-07-28
> **ayenack said:**
> 

Then:-

**sudo sh NVIDIA-Linux-x86-185.18.14-pkg1.run**



closer.

got another error

ERROR: You appear to be running an X server; please exit X before installing.

whats an x server and how do i exit it

---

### Post by ayenack on 2009-07-28
Did you press ctrl+alt+F4?

Wait a minute just remembered. You'll need to type this to stop GDM.

**sudo /etc/init.d/gdm stop**

Then do the install.

---

### Post by halitech on 2009-07-28
the X server is what gives you the desktop

press ctrl+alt+F4 (as ayenack says) and log in, then run
```
sudo /etc/init.d/gdm stop
```
then run the installer again

---

### Post by ayenack on 2009-07-28
As halitech says the X Server is what your display drivers use to give you the desktop GUI. GDM stands for Gnome Display Manager.

---

### Post by pleasantashes on 2009-07-28
got it.

thanks!!!!    


:popcorn:

---

### Post by ayenack on 2009-07-28
Cool. Mark thread as solved so others can benefit form your experience.

---

