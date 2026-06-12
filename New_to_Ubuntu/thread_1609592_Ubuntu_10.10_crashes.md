---
title: "Ubuntu 10.10 crashes"
date: 2010-10-30
forum: New to Ubuntu
---

### Post by benjie1 on 2010-10-30
Filed a bug and don't mean to duplicate things but this problem is getting worse. It has crashed 4 times today. Very annoying and getting to the point where I may have to stop using Ubuntu cause it really isn't functioning well Please help so that I can use this great OS. Apologies for any duplicate posting. newbie too.
[https://answers.launchpad.net/ubuntu/+source/xorg/+question/130707](https://answers.launchpad.net/ubuntu/+source/xorg/+question/130707)

---

### Post by bioterror on 2010-10-30
> **benjie1 said:**
> Filed a bug and don't mean to duplicate things but this problem is getting worse. It has crashed 4 times today. Very annoying and getting to the point where I may have to stop using Ubuntu cause it really isn't functioning well Please help so that I can use this great OS. Apologies for any duplicate posting. newbie too.
[https://answers.launchpad.net/ubuntu/+source/xorg/+question/130707](https://answers.launchpad.net/ubuntu/+source/xorg/+question/130707)

Does this happen with 10.04? As 10.04 is a LTS (Long Term Support), I'm going to suggest you to try it. I'm running on my desktop 10.04 and I've no hurry to move to 10.10.

Hope this problem gets sorted out, it would be a shame to loose one user to somewhere ;)

---

### Post by P4man on 2010-10-30
It could be a million things, we will have to narrow it down a bit. Lets start by telling us what hardware you have and what (if any) videodrivers you installed or activated?

Next, I would suggest you go to system | preferences | keyboard | layout | options and under "Key sequence to kill the X server" active the ctrl+alt+backspace. Next time the machine freezes up, use that key combo and if it throws you back at the login screen, then we know its likely a Xorg/video driver issue. If it doesnt, its (even) more serious.

If the above doesnt help, before hitting the reset button, try 2 more keyboard shortcuts; control+alt+F1. If the machine isnt hung completely, that should give you a full screen terminal where you can log in (control alt F7 or F8 gets you back to the GUI normally).

If neither if the above does anything, still dont use reset button, but try this:
[http://mark.koli.ch/2009/02/linux-magic-sysrq-key-r-e-i-s-u-b-reboot-even-if-system-utterly-broken.html](http://mark.koli.ch/2009/02/linux-magic-sysrq-key-r-e-i-s-u-b-reboot-even-if-system-utterly-broken.html)

(note that on most keyboards, sysrq key is the same key as printscreen).

If even that fails, then its a kernel panic or hardware problem. Do the keyboard leds flash?

---

### Post by zhogan85 on 2011-01-20
I've been having a problem that I feel should go under the same subject, "Ubuntu 10.10 crashes" but is different from the initial problem described and I'm not sure if its related.

Occasionally, maybe every couple of days, the screen will just go black and then Ubuntu restarts itself. I believe firefox has been running with multiple tabs and windows open every time this has happened. I'm still a noob so any ideas would be greatly appreciated and please let me know if you need any more info.

I'm running Ubuntu 10.10 on an Asus Eee PC 1005HA-P. I also have Windows XP installed.

---

### Post by steve7777777 on 2011-01-20
Response to zhogan85 - do you have XP running for extended periods of time - like all day, and it doesn't crash?
If that is true a hardware problem can likely be ruled out.

I suggest that you use [Webmin]("http://www.webmin.com/") to take a look at the logs. Note the exact time that the screen goes black and check the logs for events with the same time stamp. I'm new to Linux/Ubuntu and have found that Webmin is a great learning tool!

Hang in there. A flakey driver is the likely culprit. I have two Ubuntu systems running and have never had a single crash or freeze up.

---

### Post by zhogan85 on 2011-01-20
Thanks, I'll do that next time it happens and keep you updated. Windows has crashed a couple of times, but I use it so infrequently I guess I didn't think of it as a big issue. But I guess since both systems have crashed in the past, there might be a hardware problem?

---

### Post by Chris Edgell on 2011-01-20
I totally agree with bioterror.

p4man is giving good advise too, otherwise you can ruin your hard drive (hey, just ask me...lol)

And zhogan, you can read and SEE if it the same problem, but don't be afraid to start your own thread...you don't have to be the one worrying if they overlap...otherwise, it can be viewed as hijacking someone elses thread.  (Which I did a time or two until someone told me how that works.

Best wishes to you both!

Chris

---

### Post by Hamid2547 on 2011-01-31
my 10.10 ubuntu has a keyboard problem,for example i change layout to farsi and when i start to type it's half en half farsi like this "h&#1579;g&#1605;h&#1662;" and i can't change the layout and i have to logout to solve the problem, i dont know if 10.10 is proper version for me or not:roll:

---

### Post by boblizar on 2011-04-20
my ubuntu 10.10 freezes and hangs after being idle in screen saver mode for a little bit.  slackware never had a problem on this computer for the longest time until it freaked out one day and got formated to ubuntu.  next freeze im gonna drop down from 64 to 32 and if issue keeps going on ill drop from 10.10 to 10.04 also.

---

### Post by mörgæs on 2011-04-20
That is exactly what I would have suggested.

---

### Post by boblizar on 2011-06-16
this issue was resolved, and it was a hardware problem.  i had to flash the firmware of my seagate drive and zero the drive out.  back on 64, and already have a linux from scratch virtual machine built and installed on here =D  i would like to lose ubuntu to gentoo amd64 though sry =(  id also like to be able to compile my own kernels and have apt have less of a grip on me.

---

### Post by wildmanne39 on 2011-06-16
> **boblizar said:**
> this issue was resolved, and it was a hardware problem.  i had to flash the firmware of my seagate drive and zero the drive out.  back on 64, and already have a linux from scratch virtual machine built and installed on here =D  i would like to lose ubuntu to gentoo amd64 though sry =(  id also like to be able to compile my own kernels and have apt have less of a grip on me.
Hi, thats no problem go ahead and do it. I installed gentoo in virtualbox so I could learn how to do it, I was thinking about making it my primary system but I like ubuntu and the people to much.

---

### Post by steve7777777 on 2011-06-17
> **boblizar said:**
> this issue was resolved, and it was a hardware problem.  i had to flash the firmware of my seagate drive and zero the drive out.  back on 64, and already have a linux from scratch virtual machine built and installed on here =D  i would like to lose ubuntu to gentoo amd64 though sry =(  id also like to be able to compile my own kernels and have apt have less of a grip on me.

Could you post the model #, bios, etc of the Seagate or provide a link? Luckily no problems of that kind with my Seagates.

---

