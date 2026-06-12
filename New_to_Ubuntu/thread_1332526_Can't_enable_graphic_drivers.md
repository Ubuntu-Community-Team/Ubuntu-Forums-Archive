---
title: "Can't enable graphic drivers"
date: 2009-11-20
forum: New to Ubuntu
---

### Post by Kenta92 on 2009-11-20
After updating my distro to Karmic Koala, i have problems with the graphic drivers.
I have two drivers installed but none is enabled, so i tried from desktop the first time with no results, i restarted and then i couldn't start the graphic mode anymore.
So i started the recovery mode and tried some commands that i found, with no positive results. It seems that i can't enable the drivers, i don't know why, but in both graphic and recovery mode when i ask to enable the driver, nothing happens.

---

### Post by wrgb2 on 2009-11-20
Login in text mode from recovery mode and try the following:

sudo dpkg-reconfigure xserver-xorg

then 

sudo /etc/init.d/gdm start  

to start the X-server again.  That at least should get you back in graphical mode and then you can try adding your drivers back.

---

### Post by Kenta92 on 2009-11-20
when i do the first command it says:
dpkg conflicting actions -e (--control) and -r (remove)
type dpkg --help for..............and so on.

What to do?

---

### Post by falconindy on 2009-11-20
the dpkg --reconfigure trick isn't valid in 9.10. Before you go about changing xorg.conf, what video card are you using? As a temporary measure, you could rename xorg.conf so that it doesn't get used on boot and see if that lets you get into the GUI.

---

### Post by Kenta92 on 2009-11-20
nVidia GeForce FX 5200.
I can't start the graphic mode and i'm a total n00b in Ubuntu, so everything i have to do i need to know how..

---

### Post by falconindy on 2009-11-20
From the terminal do this:
```
sudo apt-get install nvidia-graphics-drivers-173
nvidia-xconfig
sudo reboot
```
Should do the trick.

---

### Post by realzippy on 2009-11-20
> **falconindy said:**
> the dpkg --reconfigure trick isn't valid in 9.10. 

is it possible that it still works when upgraded from jaunty?

---

### Post by realzippy on 2009-11-20
For "total noob" there is a script,what could do this: envy.
Can you open terminal and type:

**sudo apt-get install envyng-core**

if done so,envy can be found in menue/systemtools
edit: or started by *sudo envyng -t* from terminal
rest is selfexplaining...
feel free to ask...

---

### Post by Kenta92 on 2009-11-20
i installed the drivers, but nothing happened when i did nvidia-xconfig

it seems not to work (dpgk-reconfigure) even if upgraded from  jauntry..

is envy useful even in recovery mode?

---

### Post by realzippy on 2009-11-20
**sudo nvidia-xconfig** ?

---

### Post by realzippy on 2009-11-20
*is envy useful even in recovery mode?*

Never tried.Maybe you must start runlevel3.
Does it only boot in recovery mode?

**sudo envyng -t** starts envy in text mode.

---

### Post by Kenta92 on 2009-11-20
i can boot in graphic mode but then it freaks out and i can't do anything. So my only option is to enter recovery mode and try to fix the drivers..

---

### Post by realzippy on 2009-11-20
So install and test...(in recovery mode)

[B]sudo apt-get install envyng-core

sudo envyng -t[/B]

---

### Post by Kenta92 on 2009-11-20
it worked!! thank you very much!
So easy to use and so fast, in no time i got back my graphic mode!
I'll let you know if the problems it's not solved at the next reboot, but now it shows the driver as enabled so the problem seem solved.


Thank you all.

---

### Post by realzippy on 2009-11-20
Please mark thread as solved ([COLOR="Red"]threadtools[/COLOR])
if it works...

Edit:
And vote for the washingmachine...

---

