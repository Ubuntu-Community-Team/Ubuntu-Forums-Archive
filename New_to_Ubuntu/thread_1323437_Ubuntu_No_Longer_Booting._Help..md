---
title: "Ubuntu No Longer Booting. Help."
date: 2009-11-11
forum: New to Ubuntu
---

### Post by wapayze on 2009-11-11
Hello,
I recently installed Ubuntu 9.10 using the wubi installer. I am also running vista. It was working a treat for one week and then when I started my computer up and selected Ubuntu I get the following up on screen.

[I]GNU GRUB version 1.97~ beta 4

[ Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device/file completions. ]

sh:grub>[/I]


Every command from the list offered with help and tab has failed to achieve anything. I've trawled the forums and google and tried previous suggestions like 'startx' and 'sudo fdisk -1' but these commands are not recognised. I must add that I am new to command lines and not very too clued-up.

Vista still boots up without any issues. 

Any assistance and guidance is much appreciated.

William.

---

### Post by OriginalName on 2009-11-13
Hi,

startx / fdisk won't work here as you've not yet booted to the operating system... and it looks like your using a beta version of grub (which could be why it's broken)... I'd recommend you do a reinstall making sure you've the latest version of Ubuntu... 

Just been reading on WUBI (I've not used it myself) and it seems to install ubuntu on the windows disk... so if you have altered any of the boot files on that drive when in windows that could have caused this...

---

### Post by lotharmat on 2009-11-13
That version of Grub is actually GRUB 2 (which is still in Beta) I'm not sure how to fix this though!

Somebody knowledgeable will, I'm sure, be along in a minute!

---

### Post by BinaryFeast on 2009-11-13
It would be useful to know if you have done any recent changes to your system, such as installed (or tried to install) drivers or edited any configuration files. If so, this can probably be fixed by using the command line tool you see when you start.

But first: Try to boot into safe mode (if you don't get a list of kernel boot options when you start, try to press ESC after you have chosen "Ubuntu" from the windows boot-loader menu).

Another option is to explore your previous installation by booting from an Ubuntu live-CD and diagnose it that way. 

These are all just some general approaches though, since I find it hard to tell what exactly has occurred here.

By the way: You haven't tried hibernate or sleep mode, have you? Because those are known to crash Ubuntu on wubi installations.

---

### Post by wapayze on 2009-11-13
Thanks for all the advice. I have reinstalled it again and now it is booting up properly.
I didn't intentionally install or adjust anything outside of apps in either ubuntu or vista so I'm not sure how I angered the computer gods. I'll see how it goes this time.

---

### Post by wapayze on 2009-12-05
It has happened again. Well it has happened twice to be exact. What occurs is that I install ubuntu using wubi and everything is dandy. Then I install all the updates and this is when the problem occurs. It is the exact same problem as I originally posted. I really like using ubuntu so I would love to be able to resolve this. If anyone is able to figure this out please inform. 
Cheers,
W.A.Payze

---

### Post by edu65 on 2009-12-05
Are you using the same language in Ubuntu as in Windows? I seem to remember there was a bug in Jaunty that produced the symptoms you describe when you installed Ubuntu using a different language. The bug may still be around. 

Cheers,
E.

---

### Post by Buuntu on 2009-12-05
Wubi isn't very reliable from my experience.  Unless you have a good reason I would suggest installing Ubuntu as a separate partition.  Just plop in a live CD, (you can get the ISO from here -> [http://www.ubuntu.com/GetUbuntu/download](http://www.ubuntu.com/GetUbuntu/download)) and the rest is self explanatory.

---

### Post by wapayze on 2009-12-06
Thank you for the advice. I'm not sure whether the languages match up so I can't say whether or not that is the problem. However, I've decided to uninstall wubi and go the partition method.
Regards,
W.A.Payze

---

