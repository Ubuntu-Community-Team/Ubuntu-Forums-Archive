---
title: "Remove a bad graphics driver"
date: 2010-08-16
forum: New to Ubuntu
---

### Post by Errandir on 2010-08-16
Okay, so I'm new to Ubuntu - I just set it up today (dual-booting with Windows 7). But while I was setting things up, I installed a bad ATI driver. I did a google search, and it's the same problem people had [here]("http://ubuntuforums.org/showthread.php?t=1337717") and [here]("http://ubuntuforums.org/showthread.php?t=1434119"): to sum up, after rebooting and trying to start up Ubuntu, the screen goes black and stays that way.

Problem is, all the solutions suggested in the other threads need the command prompt, and I can't bring it up. Pressing ctrl+alt+F1 after the screen goes black won't do anything, in regular or in recovery mode. In regular, the screen goes black right after I select it from the boot menu, and in recovery there are some lines of code and then it goes black, but it's the same after that. Also, if I press the power button while the screen is black, the Ubuntu loading screen will pop up and it powers down normally (which I thought was kinda strange), but that only works in regular mode.

Anyway, if anyone thinks they know how to fix it, that would be great.

---

### Post by Errandir on 2010-08-17
Bump. 

I guess I can wipe the Ubuntu partition and re-install, but I'd rather not unless I have to. Maybe I can boot up the install CD and delete the bad driver files? Wouldn't know where to find them, though...

---

### Post by Errandir on 2010-08-18
Anyone? I'm sorry for bumping this again, but it's been a while now and I've had no luck figuring it out on my own. Should I just wipe the partition and re-install lucid?

---

### Post by stlsaint on 2010-08-18
This is only to get you back to your desktop, then maybe you can fix the ati issue:
1. Boot to the live cd
2. in terminal enter:
```
 cd /etc/X11 
```
NOTE: You can do all this via the graphical interface if its easier!
3. make a copy of your xorg.conf and title it: xorg.conf.bak
or in terminal run command:
```
 cp xorg.conf xorg.conf.bak 
```
4. reboot the system and boot into ubuntu.

This will create a new xorg.conf after you reboot and you will be using generic drivers instead of the ati one. From there install the correct driver.

---

### Post by Zorgoth on 2010-08-18
Ummmmmmmm by cp do you mean mv?

---

### Post by Paul820 on 2010-08-18
> Ummmmmmmm by cp do you mean mv?
No, he's making a copy of his xorg.conf file after cd'ing to the directory.

---

### Post by Zorgoth on 2010-08-18
I can see that that's what he is doing - but the old xorg.conf is still there and called xorg.conf, so why would the system create a new one?

---

### Post by Errandir on 2010-08-18
Thanks for the comments. Still didn't work, though - when I try the second command in the terminal, it tells me that xorg.conf isn't in the working directory ([here's]("http://img12.imageshack.us/img12/3839/terminalb.png") a terminal screenshot). Do you know why?

---

