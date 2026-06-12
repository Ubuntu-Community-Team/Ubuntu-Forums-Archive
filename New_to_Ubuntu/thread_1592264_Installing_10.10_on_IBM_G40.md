---
title: "Installing 10.10 on IBM G40"
date: 2010-10-10
forum: New to Ubuntu
---

### Post by cdnwes on 2010-10-10
Good day everyone.

I am a relative newbie to the world of Linux having fooled around with various live discs.  I have decided that I am not going to learn much about using it if it isn't my main operating system so I have ditched Windows XP and installed Ubuntu 9.10 on my older laptop.

I have an IBM G40 with 740.8MB of memory, an Intel (R) Pentium (R) 4 CPU 2.40GHz.  I realize this is not a super popular computer and efforts may not have been made to make it fully functional with Ubuntu.

I am running 9.10, Kernal 2.6.31-22-generic, with Gnome 2.28.1.  Everything seems to be working just fine with this version so far.

I have seen a number of posts referring to the processor not being supported after 9.10 with a number of failures to load.  I would like to be able to load 10.10 but do not know enough about the various commands to be able to trouble shoot on my own if the install goes south (other than trying to reinstall again and again or reburning a disc).

My questions:

1. Can anyone tell me if this issue has been addressed in 10.10 or if I will have to stick with 9.10 until it loses support?

2. Is 10.10 too much OS for this machine?

3. If 10.xx will be unloadable/unsupported on my old laptop, what should I do for an operating system?  Should I regress to the 8.04 LTS?

I am not sure how much life this laptop has in it but it is very good for surfing the web and storing photos.  I am not looking for it to do much more than work properly and let me do the typical surfing / typing functions.

Thank you for any help.

Please refer to the below posts for background:

```
http://ubuntuforums.org/showthread.php?t=1483170&highlight=g40
```

```
http://www.linuxquestions.org/questions/ubuntu-63/ubuntu-10-4-install-on-ibm-g40-failure-807942/
```

---

### Post by sikander3786 on 2010-10-10
All of your questions will be better answered if you can boot into a Maverick(10.10) Live CD. You can see if all of your hardware works with it and can decide to install it or not.

1. I never heard that Pentium 4 has lost support in Ubuntu after 9.10.

2. Will be better answered by a live CD. However, still your system seems quite capable to run it.

3. Should be answered after you've tested a live CD :-) You can always try minimal installs, lighter DEs like LXDE, XFCE etc.

---

### Post by cdnwes on 2010-10-11
Right.  

I tried the live disc but it hung up at the ubuntu logo where the dots go across the screen underneath.

I hit ESC as it stayed like that for some while and a black screen with this error showed up:

process 241 GLib Warning getpwuid_r failed due to unknown user id (0) stdin: error0

Thoughts?

---

### Post by oldos2er on 2010-10-11
You should check the disc integrity with md5sum ([https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)) to rule out a corrupt disc problem.

---

### Post by cariboo on 2010-10-11
THe one other thing you can do is start in what was formerly called safe graphics mode. At the initial screen, with the keyboard and the man at the bottom, press any key to see the menu. Press F6 and select nomodeset, then press enter. You should boot to the desktop.

---

### Post by Windows Nerd on 2010-10-11
As for the Pentium 4 not working with Ubuntu after Ubuntu 9.10, that is not correct. Ubuntu was just dropping support for i486 and i586 processors. If you have a computer from within the last 10 years you should be good. If you have one that is older than that, pop the LiveCD in and see if it works.

I myself have a P4 computer thats still going strong, I don't run Ubuntu on it, but I do run Arch Linux on it (which also does not support i486 or i586 Processors) and it works blazingly fast. 

If your LiveCD can boot, your most crucial hardware is compatible with Ubuntu. You will probably need to then verify that your wireless, sound, and graphics work well (these three are generally the problem-causers for many).

---

### Post by cdnwes on 2010-10-11
> **oldos2er said:**
> You should check the disc integrity with md5sum ([https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)) to rule out a corrupt disc problem.

md5sum - Check.

> **cariboo907 said:**
> THe one other thing you can do is start in what was formerly called safe graphics mode. At the initial screen, with the keyboard and the man at the bottom, press any key to see the menu. Press F6 and select nomodeset, then press enter. You should boot to the desktop.

I never saw a man, only an ubuntu logo with a number of dots going underneath ala KITT in Knight Rider.


I will try the F6 thing to see if it works.

---

### Post by cdnwes on 2010-10-11
Right, again.

I tried out the CD I burned to see if it was actually a coaster.  It is good and started up 10.10 on my wife's newer Dell laptop so the disc is fine.

Now, how long would 10.10 take to start up on my vintage laptop?  Perhaps I am just not waiting long enough?  After five minutes though I hit Esc and got error process 254 GLib warning.

I think it took her laptop about two minutes to spin everything up and get going, perhaps 30 seconds longer.

---

### Post by cdnwes on 2010-10-12
Well, this is turning into a bit of a blog for me it seems.  At the risk of making it longer though, here's where I am at.

I took cariboo907's suggestion of hitting F6 and going with nomodest.

At 5:36 on the stopwatch, music sounded.

At 7:31, the desktop appeared ready to use.

This is from the live CD disc. 


**I am typing this post from Firefox in 10.10.**


I will try reloading this after shutting down and just leave it be for 10 minutes in default mode.  I think this poor old computer is working at its limits with the CD (likely a pretty slow and aged drive in its own right) and the processor and I just did not give it long enough to load.  I do not remember any of the other live cds taking anything close to this time to load.  Perhaps it is all the advances and changes with 10.10.

I did not think it would take that long to load.  

Is anyone using 10.10 on something of this age?  Should I expect a super long boot if I install on the hard drive?  9.10 is pretty quick compared to XP.  

I will try out some other things as well to see if all is well.

While I will search the forum, is there any sort of testing you might recommend me do to see if all is well?  Internet is fine, display looks fine, and I will start surfing around to see what is what.


Thank you for the help so far though.  What a great start to my time in this community.

---

### Post by cdnwes on 2010-10-12
Righto.

After a long boot time, 10.10 is working fine with the regular load.  I rushed it thinking that it wasn't working out but it turns out that it was just a looooooooooooooooooooooooooooooooooong load time.

So, questions (summarized from above postings):

1.  What sort of load time should I expect with 10.10 on my hard drive?

2.  What tests should I do to see if all is working before I install?


Thanks for taking the time to work through the puzzlements here.

---

