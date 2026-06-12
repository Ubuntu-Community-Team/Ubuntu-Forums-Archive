---
title: "nvidia drivers"
date: 2009-07-11
forum: New to Ubuntu
---

### Post by heyyy on 2009-07-11
there is new version of nvidia drivers but there is no update in "hardware drivers" window...
how can i get it?
why its not on the repos yet?

---

### Post by SuperSonic4 on 2009-07-11
Because ubuntu devs have to make an deb file out of them and then host them - this is after stability checks too.

You can manually install them though

---

### Post by earthpigg on 2009-07-11
> **heyyy said:**
> 
why its not on the repos yet?

it hasn't been extensively tested with Ubuntu yet, of course.

and even once it is, it may only make it into the next release -- 9.10. ;)

---

### Post by heyyy on 2009-07-11
so what you mean is that unless i do a manual install i wont have the drivers?

---

### Post by wo1fe on 2009-07-11
> **heyyy said:**
> so what you mean is that unless i do a manual install i wont have the drivers?

yeah that is what it is seeming like. i have been trying to get the file to install for awhile now. there are some useful information in the post that i made about this. here is the link maybe one of the ways might help you.

[http://ubuntuforums.org/showthread.php?t=1209038](http://ubuntuforums.org/showthread.php?t=1209038)

---

### Post by Crafty Kisses on 2009-07-11
> **heyyy said:**
> so what you mean is that unless i do a manual install i wont have the drivers?
Well what that means is you won't have the latest drivers, unless you manually install the latest nVidia drivers. Honestly it's really easy. I do it all the time.

---

### Post by heyyy on 2009-07-11
> **Codename said:**
> Well what that means is you won't have the latest drivers, unless you manually install the latest nVidia drivers. Honestly it's really easy. I do it all the time.

thanks so how im going to do that?

---

### Post by SuperSonic4 on 2009-07-11
Once you've downloaded them press ctrl+alt+F2 to drop to a terminal and log in there. From there type ```
sudo ./NVIDIA...
``` where ... is some crap you don't need to remember - just type in NV and press tab and chances are it'll come up[

---

### Post by Crafty Kisses on 2009-07-11
> **heyyy said:**
> thanks so how im going to do that?
Download your driver off of nVidia's website. Now once you have downloaded the driver, you need to press Control-Alt-F2, then enter the following:
```
sudo /etc/init.d/gdm stop

```
Then once you've done that you need to run the following, remember I'm just guessing the file is called NVIDIA-Linux and it's saved to your desktop, so remember substitute your information:
```
cd ~/Desktop
chmod +x NVIDIA-Linux.run
sudo ./NVIDIA-Linux.run
```
Once it has installed and you have confirmed everything in the nVidia installer, you need to run the following:
```
sudo /etc/init.d/gdm start
```
If the driver isn't working properly for you, you need to stop the X server, and run the following:
```
sudo sh NVIDIA* --uninstall
```
Where the * is, you need to put your driver information. You might have some errors while you're trying to build the nVidia drivers, but if you do you might need to install the "build-essential" package to finish the install, so run:
```
sudo apt-get install build-essential

```
Then try the install again.

---

### Post by NOTAGEEK on 2009-07-11
Lets not let this thread die out...

i dont think i am the only 1 lurking here to see the end results...

i installed this same driver a day or 2 ago and had to remove it...

i have gforce 9600gt and wanted better than an 8x6 res ...

being very new to pc's i made the rookie mistakeof adding a handful of drivers at once...

bottom line is i had to remove the nvidia 185.xxx driver and spend a few hours getting the system back where it was thanks to rhe mambers of this forum...

now i am back with my astonishing 8x6 res but up and running...

---

### Post by heyyy on 2009-07-11
> **NOTAGEEK said:**
> Lets not let this thread die out...

i dont think i am the only 1 lurking here to see the end results...

i installed this same driver a day or 2 ago and had to remove it...

i have gforce 9600gt and wanted better than an 8x6 res ...

being very new to pc's i made the rookie mistakeof adding a handful of drivers at once...

bottom line is i had to remove the nvidia 185.xxx driver and spend a few hours getting the system back where it was thanks to rhe mambers of this forum...

now i am back with my astonishing 8x6 res but up and running...

i feel sorry for you

---

### Post by manilaph on 2009-07-17
Hi,

Since this is the most recent thread regarding Nvidia Drivers, I decided to post my problem here.

I think the problem is specific to Kubuntu 9.04 because I had no problems with Ubuntu 9.04.

To summarize, Kubuntu detects that I need to "activate" the Nvidia-96 driver (restricted).

I click on the "activate" button but nothing happens even after I wait 5 minutes... nothing happens at all. I do not know if something is happening in the background but it seems nothing is happening too.

And so, I did some research and saw that I could install via apt-get (nvidia-glx-96). I did that and installed 6 files including the nvidia-settings.

i enter nvidia-settings using root (as advised) and then inside nvidia-settings, it says that i do not have any nvidia drivers installed.

my question is... how do i stall the nvidia (version 96) driver when the "activate" button does not seem to work in Kubuntu but works in Ubuntu?

Thank you.

---

### Post by imtheshade on 2009-07-17
Hi! I'm having problems installing my FX5200 as well.I did everything Codename suggested but I get this error: "unable to open '/usr/lib/nvidia/libglx.so.xserver-xorg-core' for reading (no such file or directory)"
Could anyone please tell me what to do next ?

---

### Post by DownTown22 on 2009-07-17
Have you tried using the nvidia drivers that Ubuntu provides (via the restricted drivers)?

If those work, why bother with an update?

---

### Post by imtheshade on 2009-07-17
They don't work. My max resolution on linux is 800x600, and on windows it is over 1024x768. Help, please?

---

### Post by imtheshade on 2009-07-18
Are there any other ways to install my graphic card?, because reinstalling Linux does not help me at all and the instructions here don't seem to work..


L.E.: I managed to use the default drivers, but when I change resolution to 1024x768 the top of my screen is shaking. What can I do to fix that ?

---

### Post by 3rdalbum on 2009-07-18
> **imtheshade said:**
> They don't work. My max resolution on linux is 800x600, and on windows it is over 1024x768. Help, please?

The old Nvidia drivers that you need to use, are not really very good - you will probably need to add the 1024x768 mode to your xorg.conf.

To the other poster with the 9600GT: If you are running Ubuntu 9.04, the Nvidia driver in the Hardware Drivers program can run your card. I'm using that same driver to run a GTX260 and a friend is using it to run a 9600GT.

---

### Post by Sidewinder1 on 2009-07-18
> **imtheshade said:**
> Are there any other ways to install my graphic card?, because reinstalling Linux does not help me at all and the instructions here don't seem to work..


L.E.: I managed to use the default drivers, but when I change resolution to 1024x768 the top of my screen is shaking. What can I do to fix that ?
If the top of your screen is shaking (had exactly the same prob.) go to System---->Preferences---->Screen Resolution and change the Refresh Rate, probably to 58 Hz.

HTH,
Side

---

