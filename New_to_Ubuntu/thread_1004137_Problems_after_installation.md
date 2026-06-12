---
title: "Problems after installation"
date: 2008-12-06
forum: New to Ubuntu
---

### Post by bettina on 2008-12-06
I just installed Ubuntu 8.10 into an 3 year old dell dimensions desk top.  I am pretty sure the file downloaded without any problems and the cd burned correctly. I did the cd check and the system check that are options on the initial screen and both came back clear.  I completely wrote over the existing Microsoft XP OS (and everything else) that was originally on the desktop.  After the installation I entered the username and password, but after that the screen remained beige and empty.  I restarted and the system booted up with the Linux, I went through the log in steps and again I only got a beige empty screen. 

Any idea's what could be causing this?  Is it a hardware issue?  I have attached a list of the desktop config from dell.

---

### Post by falcon61102 on 2008-12-06
Seems that a few people have had similar problems lately and many of them are stemming from Compiz and/or the graphics card.  

If you are able to login through the Failsafe GNOME, you could disable compiz with:
```
metacity --replace
```
Which would load metacity, a more basic window manager.

When you get to the login screen, select Options and then Select Session.  Select Failsafe GNOME from there.

If switching the window manager, you could try removing Compiz completely with:
```
sudo apt-get remove compiz compiz
sudo apt-get remove compiz compiz-core
```

To do this, go back to the Select Session menu and select Failsafe Terminal and then run those commands.  Restart and see if things are better.

If all that doesn't work, then it's more likely a hardware issue that will have to be resolved, possibly with some new drivers but I would recommend trying that because it will be the easiest two fixes right now.

---

### Post by NewJack on 2008-12-06
After downloading the .iso file, did you check the MD5 Hash of the file?  That should always be step one after downloading an image.  This way you make sure the file integrity is intact.  

If you don't know how to, here is a help page explaining how to do an MD5checksum:  [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Also, when you burned the CD, what speed did you burn it at?  Rule of thumb is, the slower the better.  I alway burn the .iso's at x4 or x6 speed without a problem, ever.  

I would try the above and then try reinstalling Ubuntu.

Good luck!

---

### Post by mtinman on 2008-12-07
Bettina, the file you attached appears to be an internal parts list from Dell. Please post your Dell Dimension model number in reply.

From what you describe, it appears to be some kind of problem with the X server, which is what makes the graphical user interface (aka X11, or X Windows) possible.

This may take some time and effort to fix, and you will want to have internet access via another computer while you fix it, so you can access help files & such.

You will probably end up having to change some configuration files via the command line before all is said and done.

---

### Post by bettina on 2008-12-07
Thank you everyone for your help.

Mtinman - The desktop is a dell dimensions 2400.

NewJack - I did not check the MD5 hash because the cd was working fine on my laptop.  So I reinstalled and created a new cd completing all the checks successfully and writing @ 4x.  Now this cd will get me to the main menu at boot up but does nothing when i select any of the menu options.

Falcon61102 - When I select the failsafe GNOME option I get the same empty beige screen.  When I select the failsafe terminal option i get a box with text.  I am guessing I should not erase compiz completely if i could not perform the first step, loading metacity.

Thank you again!

---

### Post by mtinman on 2008-12-07
bettina: check this forum post, I think it will have the answer you seek...

[http://ubuntuforums.org/showthread.php?t=483341](http://ubuntuforums.org/showthread.php?t=483341)

---

### Post by falcon61102 on 2008-12-07
You can try the metacity --replace code in the Failsafe Terminal.  And if not, you can remove compiz and the GNOME will automatically switch over to metacity.  So either way.

---

### Post by abn91c on 2008-12-07
> **bettina said:**
> Thank you everyone for your help.

Mtinman - The desktop is a dell dimensions 2400.

NewJack - I did not check the MD5 hash because the cd was working fine on my laptop.  So I reinstalled and created a new cd completing all the checks successfully and writing @ 4x.  Now this cd will get me to the main menu at boot up but does nothing when i select any of the menu options.

Falcon61102 - When I select the failsafe GNOME option I get the same empty beige screen.  When I select the failsafe terminal option i get a box with text.  I am guessing I should not erase compiz completely if i could not perform the first step, loading metacity.

Thank you again!
I havethe same dell PC it has a intel 845 series video card there is a ubuntu/kubuntu  bug in the driver, follow the above instructions to remove compiz and you will be able to use in my case kubuntu with no desktop effects.
try ctr+alt+f1 then in the terminal do first dhclient eth0 to get access to your network then sudo apt-get remove compiz compiz followed by
sudo apt-get remove compiz compiz-core

---

### Post by bettina on 2008-12-15
Thank you everyone for your help.  I removed compiz using the codes provided and now i am able to log in and everything seems to be running ok!

Thanks again!

---

### Post by falcon61102 on 2008-12-16
No Problem.  Glad you got it running.

---

