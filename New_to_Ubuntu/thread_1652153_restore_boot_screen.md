---
title: "restore boot screen"
date: 2010-12-24
forum: New to Ubuntu
---

### Post by rburkartjo on 2010-12-24
when a started system right before the login screen i had a screen that showed the kernels etc. somehow i lost this how can i enable again/tks

---

### Post by Quackers on 2010-12-24
On restarting the machine you're not getting the grub menu now?
How many operating systems are there on your machine?

---

### Post by rburkartjo on 2010-12-24
qua only one. no idea how i did it. but sure there is a way to fix

---

### Post by ajgreeny on 2010-12-24
If you only have one OS the grub menu is hidden by default.  When you need it press **shift** at boot and it should appear.

If you want it to appear always you will need to edit /etc/default/grub, see below for details.

**GRUB_HIDDEN_TIMEOUT=0**   [ [COLOR=DarkRed]Note: This setting only applies to computers with only a single operating system.[/COLOR] ]
[LIST]
[*]The  hidden timeout option allows a screen to be displayed without the Grub 2  menu, awaiting input from the user for a given number of seconds. It is  available to single-OS computers - if multiple OS's are known to Grub  2, this option is bypassed. 
**On single-OS computers:**
[LIST]
[*]The menu will be hidden unless the  user adds a # symbol to the beginning of this line ( #  GRUB_HIDDEN_TIMEOUT=0 ) and the GRUB_TIMEOUT value is greater than 0.
[*]If a background image is designated in 05_debian_theme it will be  displayed rather than a blank screen during a hidden menu timeout.
[*]**For integers greater than 0**:
[LIST]
[*]The system will pause without displaying a menu for the designated number of seconds. If the user does not press the *SHIFT* key during the timeout the system will then boot the default OS/kernel.
[*]If the user presses the *SHIFT* key to display the menu, the  menu will be displayed for the number of seconds designated by the   GRUB_TIMEOUT value unless the user again intervenes.
[/LIST]
 
[*]With a value of **0**:
[LIST]
[*]Unless the user intervenes, the system will boot the default OS/kernel with only a slight delay. No menu will be displayed.
[*]The user may force displaying the menu as the computer boots by holding down the *SHIFT*  key.
[/LIST]
[/LIST]
[/LIST]
See [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275) for lots of detail on grub2, a great post by dfrs305 that I have used a lot.

---

### Post by Quackers on 2010-12-24
I don't know why it suddenly disappeared unless you've recently got rid of an OS and since run update-grub, maybe.
ajgreeny has the details :-)

---

### Post by rburkartjo on 2010-12-24
yea i installed kubuntu to try it out and that is when the problem started

note ref this link

[http://linuxmini.blogspot.com/2007/10/restore-grub-in-ubuntu-if-your-mbr-is.html](http://linuxmini.blogspot.com/2007/10/restore-grub-in-ubuntu-if-your-mbr-is.html)

i  did as advised however ref step 4 when i typed in find /boot/grub/stage1 nothing was recongized

---

### Post by rburkartjo on 2010-12-24
going  to try what ajg suggested

---

### Post by rburkartjo on 2010-12-24
ajg navigated  to   /etc/default/grub

no grub file was there

---

### Post by rburkartjo on 2010-12-24
if i hold the shift key down at startup the grub menu does show up though

---

### Post by rburkartjo on 2010-12-24
any help would be appreciated. i know there is a way to fix (did it about 2 years ago-when i had a similar problem but lost the bookmark). tks

---

### Post by Quackers on 2010-12-24
I'm sure that the file grub must exist in /etc/default because I don't think you could boot without it.
Edit using ```
gksu gedit /etc/default/grub
```

---

### Post by rburkartjo on 2010-12-24
thank you got it fixed

---

### Post by Quackers on 2010-12-24
Excellent :-)

---

