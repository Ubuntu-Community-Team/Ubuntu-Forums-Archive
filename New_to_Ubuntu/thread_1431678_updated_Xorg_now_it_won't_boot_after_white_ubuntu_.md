---
title: "updated Xorg now it won't boot after white ubuntu logo"
date: 2010-03-16
forum: New to Ubuntu
---

### Post by I8NY on 2010-03-16
So i did a update today and i just skimmed over the titles of the updates for xorg and a new kernel.  I did a reboot and when it loads it will show the white Ubuntu logo but then the screen goes black when the loading bar should come on and it doesn't respond after that.  I can go into the recovery kernel so i think the problem is with the ati proprietary driver not working with the new version xorg.  Is there a way to rollback the xorg version to get the ati driver working again?  I did try super grub disc and the black screen came on the loading bar part. 


2.6.31-20 Ubuntu 9.10 64bit
I don't know my xorg version

---

### Post by mcoleman44 on 2010-03-16
Did you try booting into an earlier kernel? 

If that works then just take a look at your xorg.conf and see whats going on.

It might not even be an xorg problem.

---

### Post by I8NY on 2010-03-16
i have tried earlier kernels and it doesn't work, same problem.  This has happened to me before when ati drivers didn't support the new xorg and i ended up reinstall ubuntu 3 time so i'm almost sure it is the new xorg.  I do have dual monitors so i don't know if that makes a difference.

---

### Post by mcoleman44 on 2010-03-16
If you can log in using recovery mode, can you log in running low graphics mode?

---

### Post by I8NY on 2010-03-16
there is no option to boot with low graphics, but the low graphics do work.  the root recovery option still works but that is all text.

---

### Post by mcoleman44 on 2010-03-16
Did you have to do any type of extra setup to make dual monitors work? chances are, you'll have to redo that with your current xorg.

---

### Post by I8NY on 2010-03-16
i did nothing to xorg.conf to get dual monitors working, i just used the Display app in system>administrative to configure them.

---

### Post by mcoleman44 on 2010-03-16
Did you have any proprietary drivers installed?

---

### Post by I8NY on 2010-03-16
i said i had it running my first post "...problem is with the _ati proprietary_ driver not working with the new version xorg."

---

### Post by mcoleman44 on 2010-03-17
My bad. Then all you should have to do is go into low graphics mode and reinstall the driver. Deactivate it and then re activate it.

---

### Post by I8NY on 2010-03-17
how do i go into low graphics mode?  there is no recovery option to to boot with low graphics, do i do it through it through the root option?

---

### Post by mcoleman44 on 2010-03-17
If you go into recovery mode, choose to continue boot. If its a problem with xorg it should give you the option of low graphics mode. 

But Im starting to think that its not your video driver thats the problem. If you just get the white logo forever then it sounds like a problem with the kernel not xorg. Does the caps lock key flash by any chance? If it does then this could be a kernel panic.

---

### Post by I8NY on 2010-03-17
okay i tried that but before press enter to boot normal there is text over it saying "* could not access PID file for nmbd" but once i go down and up it goes away.  This didn't happen before.  It boots but not into any graphics gui, all text.

---

### Post by mcoleman44 on 2010-03-17
ok, so now try typing startx and see what happens.

---

### Post by I8NY on 2010-03-17
okay that got me to the desktop, ya!, i did uninstall the ati driver and installed it again but on a normal boot it has a error, "Kernel panic - not syncing: VFS: unable to mount root fs on unknown-block(0,0)"  this might have messed it up even more.  So is there a way to downgrade xorg in the package manager or do you have a better idea?

---

### Post by mcoleman44 on 2010-03-17
To be honest Im all out of ideas. Im sure theres a way to downgrade xorg, But im not aware of it. Heres another thing you can try though. Open a terminal and type:
sudo update-grub

---

### Post by dreq on 2010-03-17
I have this problem as well using ati proprietary drivers. But i cannot log into recovery or low graphics because i have autologin enabled. How can i get into a console so i can try what you said earlier?
Thank you!

---

### Post by distortedecho on 2010-03-17
Correct me if I'm wrong but xorg auto configures on startup in 9.10.

Try this:

1. Get to the system console (no good in a terminal from the Ubuntu desktop – it must be a command line log in).

2. Log in using your username and password

3. Issue the following at the command prompt:
```

    sudo apt-get remove –purge xserver-xorg
```

4. Reboot the computer using the following:

    ```
sudo reboot
```

5. Log in once again. Then issue the following command:

    ```
sudo apt-get install xserver-xorg
```

6. Then issue the following command (don’t worry it looks like it’s done nothing):

    ```
sudo dpkg-reconfigure xserver-xorg
```

7. Then finally issue the command to reboot your computer again:

    ```
sudo reboot
```

---

### Post by nothingspecial on 2010-03-17
> **dreq said:**
> I have this problem as well using ati proprietary drivers. But i cannot log into recovery or low graphics because i have autologin enabled. How can i get into a console so i can try what you said earlier?
Thank you!

Press Ctrl Alt F2 (or F{3,4,5,6})

---

### Post by mcoleman44 on 2010-03-17
What do you mean you cant log into recovery? Does grub not give you that option? If you can get into recovery choose drop to root shell promt or something of the like and login from there.

---

### Post by caravel on 2010-03-17
This is fairly typical.  You need to recompile the fglrx driver for the new kernel.

Try booting to the terminal only and do: apt-get remove -purge *fglrx*.

---

### Post by acesabe on 2010-03-17
I use sgfxi to install latest fglrx module, it broke today - no biggy, sgfxi soon rebuilds new module - but I noticed on teh way it upgraded package libgl1-mesa-glx which wasn't upgraded with the kernel upgrades (et al) of today, which is interesting....

Have people using the Ubuntu fglrx had this issue also?

---

### Post by dreq on 2010-03-17
Ok. I tried Ctrl+F2, F3-F5 and for a brief second this shows up and then the screen goes black. The monitor doesnt go into stand by.Everything worked great till the update this morning.

Later edit: i booted with shift pressed and i chose the previous kernel .14. i managed to boot into ubuntu but in low graphics mode. there i reinstalled ati drivers from amd.com. did a reboot, got into ubuntu again and everything is ok now exept for the fact that my mouse cursor is MISSING! i've had it for today ... im going to bed.

---

### Post by nothingspecial on 2010-03-18
That`s because it should be Ctrl Alt F2 etc etc oops

---

### Post by dreq on 2010-03-18
Gave it up and installed windows home server, ill try again when ill have more free time. thx

---

### Post by mcoleman44 on 2010-03-18
Im sorry it didnt work for you. It may have though if you had tried installing the driver listed under system>admin>hardware drivers. 

Open source drivers normally arent very reliable. (no offense to the writers of the said drivers.)

---

### Post by I8NY on 2010-03-18
I got my error fixed now after i selected fix packages in recovery so now i can boot to the desktop with 1 monitor.  I had problems with the 2nd monitor because it would not auto detect(it did before) and it would always reset the resolution on start up.  So i tried plugging in the monitors in different dvi ports and the 2nd monitor got detected and everything works.  Thanks mcoleman44 for the "startx" commend to get me to the desktop.

---

