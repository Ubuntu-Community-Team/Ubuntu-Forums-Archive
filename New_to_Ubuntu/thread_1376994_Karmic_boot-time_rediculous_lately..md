---
title: "Karmic boot-time rediculous lately."
date: 2010-01-09
forum: New to Ubuntu
---

### Post by k3lt01 on 2010-01-09
In the last few weeks my laptops Karmic install has slowed down alot at boot-time. Last night I updated and Ureadahead has had 4 attempts at doing its thing and I am still waiting for Karmic to boot to a usable stage. I am typing this from my Lucid install.

I had bootchart etc installed and it showed up OK but it wasn't. I have since removed it and nothing has changed. I think Ureadahead is the problem but I am not sure if removing it will bork my system.

Is anyone else having a similar experience or know of the probem? if yes what did you do?

---

### Post by warfacegod on 2010-01-09
Have you checked the start up apps? An update to the newest kernel may be in order too. Can't tell you about Ureadahead though, sorry.

---

### Post by danwosere2007 on 2010-01-09
Without being a super mega technical engineer (which sadly im not), i think war had a good idea, perhaps hack about with the start up applications, and by using powers of deduction (disabling and re-enabling the apps) try to logically discern which application is causing you grief. At the same time perhaps meddling with applications you are uncertain of would have bad consequences but as long as you steer clear of system critical ones im sure it wouldnt do much harm. Failing that wait about for some one with a little more experience to help you with your dilemma as i am but a rookie myself ;) good luck dude! 

-Dan

---

### Post by k3lt01 on 2010-01-09
I finally got Karmic booted to a usable stage, it only took slightly over an hour. After I got it going I rebooted again and the next one was a few minutes.

I will try out your suggestions and see what I find.

---

### Post by k3lt01 on 2010-01-16
There is no doubt about it Ureadahead was the problem. I removed it off both my Karmic and Lucid installs and my boot times have decreased dramatically. Furthermore prior to its removal each time I updated Ureadahead would cripple my system (both Karmic and Lucid) upon reboot, now after each update the boot is crisp and fast.

---

### Post by lavinog on 2010-02-12
> **k3lt01 said:**
> There is no doubt about it Ureadahead was the problem. I removed it off both my Karmic and Lucid installs and my boot times have decreased dramatically. Furthermore prior to its removal each time I updated Ureadahead would cripple my system (both Karmic and Lucid) upon reboot, now after each update the boot is crisp and fast.


I think they need to just disable ureadahead for karmic installs.  I have been trying to track down some of its issues:
[https://bugs.launchpad.net/ubuntu/+source/ureadahead/+bug/501715](https://bugs.launchpad.net/ubuntu/+source/ureadahead/+bug/501715)
For a while I was getting segfaults in xorg everytime ureadahead would do its trace.  That seemed to stop recently, but the memory issue is still there, and likely other stability issues still exist.  There have been many posts about stability issues after an update that disappear after the next update.

---

### Post by k3lt01 on 2010-02-12
On a new standard install I make sure it is removed before I do anything. It just isn't worth the time dealing with it on a low resource laptop. I even removed it from my desktop.

---

### Post by Phil Hansen on 2010-02-12
Does this only apply to Karmic?
If it does apply to other installations how is it disabled?
Looked but couldn't find ureadahead.
Thanks
Phil

---

### Post by lavinog on 2010-02-12
ureadahead is only on karmic and lucid.

---

### Post by k3lt01 on 2010-02-12
> **lavinog said:**
> ureadahead is only on karmic and lucid.Ureadahead isn't in all Karmics, from what I can tell it come through as a new install in one of the initial updates. I have 3 Karmic disks (amd64 and i386 LiveCDs and i386 Alternate) and it is only on the Alternate and it was downloaded a week after release.

---

### Post by lavinog on 2010-02-12
> **k3lt01 said:**
> Ureadahead isn't in all Karmics, from what I can tell it come through as a new install in one of the initial updates. I have 3 Karmic disks (amd64 and i386 LiveCDs and i386 Alternate) and it is only on the Alternate and it was downloaded a week after release.

It was installed on all of my systems when I upgraded from jaunty (64 and 32)

---

### Post by Eksilius on 2010-02-20
I haven't got these insane boot times bu I've noticed on two different system that after sreadahead was replaced by ureadahead, my boot times got longer by 5-10 seconds. Removing the pack file to force a reprofile has repeatedly proven that boot is faster without ureadahead than with it. Other people are having problems with it as well, both like mine ([https://bugs.launchpad.net/ureadahead/+bug/491956/?loggingout=1](https://bugs.launchpad.net/ureadahead/+bug/491956/?loggingout=1)) and with odd memory usage search for it in Launchpad and subscribe to the bugs that match your issues. It's the best way to let the developers know that it's a serious issue.

To those of you that have disabled ureadahead as a workaround, what's the safest and best way to do it?

---

### Post by k3lt01 on 2010-02-20
I simply removed it and sreadahead totally.

---

### Post by skymera on 2010-02-20
> **k3lt01 said:**
> There is no doubt about it Ureadahead was the problem. I removed it off both my Karmic and Lucid installs and my boot times have decreased dramatically. Furthermore prior to its removal each time I updated Ureadahead would cripple my system (both Karmic and Lucid) upon reboot, now after each update the boot is crisp and fast.

I believe uReadahead has a memory issue.

It's not releasing RAM after boot.

When uReadahead profiles boot, excessive RAM is used but when the desktop is loaded the RAM isn't released. This pushes RAM usage to about 1200MB~

However on subsequent boots, memory usage is fine.

So it's def a problem with uReadahead

(64bit Lucid)

---

