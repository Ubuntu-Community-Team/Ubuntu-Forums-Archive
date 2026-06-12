---
title: "I'm in over my head"
date: 2010-08-09
forum: New to Ubuntu
---

### Post by jjcnc82 on 2010-08-09
Hello!
 
I've recently acquired an old Toshiba laptop from a friend, and I am attempting to install ubuntu 10.04 on it. I was met with resistance from the start because of the old intel video chip installed on it. When i would try the install from the live cd, it would get to the ubuntu splash screen and then just go black and sit there. After a lot of researching, i overcame that problem by editing the boot parameter. I added "i915.modeset=1" or something like that. SO anyway, i got it installed, but now whenever i try to load the OS, i believe im hitting the same problem because it is still attempting to boot without the use of that special parameter...so again...boot to black after splash screen.
 
So here's what I am seeking. I am 100% linux illiterate. I have no idea how to do anything outside of a GUI...I do know that somehow i have to get to a boot menu before the thing loads. Ive also read that in order to get to the grub2 menu, you press and hold shift in order to do that. For some reason though, that does not go to any sort of menu...it just continues to boot to black. 
 
Anyway bottom line is, i need to add the line "i915.modeset=1" to the boot sequence so that every time ubuntu boots, it follows that parameter. Please don't assume that i know how to accomplish anything on a  command line because i definatley do not. Please spell it out like you're talking to a 5 year old. =D (used windows for far too long)
 
Any assistance would be greatly appreciated!

---

### Post by Bachstelze on 2010-08-09
Hold the Shift key at boot, you will get a menu with some "Ubuntu" and "Memory test" entries. Press 'e' to edit the first entry. Add your boot parameter at the end of the line that starts with "linux" (normally it ends with "quiet", add it after that), and press Ctrl+X to boot.

See if it works. If it does, we'll add it permanently so you don't have to do that every time.

---

### Post by Peter09 on 2010-08-09
Here is a thread where someone asked a very similar question, the second reply gives you the steps to do what you want.
 
Don't be afraid of the terminal its not as bad as you think. By the way if you make a typo using the terminal use the up arrow to get to the command again and then the arrow keys and delete key to correct the problem.
 
[http://ubuntuforums.org/showthread.php?t=1470191](http://ubuntuforums.org/showthread.php?t=1470191)

---

### Post by jjcnc82 on 2010-08-09
Gonna poke around the gui to see if i can solve this...will post within the hour if i get stuck

---

### Post by Peter09 on 2010-08-09
From the thread I linked above
 
> [SIZE=2]- Once logged in, you can edit grub; in a terminal (Applications-->Accessories-->Terminal), type:

gksudo gedit /etc/default/grub

- There should be a line:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

- add your parameters there (between the quotes). Save, and exit the editor. Then run:

sudo update-grub

- to update grub. Reboot. If you suspect something's wrong or if something's unclear, don't edit anything yet, but ask here instead. Good luck.[/SIZE]
[IMG]http://ubuntuforums.org/images/statusicon/user_offline.gif[/IMG] [[IMG]http://ubuntuforums.org/images/buttons/report.gif[/IMG]]("http://ubuntuforums.org/report.php?p=9221365")   

---

### Post by arochester on 2010-08-09
See "Intel 82830 CGC (830m) graphics fix for Ubuntu Lucid 10.04 just might work for your Intel video chip, too" - [http://www.insidesocal.com/click/2010/02/intel-82830-cgc-830m-graphics.html](http://www.insidesocal.com/click/2010/02/intel-82830-cgc-830m-graphics.html)

---

### Post by Jerry N on 2010-08-09
How old is your Toshiba?  I have a 1999 Toshiba laptop that so far has refused to run any Linux live CD that I have tried, although I haven't tried the latest version of Puppy yet.  It also refuses to upgrade from Win98SE to Windows 2000.

Jerry

---

### Post by jjcnc82 on 2010-08-09
Great advice guys...everything is booting up just as it should be now. This was all way simpler than i thought!

---

### Post by jjcnc82 on 2010-08-09
To be honest with you jerry, i dont even know. A friend gave me this thing a few days ago because they said it wouldnt boot up anymore. I don't know how long they had it, but i can tell you the system specs, that might give you some idea:
 
1.4ghz processor
200mb of ram
70gb hard drive
 
Hope that helps!
 
I have read that older laptops specifically the Toshibas have troubles with linux systems. My issue was just the old video chip not being compatible. That obviously can be fixed though.

---

### Post by ajgreeny on 2010-08-09
If the ram is still only 200MB the system will probably run horrendously slowly, amd you might come to a full stop in the installation as well.  You really need an absolute minimum of 512MB for gnome desktop versions of ubuntu.  If you do manage to get it installed you might like to look at **lxde** as an alternate desktop environment, which is much quicker on older machines and uses less ram.

Look for **lxde** in synaptic and see what you think.

---

### Post by Jerry N on 2010-08-09
> **jjcnc82 said:**
> To be honest with you jerry, i dont even know. A friend gave me this thing a few days ago because they said it wouldnt boot up anymore. I don't know how long they had it, but i can tell you the system specs, that might give you some idea:
 
1.4ghz processor
200mb of ram
70gb hard drive
 
Hope that helps!
 
I have read that older laptops specifically the Toshibas have troubles with linux systems. My issue was just the old video chip not being compatible. That obviously can be fixed though.

That is much more modern than my old Toshiba so none of my Toshiba experiences would be applicable to your situation.  200mb RAM is an awfully low amount though.

Jerry

---

### Post by anewguy on 2010-08-09
+1 on the low memory.  I also noted you said 200mb of memory - that normally isn't an amount you'd see.  Usually it would be (starting with older first since it's an "older" PC) things like 64mb, 128mg, 256mb, 512mb, etc. - increments of 64.  I would check for the model number on the PC itself, then check the net to see what memory options are available for it.

Dave

---

### Post by linux18 on 2010-08-09
> **ajgreeny said:**
> If the ram is still only 200MB the system will probably run horrendously slowly, amd you might come to a full stop in the installation as well.  You really need an absolute minimum of 512MB for gnome desktop versions of ubuntu.  If you do manage to get it installed you might like to look at **lxde** as an alternate desktop environment, which is much quicker on older machines and uses less ram.

Look for **lxde** in synaptic and see what you think.
I've managed to run gnome in 80MB of ram using my custom super-fast distro (see sig). @jjcnc82 once you get more ubuntu experience you should check out my distro as well, you can get fluxbox in 60MB of ram so lxde in 200MB will be faster than win7 on a modern computer.

---

