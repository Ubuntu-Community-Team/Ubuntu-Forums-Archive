---
title: "Nvidia Geforce 8800 GT trouble"
date: 2010-01-23
forum: New to Ubuntu
---

### Post by Dynamus on 2010-01-23
I downloaded the drivers through the manager but found that videos would play choppy. I decided to download the drivers from Nvidia and that made things worse. I guess I can't run the special effects, or any for that matter, in my appearance manager. I partitioned the hard drive and I find that windows runs choppy sometimes. But anyway all I'd like to know is how to get Linux up going 100 % so I can explore it and know what to expect to encounter in other distro's.

---

### Post by Dynamus on 2010-01-23
Come on man, no one wants to help me?

---

### Post by aviedw on 2010-01-23
Which drivers did you install and how did you install them? Did you also make sure that you uninsulated the previous Nvidia drivers before installing the new ones. I need to know what you did and what your working with before I can try to help.

---

### Post by Dynamus on 2010-01-23
No, I didn't. Whatever drivers I had first were running kind of laggy so I went Nvidia site and downloaded their drivers. I couldn't auto execute the install them and couldn't do it through terminal. I had to completely shut off the GUI, is that X server? Well any way I had to install as root and that brings me to where I am now.

---

### Post by LuisGMarine on 2010-01-23
I have the same video card and the same problem.  What I do to fix it, is everytime that I'm about to watch a movie on my computer I just turn my special effects off.  This stops the choppy video playback.  It's a known bug I"m sure, but that's the only work around I know about as of right now.

---

### Post by daimaru on 2010-01-23
> **Dynamus said:**
> No, I didn't. Whatever drivers I had first were running kind of laggy so I went Nvidia site and downloaded their drivers. I couldn't auto execute the install them and couldn't do it through terminal. I had to completely shut off the GUI, is that X server? Well any way I had to install as root and that brings me to where I am now.
edit:maybe you just need to change the video output module in your videoplayer. just try a few x11 etc

---

### Post by Dynamus on 2010-01-24
> **LuisGMarine said:**
> I have the same video card and the same problem.  What I do to fix it, is everytime that I'm about to watch a movie on my computer I just turn my special effects off.  This stops the choppy video playback.  It's a known bug I"m sure, but that's the only work around I know about as of right now.
Well the thing is that I can't use any effects either. So if I view a video I'm already at the lowest visual settings. As far as videos go I'm talking about Youtube and stuff. I'm thinking of reinstalling ubuntu.

---

### Post by warfacegod on 2010-01-24
There are some good tips in here for making Flash videos run smoother.

[http://ubuntuforums.org/showthread.php?t=1193567]("http://ubuntuforums.org/showthread.php?t=1193567")

You said that Windows is behaving the same way. That sounds more like a problem with hardware than a driver issue. If two OSes on the same hardware exhibit the same behaviors, that's almost always a hardware problem. Or it could possibly be an improper BIOS setup.

---

### Post by Dynamus on 2010-01-24
> **warfacegod said:**
> There are some good tips in here for making Flash videos run smoother.

[http://ubuntuforums.org/showthread.php?t=1193567](http://ubuntuforums.org/showthread.php?t=1193567)

You said that Windows is behaving the same way. That sounds more like a problem with hardware than a driver issue. If two OSes on the same hardware exhibit the same behaviors, that's almost always a hardware problem. Or it could possibly be an improper BIOS setup.

To clarify Windows runs well I just find that if I'm playing my games the graphics seem to load a little slower and just not as well as I used to. If it was an improper bios setup then how could I tell other than these symptoms and what would I have to do to fix it. I'm not very knowledgeable person when it comes to computers.

---

### Post by warfacegod on 2010-01-24
> **Dynamus said:**
> To clarify Windows runs well I just find that if I'm playing my games the graphics seem to load a little slower and just not as well as I used to. If it was an improper bios setup then how could I tell other than these symptoms and what would I have to do to fix it. I'm not very knowledgeable person when it comes to computers.

If it's BIOS I'd look for anything that sounds like it might relate to the video cards. I had a Compaq that would let me set the video RAM to 8, 16, or 32 MB RAM.

Your card is a Corvette as compared to a Ferrari (or the Ford Escort I've got. Perhaps horse draw carriage would be more accurate). It should have no problems with running whatever you ask of it, within reason.

If you go to: System> Admin.> Hardware Drivers you can deactivate the the recommended driver. Then you should reinstall the driver you got from nVidia. Make sure you got the right architecture driver. nVidia's site has a 32 Bit and a 64 Bit option for searching. You'll need to get the one that matches your OS.

---

### Post by aktiwers on 2010-01-24
I can explain to you how you install the drivers from invidia,

This is a manual install, which means that a kernel upgrade will break the installation and you will
need to reinstall the driver after each kernel upgrade. Kernel upgrades are not that often though, therefore Im personally happy to reinstall when it happens.. 

Well here goes.

1) Download the driver from here:
[http://www.nvidia.com/object/linux_display_ia32_190.53.html](http://www.nvidia.com/object/linux_display_ia32_190.53.html) (32bit)
or
[http://www.nvidia.com/object/linux_display_amd64_190.53.html](http://www.nvidia.com/object/linux_display_amd64_190.53.html) (64bit)

and save it in your home folder.

2) Open terminal(applications=> accessories=>terminal) and type:
```
chmod +x NVIDIA<hit-tab-key-on-keyboard>
```

3) Now you need to close X and go to fullscreen terminal. Close all apps and save all work and type in terminal:
```
sudo /etc/init.d/gdm stop
```
enter your password and hit enter.

4) login and type:
```
sudo ./NVIDIA<hit-tab-key-on-keyboard>
```
Clik OK, next, OK and so on until its done.

5) All done - now reboot 
```
sudo reboot
```

---

### Post by aktiwers on 2010-01-24
Did you install ubuntu-restricted-extras for video codec and so on?

---

### Post by Dynamus on 2010-01-24
> **aktiwers said:**
> Did you install ubuntu-restricted-extras for video codec and so on?

Hmm, I don't know if I should because that is exactly what I did last time. I just reformatted Ubuntu again and using the recommended drivers right now. They work but still feel choppy when I have the visual effects on extra. Where can I get a game on linux to test it or an application maybe?

---

### Post by ikt on 2010-01-24
> **Dynamus said:**
> Where can I get a game on linux to test it

Nexuiz is a fairly decent 3d game in the ubuntu software centre.

---

### Post by cenzorrll on 2010-01-25
are you talking about watching videos online, meaning you need the flash plugin?  or are these movies you own and have on your harddrive?  if it's online then you need to read Warface's first post, as flash has known issues and it's NOT your video card.

---

### Post by Dynamus on 2010-01-25
> **cenzorrll said:**
> are you talking about watching videos online, meaning you need the flash plugin?  or are these movies you own and have on your harddrive?  if it's online then you need to read Warface's first post, as flash has known issues and it's NOT your video card.

Well, yes and no. I'm saying if I'm watching youtube or some other flash based video and it has a lot of action then it lags a bit. I did the bench mark thing and scored a 1455 which isn't that good with Firefox 3.5, I guess. Well, everything is working good enough and I do my gaming in windows so I guess this is solved. Thanks for the help guys.

---

