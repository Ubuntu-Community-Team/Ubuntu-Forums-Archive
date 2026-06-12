---
title: "Screen resolution and sound issues...."
date: 2009-05-16
forum: New to Ubuntu
---

### Post by jtbrookreson on 2009-05-16
Ok, first of all, I want to send out my apologies. I was running Ubuntu 6.06 on this G3 iBook 500 256 RAM for over a year, but the lack of speed just got to me. I tried upgrading to Xubuntu 9.04, and came up with 1) Screen resolution issues (stuck with 800x600, and could not get 1024x768) 2) No sound device detected (while with 6.06 I had both perfect screen resolution and sound), 3) though faster, still slow, and a bit choppy. So on someone's suggestion, I installed Debian 5.0 Lenny, and am much happier....Except I still have resolution and sound issues. I have gone to the Linux and Debain Forums for help with  this matter, but there was non offered. So I return to the Ubuntu Forums for help because a) I always got some sort of help here, with people being very friendly and patient b) I am am a total Noob when it comes to running script commands, and c) this is my only machine, and after tasting the better and faster life, I don't want to go back to a dead system like 6.06. I know its like going to an ex-girlfriend about relationship problems with the current girlfriend, but this is the only forum I know of that has ever helped me. Thanks in advance....

-JTB

---

### Post by NHArticleTen on 2009-05-16
[http://www.debian.org/releases/stable/powerpc/](http://www.debian.org/releases/stable/powerpc/)

---

### Post by jtbrookreson on 2009-05-16
Thank you for the link. I am sure that I will need to use it for something in the future, but I can't seem to find my problem here. Everything is installed, and I know I just need to reconfigure my X11, or Xorg, or something or other (I am still getting used to Linuxspeak, despite a year of usung Ubuntu)... I can't find how to do that in Debian, nor what my reconfig should look like...

I understand the theory, but it is the exicution that is killing me. Thanks again.

-JTB

---

### Post by jtbrookreson on 2009-05-16
ok... I found this thread...

[http://www.linuxquestions.org/questions/linux-newbie-8/display-error-dpkg-reconfigure-not-working-706495/](http://www.linuxquestions.org/questions/linux-newbie-8/display-error-dpkg-reconfigure-not-working-706495/)

And it looks like the solution (for the screen problem at least). But what it does not say is how to actually do the editing. Again, I am a total Noob, so if someone can walk me through it step by step, I will be the happiest (and a bit of a lesser) Noob in the world...

Thanks in advance...
-JTB

---

### Post by CatKiller on 2009-05-16
> **jtbrookreson said:**
> Screen resolution issues (stuck with 800x600, and could not get 1024x768

Normally, resolution problems are caused by one of the monitor, the graphics card, or the graphics driver not passing the EDID information to X that lets it automatically set the correct refresh rate, and so it defaults to really low values that won't damage any monitors. You can manually set the values for your monitor by putting the VertRefresh and HorizSync ranges in your xorg.conf. You should be able to get these numbers from the manual or specifications for your monitor. These values go in the "Monitor" Section of xorg.conf.

You can edit xorg.conf with ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
gksudo gedit /etc/X11/xorg.conf
``````
Section "Monitor"
        Identifier      "Configured Monitor"
        HorizSync       aa-bb
        VertRefresh     cc-dd
EndSection

```You'll need to replace aa-dd with the values for **your** monitor.

---

