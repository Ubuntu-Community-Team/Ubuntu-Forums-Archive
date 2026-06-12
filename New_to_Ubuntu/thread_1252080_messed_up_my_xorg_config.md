---
title: "messed up my xorg config"
date: 2009-08-28
forum: New to Ubuntu
---

### Post by Zxeo on 2009-08-28
I just got Unbuntu today, never used it before. The first thing that annoyed me was that I couldn't right click and change the screen resolution to what I wanted (1920x1080). A quick google search and I found something that might  help me. I got pretty confused and typed something into the config then saved. After a restart I just get a blank screen with some red dots and green/purple lines at the top. I have NO idea how to do anything.

---

### Post by rifak on 2009-08-28
when you get to that screen, press ctrl-alt-f2. it will take you to a terminal. login, and do:
```
cd /etc/X11/
```
there you'll see your xorg.conf and any backup that was made when you edited that file. the backup should look something like 'xorg.conf.2938472928" you can rename that file to xorg.conf by
```
sudo mv xorg.conf.2938472928 xorg.conf
```
just be sure to make the numbers match to what yours is. then do 
```
sudo reboot
```
your comp will restart and you should have a working xorg

---

### Post by LewRockwell on 2009-08-28
and if you're a CLI virgin you can always reinstall

.

---

### Post by Zxeo on 2009-08-28
Thanks for the advice, but when I press ctrl alt f2 it does nothing. Still the same screen.
 
Haha I have no idea what CLI even is.

---

### Post by doas777 on 2009-08-28
cli is command line interface. most of the support you will find on these forums is done in command line, because everyones desktop is differant, and it's a real pain to spend half an hour croping images to embed, just to help someone with their problem.

first, what kind of video card do you have?
after getting your xorg fixed, the next step is to install a restricted driver for your card.
[http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide#Installing_the_restricted_drivers_.22the_Ubuntu_way.22](http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide#Installing_the_restricted_drivers_.22the_Ubuntu_way.22)

then hopefully you will have a GUI interface for configuring the card. GUI is Graphical User Interface (point with mouse and click. )

---

### Post by Zxeo on 2009-08-28
I know what a GUI is :P But thanks for the explanation of CLI.
 
I have a Radeon HD 4850 and I'm almost positive it has a GUI.

---

### Post by rifak on 2009-08-28
alright, well if you can't get to the cli at the crazy colored screen, try repeatedly pressing ctl-alt-f2 during startup. by doing this, im pretty sure you can start the cli even before the gui loads....correct me if im wrong

---

### Post by diablo75 on 2009-08-28
CLI stands for Command Line Interface.  Think of it as "Command Prompt" from Windows, or DOS.

Anyway, the quickest way to fix what you did is restore the file you edited from a previously backed up copy.  Chances are you did something to your xorg.conf file, which is automatically backed up in the same folder ("directory" as it's properly called).

When you first start your computer, you might see a "Starting GRUB.  Press ESC to something something" (I don't remember exactly but it's sort of  like pressing F8 before you boot into windows; we're going to be going into a sort of "Safe Mode" CLI environment).

What you want to do once you get that menu up is select the second item down in the menu which will have the words "(Recovery Mode)" at the end.  This will boot to a text menu, which you can use to drop to a command prompt.

From there, you'll want to type the command:

```
cd /etc/X11
```

And be sure to CAPITALIZE the X in X11; Linux is case-sensitive.  This will move you into the /etc/X11/ directory.  From there you can type in the command:

```
ls
```

ls is similar to "dir" in DOS.  It lists the files in the directory you are currently sitting in on screen.  You'll want to look for a file that is similar to the following name:  "xorg.conf.2938472928" as mentioned in the post above.  The numbers on the end represent a date and time of when the file (backup) was created.

Then you can use the move command to essentially overwrite the xorg.conf file that you modified with the backup copy:

```
sudo mv xorg.conf.2938472928 xorg.conf
```

The sudo (in this case) shouldn't be necessary, since you booted into recovery mode which takes you strait to a root prompt.

As mentioned above, if you find all of this too daunting, it might be easier to simply re-install the OS fresh.  Once you have the OS installed, you can return here to ask for advice from the forum about the best way to go about getting your monitor resolution to what you need/want it to be.

---

### Post by Zxeo on 2009-08-28
Yeah that didn't do anything either. It looked like it was working at first, but then it just loaded like usual. I get the splash screen saying Unbuntu and the loading bar, but then after that just the weird colors.
 
I'm just going to reinstall, seeing as how I didn't really DO anything that matters, then just do what doas777 said.
 
 
I will do this after I see if diablo75 way works.

---

### Post by win_soft2005 on 2009-08-28
What works for me is, just insert the liveCD, let the live system boot completely. Start the desktop(live system) and reboot in the installed Ubuntu system. Surprisingly this restored my xorg.conf(or at-least removed any conflicts). This trick worked for many distros.

---

### Post by philinux on 2009-08-28
> **Zxeo said:**
> I just got Unbuntu today, never used it before. The first thing that annoyed me was that I couldn't right click and change the screen resolution to what I wanted (1920x1080). A quick google search and I found something that might  help me. I got pretty confused and typed something into the config then saved. After a restart I just get a blank screen with some red dots and green/purple lines at the top. I have NO idea how to do anything.

Reboot. Press the esc key when grub appears. With the down arrow key choose the recovery mode option. Press enter. After a short while the recovery menu will appear. Choose xfix. When it has finished it's job choose resume normal boot.

---

