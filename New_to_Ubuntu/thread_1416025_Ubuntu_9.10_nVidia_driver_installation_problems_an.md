---
title: "Ubuntu 9.10 nVidia driver installation problems and programs"
date: 2010-02-25
forum: New to Ubuntu
---

### Post by TreadLight on 2010-02-25
I am using the Acer Aspire X1200 Mini-PC with Ubuntu 9.10 just recently installed today. I have an nVidia Geforce 8200 that I would like to install the drivers for so that I can get a higher screen resolution than 800x600 and to play some video games. Sadly, I've had a few problems along the way.

1) Newly installed programs are not launching. I downloaded and installed Resolution Switcher and EnvyNG from the Ubuntu Software Center, but neither of them are opening at all.

2) I've downloaded the nVidia Linux drivers that are compatible with my video card from [here]("http://www.nvidia.com/content/DriverDownload-March2009/confirmation.php?url=/XFree86/Linux-x86/190.53/NVIDIA-Linux-x86-190.53-pkg1.run&lang=us&type=GeForce"), but the following happened when I tried to install them through the Terminal:

> miles@Venthemiux:~$ cd ~/Desktop
miles@Venthemiux:~/Desktop$ chmod +x nvidia.run
miles@Venthemiux:~/Desktop$ ./nvidia.run
Verifying archive integrity... OK
Uncompressing NVIDIA Accelerated Graphics Driver for Linux-x86 190.53............................................................................................................................................................................................................................................................................................................
nvidia-installer: Error opening log file '/var/log/nvidia-installer.log' for writing (Permission denied); disabling logging.
miles@Venthemiux:~/Desktop$ sudo sh nvidia.run
Verifying archive integrity... OK
Uncompressing NVIDIA Accelerated Graphics Driver for Linux-x86 190.53............................................................................................................................................................................................................................................................................................................

 [QUOTE] NVIDIA Accelerated Graphics Driver for Linux-x86 (190.53)

ERROR: You appear to be running an X server; please exit X before installing.  For further details,       
         please see the section INSTALLING THE NVIDIA DRIVER in the README available on the Linux driver    
         download page at [www.nvidia.com](www.nvidia.com).

[OK]

  >  NVIDIA Accelerated Graphics Driver for Linux-x86 (190.53)

ERROR: Installation has failed.  Please see the file '/var/log/nvidia-installer.log' for details.  You    
         may find suggestions on fixing installation problems in the README available on the Linux driver   
         download page at [www.nvidia.com](www.nvidia.com).

[OK]
[/QUOTE]
Please help... I really have no idea what to do. I mean, I am posting the in Absolute Beginner forum, aren't I?

---

### Post by Apollo87 on 2010-02-25
You need to kill your X server before you can start the install:
```

sudo /etc/init.d/gdm stop
```

Then when you're in a terminal:

```
sudo ./nvidia.run
```

Then after you install the drivers

```
sudo /etc/init.d/gdm start
```

---

### Post by TreadLight on 2010-02-25
I've installed the nVidia drivers but now I am in an even larger problem. After installation, Ubuntu is now forcing a 640x480 screen resolution. I am unable to change the resolution through Preferences>Display, and refers me to the NVIDIA X Server Settings program instead. Within this program, the only resolutions it offers me are "Auto" (which is automatically 640x480) "640x480" and "320x240". It says the model of my monitor is "CRT-0 (CRT-0 on GPU-0)" and the configuration is "Separate X Screen". The mode name "nvidia-auto-select". The "Detect Displays" option detects the exact same options. Is there a better way that I can change the resolution?

---

### Post by Apollo87 on 2010-02-25
Hmm, check out this thread, it might be of some use:

[http://ubuntuforums.org/showthread.php?t=860733](http://ubuntuforums.org/showthread.php?t=860733)

---

### Post by TreadLight on 2010-02-25
What if EnvyNG isn't even launching? I click on the icon, or right clik and press "Launch", but nothing happens. Keep in mind I am using Ubuntu 9.10.

---

### Post by Apollo87 on 2010-02-25
Make sure you have envyng-qt installed

```
sudo apt-get install envyng-qt
```

---

### Post by TreadLight on 2010-02-25
Ah, my nVidia drivers are installed now. Thanks.

Now I just need to know how I can force a higher screen resolution than the measly and annoying 640x480... How would I go about doing that? I'd like to have 1280x960, if possible.

---

### Post by Apollo87 on 2010-02-25
Have you tried changing the resolution in:

```
sudo nvidia-settings
```

Go to &#8216;X Server Display Configuration&#8217; and then select the resolution for your monitor.

It may be under something different actually, I don't have it in front of me.

---

### Post by TreadLight on 2010-02-25
> miles@Venthemiux:~$ xrandr
Screen 0: minimum 320 x 240, current 640 x 480, maximum 640 x 480
default connected 640x480+0+0 0mm x 0mm
   640x480        50.0* 
   320x240        51.0

If I enter the line you edited in, it brought me to the NVIDIA X Server Settings program and said this in the Terminal:

> miles@Venthemiux:~$ sudo nvidia-settings
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

---

### Post by Apollo87 on 2010-02-25
And you can't change the resolution under X Server Display Configuration?

---

### Post by TreadLight on 2010-02-25
I can, just only to the three options listed above (nothing more than 640x480).

---

### Post by Apollo87 on 2010-02-25
This is quite the pickle. Can you post your xorg.conf file?

---

