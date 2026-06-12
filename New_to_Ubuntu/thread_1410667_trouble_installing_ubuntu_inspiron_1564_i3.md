---
title: "trouble installing ubuntu inspiron 1564 i3"
date: 2010-02-19
forum: New to Ubuntu
---

### Post by ramsus88 on 2010-02-19
Hey, I've been trying to install Ubuntu on my new Dell laptop but each time I can get to the point where I have a choice at startup between Windows 7 and Ubuntu.  The trouble is, after selecting Ubuntu it shows a couple lines about finishing installation and then goes to a completely black screen.  My harddrive light shows it working for a while but soon that goes off as well and I just have to power down.  I can press esc after selecting ubuntu to choose a mode for booting but those don't seem to help either.

I tried installing through wubi and I also tried partitioning and using a burned dvd but both had the same problem

From what I've read online it might be my processor, Intel core i3 m330 but I'm not sure and I really hope that's not the case

Does someone know whats wrong or how to work around it? or is there another version of Linux i might be able to install?

thanks

---

### Post by Sef on 2010-02-19
How well does the LIve CD work?

---

### Post by darkerlink on 2010-02-19
> **ramsus88 said:**
> Hey, I've been trying to install Ubuntu on my new Dell laptop but each time I can get to the point where I have a choice at startup between Windows 7 and Ubuntu.  The trouble is, after selecting Ubuntu it shows a couple lines about finishing installation and then goes to a completely black screen.  My harddrive light shows it working for a while but soon that goes off as well and I just have to power down.  I can press esc after selecting ubuntu to choose a mode for booting but those don't seem to help either.

I tried installing through wubi and I also tried partitioning and using a burned dvd but both had the same problem

From what I've read online it might be my processor, Intel core i3 m330 but I'm not sure and I really hope that's not the case

Does someone know whats wrong or how to work around it? or is there another version of Linux i might be able to install?

thanks

I have the inspiron i5 that I've also had trouble installing. You have to log in with "safe graphics mode". There should be an option when you boot and choose either windows or ubuntu. You may want to wait before you install karmic. I've install karmic and Im having some trouble with the intel GMA HD driver. 

[http://ohioloco.ubuntuforums.org/showthread.php?p=8799407#post8799407](http://ohioloco.ubuntuforums.org/showthread.php?p=8799407#post8799407)

Follow my thread above to read more.

TLDR version: No recent intel support for GMA HD until Lucid Lynx.... MAYBE!

---

### Post by teh603 on 2010-02-26
Fellow i3 purchaser here, having the same problem. Jaunty 64 boots but the video chipset is totally unsupported (I get a screwy stretched version of 1024x768 ). Karmic i386 gives me a black screen of doom. Lucid i386 (a2) seems to boot but freezes. I'm going to be testing it a little more.

I'm downloading Karmic 64 as I edit his.

Edit: Karmic 64 also gives me the black screen of death unless I boot in safe video mode, which also gives me the stretched version of 1024x768.

Guess we need to wait for the final version of Lucid?

Edit again: Lucid A3 seems to work a lot better, althoug it still seems to freeze from time to time. Disable compiz for teh win?

---

### Post by ramsus88 on 2010-03-02
Hey thanks for the responses.

I got the LiveCD to work in Safe Graphics mode but when I tried to install it and run in safe graphics mode I got the same problem

This is my first time trying to use any Linux build so what are Lucid and Karmic?  Do you suggest I try Lucid A3 if that seems to work.

I didn't quite understand what you were trying in the i5 topic, is there a custom driver I could install to get it atleast to the desktop?  I only need Ubuntu for some languages we're going to use in class (3pi and Pololu and Lush for robotics) so I don't need a lot out of my ubuntu install, just compiling, editing, and uploading code to robots.

if you need more information on my computer I'd be glad to post it

---

### Post by teh603 on 2010-03-02
Lucid is 9.10, the current version. Karmic is 10.04, which is currently in the Alpha 3 phase. Its due out in about two months.

Supposedly, you can download and build a driver from the X.org "edgers" repositories, but that's beyond my experience level. Installing Lucid was an easier solution, even if it is unstable.

---

