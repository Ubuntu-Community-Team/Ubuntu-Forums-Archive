---
title: "Resolution problems"
date: 2009-02-12
forum: New to Ubuntu
---

### Post by itsvan on 2009-02-12
Hello there,,i was running Gnome and i had several resolution problems much that past threads could not fix,,i ended up installing KDE instead,,but my resolution is still low and i cannot fix this problem,,what is odd i have my drivers enabled for my graphics card,,but when i disable it the resolution seems to work perfectly and gives me all the options as it used to,,but then i cannot use any special effects,,,what is going on???

---

### Post by abyssius on 2009-02-12
> **itsvan said:**
> Hello there,,i was running Gnome and i had several resolution problems much that past threads could not fix,,i ended up installing KDE instead,,but my resolution is still low and i cannot fix this problem,,what is odd i have my drivers enabled for my graphics card,,but when i disable it the resolution seems to work perfectly and gives me all the options as it used to,,but then i cannot use any special effects,,,what is going on???

Have you tried running the configuration program for your proprietary graphics driver?  Anyway, what card do you have? I had a problem with NVIDIA where I could only get 640x480 whenever I enabled the driver. It turned out to be because the driver did not properly detect my monitor. I fixed it by manually entering the monitor's horizontal sync, vertical refresh rate and my desired resolution in my xorg.conf file.

---

### Post by itsvan on 2009-02-12
That sounds like it could be the problme,,its an NVIDIA GEFORCE 7 series,,,its enabled but it seems like its not working right..what now?

---

### Post by paydaydaddy on 2009-02-12
If the problem is that you do not have the option for the correct resolution, run this command in terminal and then check resolutions options.

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by abyssius on 2009-02-12
> **paydaydaddy said:**
> If the problem is that you do not have the option for the correct resolution, run this command in terminal and then check resolutions options.

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

When I tried this command it corrected the resolution, but for some reason it reloaded the NV driver instead of the NVIDIA driver. I think he can already do this, since he stated he gets the correct resolution when he disables the driver. He wants 3-D, which requires the proprietary driver working at the proper resolution. Does this command work with the NVIDIA proprietary driver?

---

### Post by abyssius on 2009-02-12
> **itsvan said:**
> That sounds like it could be the problme,,its an NVIDIA GEFORCE 7 series,,,its enabled but it seems like its not working right..what now?

What resolution do you get when you enable the driver? 

How have you tried to adjust it? 

What resolution do you want it set to?

You'll probably have to post your xorg.conf file. Do you know how to do this?

---

### Post by paydaydaddy on 2009-02-13
I think that the command I posted does not work with the nvidia driver. Sorry, I had not noticed that before.

---

### Post by itsvan on 2009-02-13
my resolution is only at 1024x768,,its way to low,,everything is huge,,still havent foudn a way to fix it,,when my driver is disabled it goes back to letting my go higher,,but then the 3d effects do not work

---

### Post by itsvan on 2009-02-13
and sorry i do not know hot to post the xorg.conf file

---

