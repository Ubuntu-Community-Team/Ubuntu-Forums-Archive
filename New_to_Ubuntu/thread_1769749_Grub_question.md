---
title: "Grub question"
date: 2011-05-28
forum: New to Ubuntu
---

### Post by spillage2 on 2011-05-28
Hi all,

I have been on a learning curve with ubuntu and enjoying every moment...well nearly.

One thing I have got round to looking at or understanding is plymouth and grub..are these both the same things??

Is my grub splash screen the purple one I see on boot up or is this plymouth..

If I download a grub splash screen and install it is this the same as changing my plymouth settings..

sorry it all probably sound confusing..

Spill.

---

### Post by drs305 on 2011-05-28
The grub splash screen is independent of Plymouth. If you are using Natty you can change the background simply by adding an appropriate png, tga or jpg image to the /boot/grub folder and then running "sudo update-grub". 
Here's a link for Natty Grub backgrounds/fonts:
[http://ubuntuforums.org/showthread.php?t=1739412]("http://ubuntuforums.org/showthread.php?t=1739412")

For earlier versions, it is a little more complicated but not too much. Using a GUI app like Grub Customizer can help (click the "Customizer" link in my signature line).

---

### Post by spillage2 on 2011-05-28
Hi drs305,

Im running 10.04 and have been thinking of changing the  start up screen..

I have come across a few and found this one to try [http://gnome-look.org/content/show.php/grub+splash+screen-SystemFailure?content=123875](http://gnome-look.org/content/show.php/grub+splash+screen-SystemFailure?content=123875)

but its shown for grub not plymouth..must I use plymouth or can this be installed?

spill.
[]("http://gnome-look.org/content/show.php/grub+splash+screen-SystemFailure?content=123875")

---

### Post by drs305 on 2011-05-28
I can help if you want to change the GRUB background - the background image that you see behind the Grub menu options. I am not talking about the splash screen you see as the OS boots, only the one that appears until you make an OS selection.  

If that is what you want to change (the boot splash image), the only you link to is not in a compatible format for Grub, but you can easily convert it to a png image with GIMP or another graphic app. 

If that's the image you want to use on the Grub screen just post back and I can tell you how to do it.

---

### Post by spillage2 on 2011-05-28
yeah I get it now grub is the boot menu and plymouth is you start up screen on the main start up...

I have installed this one [http://gnome-look.org/content/show.php/Floating-Ubuntu+Plymouth+Theme+by+dinin?content=142029](http://gnome-look.org/content/show.php/Floating-Ubuntu+Plymouth+Theme+by+dinin?content=142029)

but the res is awfull..

I have changed GRUB_GFXMODE to GRUB_GFXMODE=1280x1024 in the /etc/grub/default but its made no difference.

I have tried old google but cant seem to change it..I know its only a daft thing but I would like to understand how to fix it..

spill.

update:

I have now resolved this by installing startupmanager but this I feel is the wrong way being a gui..I would like to know how to do this manually if possible.

---

### Post by drs305 on 2011-05-28
I played with the background image - I"m assuming you extracted logo.png, or at least that is the one I pulled out of the .deb you referenced.

I tried it at various resolutions and it looked fairly good for me in all of them; I didn't try 1280x1024. You might try changing the image size to the resolution you want using GIMP so it doesn't have to stretch or contract the image. I think part of your problem is that the image is 1920x1080 which won't scale correctly to 1280x1024. You could crop the image to the proper ratio rather than resize it and the image will probably look much better.

Although 1280x1024 is a fairly standard resolution, at the grub prompt you may wish to press "c" to get to the grub prompt and run "vbeinfo" to make sure your system's BIOS can use that resolution before the OS is loaded.

As far as why it didn't accept the new resolution: again, check vbeinfo. It may not be available to grub. The image looked very good on my screen with 1280x1024. When you set the new resolution in /etc/default/grub, did you run "sudo update-grub" afterwards to ensure the change was incorporated into the grub.cfg file?

---

