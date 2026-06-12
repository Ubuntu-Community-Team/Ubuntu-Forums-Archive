---
title: "Update ruined graphics configuration (restricted driver with Nvidia)"
date: 2009-03-21
forum: New to Ubuntu
---

### Post by Zach.Town on 2009-03-21
Installed 8.10 no problems was running fine. Then I restarted after updating things.

I enabled the restricted graphics and got a black login screen.

I have an Nvidia GeForce 8800

---

### Post by wjp.reg on 2009-03-21
have you tried running recovery mode and letting ubuntu reconfigure your video?

---

### Post by Zach.Town on 2009-03-21
No, how would I go about doing that?

BTW I've had this problem every time i've used 8.10. A couple months ago I tried to dual boot it, same exact problem. Then I went to feisty fawn. Now I'm going entirely linux, no dual boot, and using intrepid but same problem again.

^if that means anything.

(atm I'm reformatting intrepid on again I'm going to select an older restricted driver as a friend recommended)

---

### Post by wjp.reg on 2009-03-21
should be listed as an option in /boot/grub/menu.lst and can be selected when you boot.

---

### Post by Zach.Town on 2009-03-22
I select xfix correct?

---

### Post by Zach.Town on 2009-03-22
Didn't work.

---

### Post by gali98 on 2009-03-22
Okay here is my suggestion... 
Get your system installed without enabling restricted drivers.
Then backup your xorg.conf by running this command (in the terminal... Applications->accessories->Terminal)
```
sudo cp /etc/X11/xorg.conf ~/xorg.bak
```
This will copy the conf to the file xorg.bak in your home folder...
Now if you try enabling restricted drivers and it messes up everything, there is no need to resinstall...
simply boot into recovery mode and choose the option about going to the command line
(I'm not sure on the exact option.. it may be something about a root shell...)
Anywho once you get there you just need to run the command:
```
sudo cp /home/yourusername/xorg.bak /etc/X11/xorg.conf
```
then restart and your video settings (actually all of Xserver settings...) will be restored and your system can live to fight another day... :)
Kory

---

### Post by Zach.Town on 2009-03-22
thanks :) that should help with finding out how to fix this whole thing... someone reccomended that I try using envy? I'm gonna give it a shot.

---

### Post by Zach.Town on 2009-03-22
this sound right to anybody?

[http://samiux.wordpress.com/2008/12/16/howto-avoid-to-drop-to-busybox-in-ubuntu-810/](http://samiux.wordpress.com/2008/12/16/howto-avoid-to-drop-to-busybox-in-ubuntu-810/)

---

### Post by gali98 on 2009-03-22
Envy always worked pretty good for me.
As far as those two methods, I say give it a shot...
It can't really hurt anything...
Kory

---

### Post by Zach.Town on 2009-03-22
Okay, well this is new

I tried restoring the xorg.conf using what you said and everything, it all worked perfectly. I rebooted and guess what BUSYfucknBOX. 

So maybe it isnt anything to do with the drivers / xorg / video...

any ideas?

---

### Post by stoogiebuncho on 2009-03-22
I had a similar problem with Nvidia restricted drivers.  I found this page to be of much help:
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia")

This is the part that fixed the black screen for me:
> Screen Blanks/Monitor Turns Off

Using a laptop with a GeForce Go card, or connecting the sole display via DVI on a dual-head system sometimes results in the screen not receiving a picture. This is caused by the driver outputting video to the VGA port on the graphics card, instead of DVI.

The usual hint that you have this problem is when you hear the startup sound but nothing appears on the screen. If you do not hear any sound, you are more than likely experiencing unrelated problems.

This is a launchpad bug about displays on digital outputs being blank when using NVIDIA binary driver, and can be resolved by editing your /etc/X11/xorg.conf file:

*

Switch to the console (Try using ctrl+alt+F1, or reboot and select recovery mode from the GRUB menu.)
*

Use your text editor to open /etc/X11/xorg.conf. (try sudo nano /etc/X11/xorg.conf)
*

Find the line that says Section "Screen"
*

Insert a new line that says Option "UseDisplayDevice" "DFP".
*

Save the file. If you had to restart into recovery mode, type reboot, otherwise restart your display using sudo /etc/init.d/gdm restart.

Then again, I don't think I ever got busybox, so maybe your problem is different, but it's worth a shot.

---

### Post by gali98 on 2009-03-22
Couple things.... First that xorg.conf trick will only work if you did it when your system was working... (i.e. before you ever enabled restricted drivers.)

Second, did you try typing exit at busybox like that website said? What happened?
If possible try uploading your current xorg.conf...
Kory

---

### Post by stoogiebuncho on 2009-03-22
> **gali98 said:**
> Couple things.... First that xorg.conf trick will only work if you did it when your system was working... (i.e. before you ever enabled restricted drivers.)
Kory

I actually did it after I enabled the restricted drivers.  
I enabled the restricted driver, rebooted, got the black screen, rebooted into recovery mode, dropped into root terminal, opened xorg.conf with nano, added the line, rebooted again and presto.

---

### Post by gali98 on 2009-03-22
lol... No no... That wasn't for you :)
That was directed towards Zach.Town...
Kory

---

### Post by Zach.Town on 2009-03-22
I made the backup when I had a working system. The exit thing didn't do anything except put my in busybox again.

---

### Post by gali98 on 2009-03-22
I see.
Have you tried the other option? (editing your grub.conf?)
You may need to boot into a live cd and edit the file there then reboot...
Kory

---

