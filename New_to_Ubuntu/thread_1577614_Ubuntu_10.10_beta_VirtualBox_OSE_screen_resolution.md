---
title: "Ubuntu 10.10 beta VirtualBox OSE screen resolution"
date: 2010-09-19
forum: New to Ubuntu
---

### Post by men28 on 2010-09-19
Hi

I have installed Ubuntu 10.10 Beta in a VirtualBox OSE virtual machine.

But screen resolution is very low - 800x600.

When I choose
System > Preferences > Monitor
there are only two possible screen resolutions: 800x600 and 640x480.

When I try to install VirtualBox Guest Additions they just don't work or there is garbage on the screen and the virtual machine hangs.

How can I use higher screen resolution inside the VirtualBox OSE without guest additions?

I need this for development. It's a little bit difficult to develop something with 800x600 screen resolution.

Thanks for help.

---

### Post by howefield on 2010-09-19
Have a browse/search at the Virtualbox forums, there is a known issue with Guest Additions and Maverick, with a test release of GA available, but bear in mind it is a test release.

[http://forums.virtualbox.org/viewtopic.php?f=3&t=33645&start=0](http://forums.virtualbox.org/viewtopic.php?f=3&t=33645&start=0)

---

### Post by men28 on 2010-09-19
Thank you, howefield!

The link was very useful.

I have installed a package virtualbox-ose-guest-x11 and this solved the screen resolution problem.

---

### Post by howefield on 2010-09-19
Excellent, I'm glad you fixed the issue.

---

### Post by CookieNinja on 2010-09-23
Awesome! Solved my problem, too. I had been quietly accepting the limitations of VBox until I saw this solution elsewhere.

God bless the Ubuntu community for working this out and spreading the good news around!

ps. why doesn't my Ubuntu-packaged Firefox recognise either Ubuntu or Firefox in it's dictionary :-O Shame on the maintainers!

---

### Post by Image0fman on 2010-10-08
Completely awesome and fixes this issue, if your having problems running the command try updating first (apt-get update)

Thank!

---

### Post by fizzfoam on 2010-11-07
Doubly awesome, this fixed mine too!  I had the same resolution problem with Linux Mint 10 RC.  I just installed package 
virtualbox-ose-guest-x11, 
inside the virtual Mint machine, rebooted Mint, and this solved the screen resolution problem.

Thanks guys!

---

### Post by John.Bus on 2011-12-03
It's an old thread but still useful.  I wanted to get away from Windows OS as I have been having all kinds of problems with win7 64bit on my asus intel core I5 with nvidia geforce 360m 1gb.

I didn't realize netflix didn't stream to nix based systems, so I found the VBOSE solution.  Just needed to do one quick search on "virtualbox ose and screen resolution" to find this thread. 

Nice smooth fix, no unexpected crap.  Very please to have all this going good in less than 24 hours.  

Thanks to the community at large and to the dedicated developers for a superior alternative. 

I look forward to participating in the future.

---

