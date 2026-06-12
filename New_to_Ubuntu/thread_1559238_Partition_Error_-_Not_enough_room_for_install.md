---
title: "Partition Error - Not enough room for install"
date: 2010-08-23
forum: New to Ubuntu
---

### Post by robertcowper on 2010-08-23
Hey everybody...thanks in advance for helping out somebody brand new to the dual-boot with ubuntu world...

i'm trying to try out ubuntu (more than just running it off the live usb) and decided i'd try the dual boot with XP....

when at the partition set up, I was originally given the option of having ubuntu have 3gb of my 160gb...i tried evening it out, but each time the installer would lock up or i would get an error that it cannot partition the way i tried

after getting very frustrated, i figured i would try not editing the partition and go with what it was suggesting (3gb for ubuntu and ~150 for xp)...i was able to continue through the installation, but after i got to 100%, it brought me back to the desktop and then locked up

i restarted, booted into ubuntu and noticed things weren't going well...an error popped up (wish I wrote it down, I'm trying to get it to come up again) but it let me continue to the "desktop"...

the screen was black with a square in the middle asking me to pick my user, but no matter what i pressed it wouldn't let me continue...i noticed in the bottom corner it said that i didn't have enough space for the install

i'm assuming it wasn't able to fully install due to the partition error...i've tried rebooting and have had a few different things happen...i got a "low graphics mode" pop-up but when it tried to reset the display it got stuck "checking battery state..."...i've also tried going into the command prompt to try a few things i've seen throughout the forums, but when asked for my user id/password i am unable to type into the password field (tried turning caps on/off, etc)

sorry, i know it's a ton of info and i wish i had taken better notes of the errors, but i'm hoping somebody can help me wipe this failed install out and re-partition (correctly) and re-install

thank you so much in advance for your help!!

---

### Post by Elfy on 2010-08-23
Did you defrag before you tried to resize the partitions? I've had an issue where the pagefile in windows was in the way - turning it off, defragging, installing ubuntu and then turning on the pagefile worked under those circumstances.

Sounds as though it didn;t install properly - reinstalling it and trying to expand the partition after dong the above might help - this time though if you go for a re-install you will need to also deal with the partitions the installer made the first time - sounds worse than it is :)

If you have ethernet during the install - you can get back here - maybe post a screenshot of the partitions - it might also be worth creating partitions before you install and then use them.

---

### Post by robertcowper on 2010-08-23
Thanks for the reply!!  I did not defrag...I thought about it, but was too eager to testdrive ubuntu...lesson learned!!

In order to re-install, I'm guessing I need to boot from the USB and install as if it's my first try?  Or is there another way I should re-install?

---

### Post by Elfy on 2010-08-23
Sort of ... 

Do the defrag - make sure when it is done there is nothing at the 'other' end - green I think 

Now - this time you already have partitions created - no way of telling how it has done the partitions till you boot the livecd. 

So boot with the usb - don't start the installer yet - but start the partition editor - it's in the system admin menu. Shrink the XP partition as much as you need.

_IF_ you have both swap and normal linux partitions _INSIDE_ an extended partition you must expand the extended first. You will also need to right click on the swap and then turn it off. Then once you have expanded that you will be able to expand the linux partition. 

If you only have swap inside the extended partition then you can leave that alone and resize the linux one first.

Once you have them resized you can start the installer - when you get to the partition part - choose MANUAL.

In the new window - select your expanded partition - edit - choose ext4 as the use as option and / as the mountpoint. Exit and carry on with the install.

Alternatively you can delete the existing linux partitions and extended - shrink the XP in the partition editor. Now when you use the installer you can choose a use free space option I believe.

---

