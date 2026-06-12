---
title: "Video driver help needed.."
date: 2009-01-24
forum: New to Ubuntu
---

### Post by WU8V on 2009-01-24
I have finally got a network connection on this box, but I am still stymied as to how to get the video driver installed. I have the file on a flash drive, but I don't know where to put it in the directory structure.

it is the for the GFX5200 (NVidia) and I have the .run file on a flash drive (or I can download to this machine again if necessary).

Please help this old newbie get the monitor situation straightened out.

Thanks and regards,
Kurt

---

### Post by taurus on 2009-01-24
What version is the driver that you've downloaded from nVidia's site?  I believe you need the legacy version which is something like 173.

---

### Post by Michael.Godawski on 2009-01-24
hey, 

have you checked the hardware drivers in 
System > Administration > Hardware Drivers?

Also there is the application EnvyNG which automatically installs ati and nvidia drivers.

---

### Post by WU8V on 2009-01-24
Yes, I have the legacy driver... and yes I have tried the system hardware drivers installation... it tries to download the driver and never gets past 0% and never activates the driver

I don't know where to put the driver that I have so that it will install correctly.

Thanks again,
Kurt

---

### Post by taurus on 2009-01-24
Insert the flash drive.  It should automount with an icon on your desktop to just copy the file to your desktop.  

Then, reboot your machine into recovery mode from GRUB menu.  At the prompt, change to your $HOME, assuming it's /home/john.

```
cd /home/john/Desktop
chmod +x **filename**.run
./**filename**.run
```
Replace the **filename** with the actual name of the file that you have downloaded.

If everything installed successfully, it will tell you to reboot so do so.

```
shutdown -r now
```

---

### Post by WU8V on 2009-01-24
Everything goes according to plan until it tries to find a pre compiled kernel module...it can't find it.... then it tries to compile it, and it errors out.. I have updated the build essential file, and installed it. Not to top that, I have a list of 224 updates that it wants me to download to the tune of over 200Mb....I thought that I was away from this stuff when I got away from Micro$haft

Any ideas how I can get the 273 driver installed? (it was not listed in the updates)

Thanks again,
Kurt

---

### Post by WU8V on 2009-01-24
oops, make that the 173 driver

regards,
Kurt

---

### Post by taurus on 2009-01-24
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by WU8V on 2009-01-24
Is get upgrade different than get install?

---

### Post by taurus on 2009-01-24
Use the install option if you want to install something.  Use the upgrade version if you want to upgrade your machine to the latest bug/security fixes.  These are not the same.

---

### Post by starcannon on 2009-01-24
I have found that it requires removing the hardware drivers manager drivers before installing the nvidia.com drivers to get things working correctly. 
sudo apt-get remove --purge nvidia*
sudo rm /lib/restricted-modules/.nvidia*

Or just follow my guide here: [http://ubuntuforums.org/showpost.php?p=5086971&postcount=6](http://ubuntuforums.org/showpost.php?p=5086971&postcount=6)

GL and have fun, pm me if you need help with my guide.

---

### Post by minsf on 2009-01-25
> **starcannon said:**
> I have found that it requires removing the hardware drivers manager drivers before installing the nvidia.com drivers to get things working correctly. 
sudo apt-get remove --purge nvidia*
sudo rm /lib/restricted-modules/.nvidia*

Or just follow my guide here: [http://ubuntuforums.org/showpost.php?p=5086971&postcount=6](http://ubuntuforums.org/showpost.php?p=5086971&postcount=6)

GL and have fun, pm me if you need help with my guide.

this guide is great, however:
A) in step 3, you should use
```
sudo apt-get install build-essential gcc linux-headers-$(uname -r) pkg-config make xserver-xorg-dev
```
some of them are probably already installed on your system, but they are needed according to the nvidia folks (see their forum).

B) get the driver from [ftp://download.nvidia.com/XFree86/Linux-x86/](ftp://download.nvidia.com/XFree86/Linux-x86/) 
be sure to check appendix A of the corresponding readme (to be sure that it will work with your card). these tend to be more up to date then those offered automatically by nvidia.com (for instance, the 96.43.07 offered by nvidia.com does not compile well with the 2.6.27-9 kernel, so that one needs the "beta" 96.43.09). as of today, you will probably need 173.14.15 or 173.14.12 
be sure to RIGHT CLICK it and save, (rather than run it with a left click)

C) you can run the file with the -A parameter to see help about the options. that is:
```
sudo sh nvidia_file.run -A
```
where, you should change the nvidia_file to the name of the driver you downloaded. in particular, if you run the pkg1 file with the pkg-history option:
```
sudo sh nvidia.run --pkg-history
```
you will see that there should not be a difference for you between pkg0 and pkg1 (they added something for radhat/fedora etc, but for ubuntu there should be no difference)

D) you can save the work in step 10. just skip it and in step 11 run
```
sudo sh NVIDIA_file_name.run
```

E) you may need to tinker with your /etc/X11/xorg.conf using
[http://wiki.compiz-fusion.org/Hardware/NVIDIA](http://wiki.compiz-fusion.org/Hardware/NVIDIA) , appendix D of the nvidia readme, and the manpage for xorg.conf
before you change this file, you probably want to back it up as mentioned in the above guide.

---

### Post by starcannon on 2009-01-25
minsf:
Wow thanks, wish we still had a "thankyou" clicky avaialble (I'm sure it will return, till then accept this as a show of gratitude)
I will do some updating to my guide, and even throw a link back to your post here if its okay.
I'm just chillin at the moment, but perhaps tomorrow I'll take time to update the guide, I've been meaning to add an envy-ng uninstall line anyway.
I will note that I still install all of my cards the same way (however I don't have to do any clean up as I don't use other methods than my own first); and I have flawless installs, and excellent performance all the way up till and including Ubuntu 8.10.

Thanks again,
Rob aka starcannon

> **minsf said:**
> this guide is great, however:
A) in step 3, you should use
```
sudo apt-get install build-essential gcc linux-headers-$(uname -r) pkg-config make xserver-xorg-dev
```some of them are probably already installed on your system, but they are needed according to the nvidia folks (see their forum).

B) get the driver from [ftp://download.nvidia.com/XFree86/Linux-x86/](ftp://download.nvidia.com/XFree86/Linux-x86/) 
be sure to check appendix A of the corresponding readme (to be sure that it will work with your card). these tend to be more up to date then those offered automatically by nvidia.com (for instance, the 96.43.07 offered by nvidia.com does not compile well with the 2.6.27-9 kernel, so that one needs the "beta" 96.43.09). as of today, you will probably need 173.14.15 or 173.14.12 
be sure to RIGHT CLICK it and save, (rather than run it with a left click)

C) you can run the file with the -A parameter to see help about the options. that is:
```
sudo sh nvidia_file.run -A
```where, you should change the nvidia_file to the name of the driver you downloaded. in particular, if you run the pkg1 file with the pkg-history option:
```
sudo sh nvidia.run --pkg-history
```you will see that there should not be a difference for you between pkg0 and pkg1 (they added something for radhat/fedora etc, but for ubuntu there should be no difference)

D) you can save the work in step 10. just skip it and in step 11 run
```
sudo sh NVIDIA_file_name.run
```E) you may need to tinker with your /etc/X11/xorg.conf using
[http://wiki.compiz-fusion.org/Hardware/NVIDIA](http://wiki.compiz-fusion.org/Hardware/NVIDIA) , appendix D of the nvidia readme, and the manpage for xorg.conf
before you change this file, you probably want to back it up as mentioned in the above guide.

---

### Post by minsf on 2009-01-25
> **starcannon said:**
> minsf:
Wow thanks, wish we still had a "thankyou" clicky avaialble (I'm sure it will return, till then accept this as a show of gratitude)
I will do some updating to my guide, and even throw a link back to your post here if its okay.
I'm just chillin at the moment, but perhaps tomorrow I'll take time to update the guide, I've been meaning to add an envy-ng uninstall line anyway.
I will note that I still install all of my cards the same way (however I don't have to do any clean up as I don't use other methods than my own first); and I have flawless installs, and excellent performance all the way up till and including Ubuntu 8.10.

Thanks again,
Rob aka starcannon

it could be that gcc and the linux-headers where fine on your system (which is why it works for you) but we want this to work for other systems too... i trust the developers (they say the packages are needed). 
like i said, your guide is great- my post just added minor cosmetic changes :)
feel free to quote or cut and paste in your post
cheers

---

### Post by minsf on 2009-01-25
> **WU8V said:**
> and yes I have tried the system hardware drivers installation... it tries to download the driver and never gets past 0% and never activates the driver

By the way, the reason why "Hardware Drivers" does not install, may be due to restrictions in the /etc/apt/sources.list file. 
Please go to System>Administration>SoftwareSources and be sure to check the first 4 boxes in the "ubuntu software tag", especially the "restricted" repository.
then try again System>Administration>HardwareDrivers

---

### Post by WU8V on 2009-01-25
This is bordering on insane.
It's like I do the same thing over and over expecting different results. I am trying to use something other than Windoze to get away from this crap.

Nothing I have done has produced a working install for the 173 kernel module.

I assume since the program says that there is a precompiled version of this file, that it can be precompiled.

Is there any way that someone cans send me a precompiled kernel module, and tell me where it is supposed to go in the directory structure?

Thanks and regards,
Kurt

---

### Post by Aang Aero on 2009-01-25
> **starcannon said:**
> I have found that it requires removing the hardware drivers manager drivers before installing the nvidia.com drivers to get things working correctly. 
sudo apt-get remove --purge nvidia*
sudo rm /lib/restricted-modules/.nvidia*

Or just follow my guide here: [http://ubuntuforums.org/showpost.php?p=5086971&postcount=6](http://ubuntuforums.org/showpost.php?p=5086971&postcount=6)

GL and have fun, pm me if you need help with my guide.
Thanks alot starcannon for the guide!  Really helped me out!  I am trying to make the switch from Windows to Linux, and just one of the picky things I would like to do is make sure I can get the latest drivers...  I am using KDE and the steps you provide work great, just had to change "gdm" to "kdm". 

Anyway, I used your guide to update to install NVIDIA-Linux-x86_64-180.22-pkg2.run.  How can I confirm that the drivers have been installed?  You mention in step 12 that I should see an Nvidia logo, but I don't believe I had one, however I wasn't sure if that was due to KDE or not.  

Additionally, I am able to "enable" desktop effects, but they don't appear to be working (i.e. - Wobbly Windows, etc.) 

I tried to install the latest Nvidia driver once before and I ended up having to reinstall.  So I am assuming that due to the fact that I am able to log into KDE again after the install that everything worked?  Or do I need to somehow "Activate" the driver?

 Thanks again for the guide!
-Aang

---

### Post by minsf on 2009-01-26
> **WU8V said:**
> This is bordering on insane.
It's like I do the same thing over and over expecting different results. I am trying to use something other than Windoze to get away from this crap.

Nothing I have done has produced a working install for the 173 kernel module.

if you read your post again and think about it - it actually does not tell us much, right?

where exactly did you get lost in the above guide of starcannon and in my remarks?

For instance, "Nothing" does not really tell us anything. instead, please post output of steps that did not work. maybe of also output of steps that did work. state "completed step 1 in your guide successfully / unseccessfully", etc.

by the way, did you update and upgrade your system like taurus suggested?
if you need to update it with 200MB then i guess that's what you need to do- trust the developers.

to your question, there is nothing bad about compiling the kernel. it should work if you have the tools needed (like build-essential. see my remark above about step 3 in starcannon's guide). so i do not think that it is essential for you to get a precompiled kernel. 

what is the exact name of the driver file?

---

