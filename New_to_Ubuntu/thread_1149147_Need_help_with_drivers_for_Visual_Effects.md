---
title: "Need help with drivers for Visual Effects"
date: 2009-05-04
forum: New to Ubuntu
---

### Post by Robbie7up on 2009-05-04
I just out ubuntu onto my laptop, a IBM Thinkpad T40, and want to turn on some of the cooler visual effexts I have seen my friends use and that I have seen in demonstrations.  When I try to turn the visual effects on normal or extra it said they could not be turned on.  I believe this is because I need some drivers.  Where exactly can I get the drivers for Ubuntu on the IBM Thinkpad T40.

---

### Post by Svensk023 on 2009-05-04
start by checking System > Administration > Hardware Drivers

---

### Post by Robbie7up on 2009-05-04
> **Svensk023 said:**
> start by checking System > Administration > Hardware Drivers
It says no drivers are in use on this system.  How and where do i get them?

---

### Post by wiznillyp on 2009-05-04
Do you have an Intel VGA?  If you do, follow the instructions in this thread for a solution:

[http://ubuntuforums.org/showthread.php?t=1136738](http://ubuntuforums.org/showthread.php?t=1136738)

---

### Post by Robbie7up on 2009-05-04
> **wiznillyp said:**
> Do you have an Intel VGA?  If you do, follow the instructions in this thread for a solution:

[http://ubuntuforums.org/showthread.php?t=1136738](http://ubuntuforums.org/showthread.php?t=1136738)
That is really complicated.I am smart with computers but I am brand new to Ubuntu, so I need some help figuring out what all that means.

---

### Post by wiznillyp on 2009-05-04
> **Robbie7up said:**
> That is really complicated.I am smart with computers but I am brand new to Ubuntu, so I need some help figuring out what all that means.First of all, do you have an Intel VGA?

Or, better yet, read this thread my friend: [http://ubuntuforums.org/showthread.php?t=799070](http://ubuntuforums.org/showthread.php?t=799070)

---

### Post by Robbie7up on 2009-05-05
> **wiznillyp said:**
> First of all, do you have an Intel VGA?

Or, better yet, read this thread my friend: [http://ubuntuforums.org/showthread.php?t=799070](http://ubuntuforums.org/showthread.php?t=799070)
I am still lost, do I input the codes from the thread into terminal,or where?

---

### Post by louieb on 2009-05-05
Visual effects did not work on my T30 until I installed Jaunty. You probably have ATI radon graphics.  Specs for most thinkpads can be found at [ThinkWiki - Linux on ThinkPad]("http://thinkwiki.org/wiki/ThinkWiki")  

Which version of Ubuntu did you install?

---

### Post by wiznillyp on 2009-05-05
> **Robbie7up said:**
> I am still lost, do I input the codes from the thread into terminal,or where?haha, 

Open a terminal, then go to this site: [http://forlong.blogage.de/entries/pages/Compiz-Check](http://forlong.blogage.de/entries/pages/Compiz-Check)

Copy and paste (or better yet Highlight and middle-mouse click) the lines in the green highlight.

---

### Post by Robbie7up on 2009-05-05
> **louieb said:**
> Visual effects did not work on my T30 until I installed Jaunty. You probably have ATI radon graphics.  Specs for most thinkpads can be found at [ThinkWiki - Linux on ThinkPad]("http://thinkwiki.org/wiki/ThinkWiki")  

Which version of Ubuntu did you install?
I installed 7.1 but then updated to the newest version

---

### Post by Robbie7up on 2009-05-05
[B]There has been (at least) one error detected with your setup:
 Error: Laptop using radeon driver. 

Would you like to know more? (Y/n) y

 It has been detected, that you are running a laptop with an ATI chip.
 The radeon driver supports Compiz out-of-the-box but because of a nasty bug
 in the driver that causes X to freeze on some cards, this particular
 combination had to be blacklisted in Ubuntu "Hardy Heron".

 In case you already used Compiz successfully on Ubuntu 7.10[/B] [B](Gutsy), it is
 safe to skip the blacklist. [/B]

That is what it says when I do the stuff on the website in terminal

What now?

---

### Post by TheNosh on 2009-05-05
> **Robbie7up said:**
> I installed 7.1 but then updated to the newest version

do you mean you updated directly from 7.10 to 9.04!?!? that could be relavent

---

### Post by wiznillyp on 2009-05-05
There are a few options, you can have Compiz skip the blacklist and load anyway, or you can paste that output in the thread about Compiz-check and see what they say.

I think the latter is a better choice, but for now, running this command will work:

mkdir -p ~/.config/compiz/ && echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager

However, it says that there is a nasty bug to make it crash, so do not blame.  Blame Obama.

---

