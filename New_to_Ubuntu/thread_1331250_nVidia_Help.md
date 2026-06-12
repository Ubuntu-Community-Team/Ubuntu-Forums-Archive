---
title: "nVidia Help"
date: 2009-11-19
forum: New to Ubuntu
---

### Post by JETLogistics on 2009-11-19
:confused:
 
I know you've probably seen a load of these messages around here, but I've never found quite the right answer to my problems (and after just over 500MB of .deb, .run and .rpm packages downloaded and NONE of them do what I need), so I'm posting here as a desperate cry for help.
 
I'm VERY new to Ubuntu (I've only had it installed for about 3 or 4 days), and I have an unfortunate lack of an internet connection at home (if you're now thinking how am I posting here then, I'm using my college to post here, download countless packages and read through page upon page of READMEs before getting home at the end of the day and it all be a waste of time). I have a VERY poor screen resolution (800x600) compared to Vista which had a nice 1280x1024, and this is because Ubuntu cannot work out what my monitor is, and I'm trying to install the nVidia Linux driver. I have worked out to go to recovery mode, type the root password, type telinit 3 and run the package. THEN it gets to the Kernel bit.... and it fails miserably. It just says it cannot build the kernel, and exits the package. 
 
I don't know what type of Kernel I'm running, and I *think* I'm running Ubuntu 9.10 (I downloaded the ISO from their website, that's all I know...
 
As I said, I don't have an internet connection, so I cannot update my Kernel online, which means I cannot update my kernel, and therefore cannot install the nVidia driver, making my Ubuntu fairly bland in comparison to my brother's, who has an internet connection for his laptop at his house.
 
Can anyone out there help me?
 
Many thanks, 
Jacob.

---

### Post by ukripper on 2009-11-19
To install nvidia drivers you don't need new kernel. Ubutnu 9.10 has fairly recent kernel. As stated you don't have internet connection this will be bit tricky but you do have your ubuntu 9.10 live cd from where you actually installed ubuntu? 

[LIST=1]
[*]Boot into your normal ubuntu installtion:
[*]insert your Live cd after you have logged in your account.
[*]Go to System-->Administration-->Software Sources. there check the option of under Installabe from CD/DVD - "CD with ubuntu 9.10". It should be ticked. then close.
[*]After that go to terminal and run:
[*]```
sudo apt-get update
```

[*]Then go to System-->Administration-->Hardware drivers .This should install your nvidia drivers automatically.
[/LIST]

---

### Post by Arup on 2009-11-19
Jacob,

Download the correct package from here at [http://www.nvidia.com/object/linux_display_ia32_190.42.html](http://www.nvidia.com/object/linux_display_ia32_190.42.html) for x32 and for x64 [http://www.nvidia.com/object/linux_display_amd64_190.42.html](http://www.nvidia.com/object/linux_display_amd64_190.42.html) make sure to download the package ending with .run2

Do a sudo apt-get build essential as from your posts, the reason it can't build the kernel is due to the fact that build tools are not installed.

Then do a ctrl+alt+F2 and login.

Do a sudo service gdm stop

Make sure your driver is in Home folder

do a sudo sh NVIIDA and hit tab.

Say yes to all the prompts you get and at the end it will write to X and go back to tty, type sudo reboot and when the system boots up you will have nvidia driver installed.

---

### Post by sandy8925 on 2009-11-19
You can followthe steps that Arup mentioned. I always use them and I've never had any problems.

To stop gdm you can also use:

sudo /etc/init.d/gdm stop

It should be sudo sh ./NVIDIA........

If it asks you whether it should automatically configure xorg.conf say yes. Otherwise the nvidia drivers won't be used.

You don't need to restart the system. You can just type:

sudo /etc/init.d/gdm start

and Gnome will start up once again with the Nvidia drivers enabled (if they installed properly).

---

### Post by 3rdalbum on 2009-11-19
If you had an internet connection at home, you could just to the Hardware Drivers program and it would automatically download and install the driver for you.

Depending on your card, you might need the 96, 173 or 185 driver from Nvidia. Don't bother downloading this from the Nvidia website; Ubuntu packages these drivers for you.

Go to [http://packages.ubuntu.com](http://packages.ubuntu.com) and download these packages for Karmic:

nvidia-185-kernel-source
nvidia-185-libvdpau
nvidia-185-modaliases
nvidia-common
nvidia-glx-185
nvidia-settings

If you're using an older card that requires the 173 driver, obviously change those package names to reflect the "173" (note: the vdpau package is not available for the 173 driver. It's not essential, but it is good to have if you have a recent Nvidia card).

Install those packages and reboot. Now run Nvidia-settings as root:

```
gksudo nvidia-settings
```

Tell it to save to your Xorg.conf file. When you reboot, you should have the proper Nvidia driver running.

---

### Post by Arup on 2009-11-19
Thanks for pointing out the ommisions Sandy,was in a hurry so left out the ./, just one point, /etc/init.d/gdm stop doesn't work anymore in Karmic, it has been superseeded by sudo service gdm stop and sudo service gdm start

---

### Post by JETLogistics on 2009-11-20
Okay, thanks for your help on installing the driver guys, I've got it to install and rebuild the kernel, however, NOW I've got a problem of the fact the Hz and screen resolution is too much for my monitor and even my TV. 
 
Is there a text-based sudo/root command to set the resoultion? I can see the login screen, and everything before that, but as soon as I log on (as my account, another account and root) the monitor and TV complain!
 
Sorry to be such as pest!
 
Thanks again for your previous help! 
 
-Jacob.

---

### Post by Arup on 2009-11-20
sudo vi /etc/X11/xorg.conf 

You need to edit the pertinent lines relating to monitor resolution and frequency and be careful or else you will end up damaging your monitor.

---

### Post by 3rdalbum on 2009-11-20
> **Arup said:**
> sudo vi /etc/X11/xorg.conf 

Make that:

```
sudo nano /etc/X11/xorg.conf
```

Please recommend "nano" over Vi(m), because people who are new to Linux won't have the foggiest clue how to use Vi.

---

### Post by Arup on 2009-11-20
You are rigth 3rdalbum, vi can be daunting for newbies, its force of habit for a guy who basically grew up with Unix so please bear with my indulgence :)

---

### Post by Arup on 2009-11-20
[http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

Some very good advice on how to modify xorg.conf here. Please take a look.

---

### Post by JETLogistics on 2009-11-21
Don't know which of you to thank, so I'll thank you all because one of the codes worked, I am now back to a friendly, GUI'd Ubuntu with nice, pretty desktop effects!

Thanks to everyone who helped and tried so hard to get my Ubuntu working, it means a lot to me!

Thanks again,

Jacob.

---

### Post by Arup on 2009-11-21
Thank you for persevering and not giving up.

---

