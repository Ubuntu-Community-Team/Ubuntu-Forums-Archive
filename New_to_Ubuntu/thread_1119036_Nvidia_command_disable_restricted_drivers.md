---
title: "Nvidia command disable restricted drivers"
date: 2009-04-07
forum: New to Ubuntu
---

### Post by graynavigation on 2009-04-07
I dual boot Vista with Jaunty 9.04 64bit
Sony z540 notebook with switchable GPU: NVIDIA GeForce 9300M GS GPU and Mobile Intel Graphics Media Accelerator 4500MHD

Installed Jaunty without any issues. Activated the recommended restricted drivers and restarted ubuntu. Now instead of loading the GUI, I only have a command-line (terminal?). While looking for a fix I tried:

sudo dpkg-reconfigure -phigh xserver-xorg

sudo apt-get remove nvidia-glx

Neither worked.

I found a possible fix but it involved changing my vista to XP and wasn't guaranteed. Links to it below

[http://blog.shiftreduce.org/?p=13](http://blog.shiftreduce.org/?p=13)
[http://www.nvnews.net/vbulletin/showthread.php?t=120810&page=4](http://www.nvnews.net/vbulletin/showthread.php?t=120810&page=4)

If anyone has a better solution or advice, it would be appreciated. 
But, at this point I'm willing to sacrifice not having the restricted drivers for a working Jaunty again. I don't want to lose my files so I ask is there a command that would disable the restricted drivers?

Thanks for any help.

---

### Post by Clay_Banger on 2009-04-07
```
sudo aptitude purge nvidia-glx-xxx
```
should completely remove the drivers, replacing xxx with the version that is installed on your computer, (either 180,177 or 173)
then you should be able to properly reset everything with:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
if that doesnt work, u could try using the nvidia drivers from their website instead.

and you say that you can switch between the cards, correct? maybe, as to not to confuse ubuntu, make sure that you only ever have the one card selected while running it?

---

### Post by Gen2ly on 2009-04-07
Having both drivers on your system shouldn't be a problem.  Likely Clay is on the right problem that the nvidia drivers are having problems.  You can specify the driver to use in "/etc/X11/xorg.conf".  For example (I don't have an intel-card this is for my nvidia):

```
Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
EndSection
```

If you want your nvidia card to be the default, there are a couple things you can do.  First, try starting the GUI with "startx" and see if it give you any useful input.  If it doesn't.  Second, look at "/var/log/Xorg.0.log" and look for EE messages and post themhere.

---

