---
title: "Problems with new install of Lubuntu"
date: 2010-08-04
forum: New to Ubuntu
---

### Post by crybllrd on 2010-08-04
I just installed Lubuntu on my old laptop, but when it loads I just get a black screen and a mouse. I can move the mouse, but cant do anything else. A screensaver will eventually come on.
 
Also when I restart it it just goes to memtest. I cant seem to boot it into the operating system. the only way I can get in to the OS is to use the "Try lubuntu without installing" option. After the first install it did load, but just to the blank screen.
 
Can anyone help with either of my problems?

---

### Post by linux18 on 2010-08-04
-choose recovery mode at grub
-drop to a root prompt 
-type "telinit 3" and logon
-type "xinit" 
-after it loads type "openbox &" (you may need to wiggle the mouse before it registers)
-then type "lxpanel & xfdesktop & nm-applet &"
your good to go! a reboot will take you back into the normal DE

---

### Post by crybllrd on 2010-08-04
Well, I installed Ubuntu 7.10 before, and it wouldn't run. On this forum it was diagnosed as my machine being too old and not powerful enough to run it.
 
So when I push Esc to enter GRUB, I see Ubuntu 7.10 but no Lubuntu.
 
How can I do this, or am I doing it wrong? Im new to LINUX

---

### Post by linux18 on 2010-08-04
> **crybllrd said:**
> Well, I installed Ubuntu 7.10 before, and it wouldn't run. On this forum it was diagnosed as my machine being too old and not powerful enough to run it.
 
So when I push Esc to enter GRUB, I see Ubuntu 7.10 but no Lubuntu.
 
How can I do this, or am I doing it wrong? Im new to LINUX
it will say ubuntu when it really is lubuntu.

---

### Post by crybllrd on 2010-08-04
I dont see a recovery mode.  When I press Esc for GRUB, My only options are 'e to edit commands before booting' or 'c for a comand-line'

---

### Post by crybllrd on 2010-08-04
And my Lubuntu is 10.4, but Ubuntu 7.10 is the only one showing up

---

### Post by snowpine on 2010-08-04
It sounds like the Lubuntu install failed and Ubuntu 7.10 is still installed. Can you run the Lubuntu Live CD in "live" mode with no change to your computer? Have you used the "check CD for defects" option to verify the burn? What are the specs of your computer (processor, RAM, video card, etc)?

---

### Post by crybllrd on 2010-08-04
Oh, i did have a couple of errors. 
Should I re burn it with the same ISO, or get  a new one? If so, where can I get a reliable ISO?

---

### Post by snowpine on 2010-08-04
> **crybllrd said:**
> Oh, i did have a couple of errors. 
Should I re burn it with the same ISO, or get  a new one? If so, where can I get a reliable ISO?

You can check the integrity of an ISO following these instructions: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

The most reliable way to download is by using a torrent; torrent clients check the md5sum automatically.

---

