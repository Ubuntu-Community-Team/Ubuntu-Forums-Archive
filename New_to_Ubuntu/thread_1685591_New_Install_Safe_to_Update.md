---
title: "New Install Safe to Update??"
date: 2011-02-10
forum: New to Ubuntu
---

### Post by Elaphae on 2011-02-10
OK, I started out with the wubi install, managed to fix it once then updated and was unable to fix. This is a new install. I was unable to put ubuntu on its own partition so it is in the same partition, beside XP pro turbo. Everything is working as far as I can tell. (I now have maybe 3 hours using ubuntu lol).

There are over 200 updates that it wants to install - last time I did this I ended up with the grub root problem. I have read that that problem ONLY involves using the wubi method - this current install is by way of a cd. I would like to know if it is 'safe' to let the program update. Since it resides along side windows and I have started adding data I really do NOT want to have to risk wiping the disk to do a third install. (Just built the computer, drive only slightly contaminated by data LOL).

So install all suggested updates or are there some I should deselect? No matter how much it begs nothing gets updated till I read your answers.

---

### Post by Elaphae on 2011-02-10
One other thing, I cannot get the boot info script to run to save my life. I can live without it but wanted to have the information handy in case of problems.

---

### Post by lisati on 2011-02-10
Doing updates immediately after a fresh install *can* be a good thing: it helped me avoid troubleshooting some sound problems before I was ready,  when I first tried Ubuntu on my previous laptop nearly 4 years ago.

I'm a little bit confused by your current situation: did you use Wubi or did you do a dual-boot?

---

### Post by Frogs Hair on 2011-02-10
If you are using a Wubi installation you may want to hold off on installing any proprietary video drivers until the updates have been installed.

---

### Post by bcbc on 2011-02-11
For wubi the problem is grub-pc and grub-common. 

For wubi or normal, if you just installed (i.e. you only have the one kernel) I'd avoid updating that same kernel (adding new ones ok). The reason is that sometimes the initrd.img can be corrupted. (This happened to a number of people right after 10.04.1 came out). 

But apart from those cases, it should be fine letting it update.

---

### Post by Elaphae on 2011-02-11
I started with wubi, fixed it once and could not manage a second time so I wiped the partition (uninstall failed). Reinstalled from a CD I made. Installed in same partition as Windows. Been having great fun exploring and trying out some of the apps.

Y'all seem to be about evenly split as to updating or not. LOL Seeing 200 plus updates listed is daunting after the problem I failed with on the original install. Which made me want to start this thread and get experienced users input.

---

### Post by mastablasta on 2011-02-11
> **Elaphae said:**
>  Reinstalled from a CD I made. Installed in same partition as Windows. 
 
Not possible! unless you are using wubi again. or unless you deleted windows.
 
> 
Y'all seem to be about evenly split as to updating or not. LOL Seeing 200 plus updates listed is daunting after the problem I failed with on the original install. Which made me want to start this thread and get experienced users input.
 
They are not split - if you have a wubi install you need to lock the two mentione grub packages (you can do this in Synaptic). then you can update.
 
If however you did not make a wubi install you can update without worries. 
 
To get the bootinfo script running you can use the liveCD or liveUSB. boot from CD 8Or USB key) and select "try it" instead of installing it.

---

### Post by Elaphae on 2011-02-16
[QUOTE=mastablasta;10448088]Not possible! unless you are using wubi again. or unless you deleted windows.
 
Sorry, should have said it split the windows partition. The install is from a live CD, the one from wubi was removed. Later, when I can watch over it, I'll open a Polly Girl and start the update.

I think I was running the script w/o the cd and will try that again too, as directed.

---

### Post by Elaphae on 2011-02-20
Installed the update, running fine I think. (Rhythmbox wants to open when I click HD partitions. I can live with that and doubt it is associated with the updates. Thanks for the forums and thanks for the advice. Happier every day with Ubuntu.:p

---

### Post by deconstrained on 2011-02-20
I would recommend paying attention to the output of dpkg when you update. Since a common problems of people who do massive updates seems to be an Ubuntu that won't boot, you should observe to see if any errors occur during the kernel image rebuild (which is what gets run when the kernel gets upgraded) and if they do, run update-initramfs -v -k all -c in attempt to regenerate the image properly (and find out exactly what's going wrong if it doesn't).

Edit: oops, too late. Reboot and see if it works fine, if not, don't worry, it can easily be fixed without reinstalling.

---

### Post by cjazz on 2011-02-20
> **Elaphae said:**
> Installed the update, running fine I think. (Rhythmbox wants to open when I click HD partitions. I can live with that and doubt it is associated with the updates. Thanks for the forums and thanks for the advice. Happier every day with Ubuntu.:p

As for your unruly Rhythmbox, try [this.]("http://ubuntuforums.org/showthread.php?t=1667615")

---

