---
title: "how to uninstall ubuntu 9.10 to get it working"
date: 2010-03-12
forum: New to Ubuntu
---

### Post by Contra75 on 2010-03-12
I installed 9.10 on my Dell laptop as it was sitting in the corner for a year or so. First 3 days was a bliss - I enjoyed new OS and all I could do in it. Then on 3rd day I decided to hook it to my HDTV to watch some internet TV on a larger screen. As I was trying to figure out the set-up for dual monitors, Ubuntu crashed and now it is not booting.
I read posts here and tried to startx from the recovery mode but that did nothing and did not get me into that mice graphical OS. 

At this point I am really annoyed and would prefer to uninstall ubuntu all together and then start from the scratch. How do I do it? 
I tried to remove it from Windows Add/Remove Prog and I got the message that it was uninstalled - but that is not true: 1) when I start up I am in GRUB and got 4 kinds of Ubuntu (2 of which are recovery modes of the other 2??), 2) even after I pick Windows I still get to pick between Windos and Ubuntu for the second time, 3) if I pick Ubuntu at this second gate it tells me that some dll file is missing. BTW, is this "second gate" normal or does it mean that I installed Ubuntu twice - as a partition (Windows space did shrink after installation of 9.10) and within Windows??

---

### Post by baddnady23 on 2010-03-12
Ubuntu is not a program that is uninstallable, like photoshop for example.  It is an Operating System which is in a whole different league.  To reinstall, simply make a live disk or use the one which you installed with in the first place and boot your computer up from it, and follow the instructions to install.  Just be sure to put it back on the partition which you installed ubuntu in the first place and not on the windows one.

Unless you installed ubuntu with the WUBI, then you did not install it within windows itself. Good Luck!

---

### Post by Contra75 on 2010-03-12
How do I boot my comp from live CD? (I know I am a nub)
When I put in in the drive and restart I get into GRUB. So I guess I got to start Windows, insert the CD and then install it again? 

Repeating my other Q: is the 2 gates of picking Windows normal on double boot?

---

### Post by baddnady23 on 2010-03-12
You'll need to tell your computer to boot from a cd since it sounds like it doesn't automatically default to that.  Put the CD in, restart the computer and when ti BIOS is booting, it should briefly say at the bottom of the screen hit "F12" or "F[something]" to bring up the boot menu.  When that shows us, select to boot from the CD drive and it will go into the main menu for the ubuntu live cd.  From there, you can select to install right away, or boot into the live cd OS and you can install it from there.  As always, i highly recommend backing up important windows files just in case something goes horible wrong during the install.  But it's pretty easy as long as you pay attention and follow the instructions.  

I'm not sure what you mean by "2 gates".  

Feel free to come back for more help!

---

### Post by Contra75 on 2010-03-13
For those who run dual boot - if you want to run windows do you have to pick it twice? First in grub and then again? Is that just me? 

If I am screwed - how can I fix it?

---

### Post by baddnady23 on 2010-03-13
I've never had to pick twice... If I want it, I select it from the GRUB menu.  Unfortunitly I can't help you on this one... Anyone else???

---

### Post by seenthelite on 2010-03-13
The 2 gates of picking windows is probably your windows partition and your recovery partition you can only use the windows partition.

---

### Post by Contra75 on 2010-03-15
I figured why I was had to pick windows twice on boot and this is totally my fault. 
I installed ubuntu as a double boot. However before that I tried to install it from windows to play within windows - even though I quitted and never finished the installation it apparently made some record and whenever I wanted to pick windows from my double boot I had to first pick it in Grub, and then (being already in windows boot) pick windows again. I even uninstalled ubuntu from windows (control panel-> add prog), but I guess because I already had installed it as double boot it was still causing me that 2nd gate.

---

