---
title: "X Crashing--the straw that broke the camel's back"
date: 2010-05-11
forum: New to Ubuntu
---

### Post by admiralspark on 2010-05-11
Well, ladies and gentlemen, I've arrived at a decisive conclusion: I'm really not that impressed with Ubuntu 10.04. I'll try to keep this from being a rant and focus on the issues at hand, though.
[/RANT]

From the beginning I've had trouble with Lucid. My original laptop, a Compaq Presario that everything worked perfectly on in 9.04 and 9.10, got sent to the nether regions when the powercord got busted (new one is $80, laptop is 4 years old and I'm buying a new one in a month anyways). The laptop I'm currently using is an IBM ThinkPad: 1.6ghz Centrino, 1.2GB Ram, the 100GB 7200rpm hdd from my old laptop, an Intel 855GM graphics card (yes, I know, it blows). It worked great with 9.10 as expected. When 10.04 came out, I got all excited and downloaded it, wanting to try out everything new like a linux junkie noob (look, shiny things!). Except.....

On booting from the CD, it refused to go anywhere after the first menu. Apparently Canonical decided to make default some software piece that makes my graphics card and a select few others refuse to work without serious tweaking. "Okay, I can live with that" I figured, since the benefits still outweighed the costs. 

Then, after it's installed and the graphics configured fine, I notice that the computer takes a full 10 seconds longer to load to the desktop, and seems to have a crapload of unnecessary processes running in the background. But I still let that slide, because the newest version of my favorite 2D game (Battle for Wesnoth) was in the repositories. 

Now, I get to analyze the situation: no GIMP so that I had to scramble to find a way to draw up some diagrams for my Physics report, a video editor that's cool but probably unused by 75% of Ubuntu users, Broadcast which failed epically with my facebook (after spending 3 hours getting it to finally connect properly, it only shows you shortened versions of your feed and allows you to send mail, nothing useful), Ubuntu One completely fails to sync my files automatically even after I've gone through all the necessary steps, having to manually sign in on the site and upload from there. Oh, and I forgot to mention the complete OSX left-hand-buttons ripoff. But, Tweak fixed that. 

[/END RANT]

Okay, so here's my LATEST problem: for the first time in all of my linux testing (check my sig for a SAMPLE of the number of distros I use), X just decided to die on me. Oh, yeah, it happens every time I go to refresh my list of updates, so if there's a fix in the works I'm not going to get it :mad:

Here's some relevant information:
IBM ThinkPad R51
1.6GHz declocked Pentium (Celeron)
1.2GB Ram
100GB 7200rpm HDD
Intel 855GM Graphics card (I believe it's 8MB graphics....)

the Dmesg is telling me:
```
Buffer I/O error on device fd0, logical block 0
[  131.806600] end_request: I/O error, dev fd0, sector 0
[  131.806610] Buffer I/O error on device fd0, logical block 0
[  133.532026] [COLOR=Red]**[drm:i915_hangcheck_elapsed] *ERROR* Hangcheck timer elapsed... GPU hung**[/COLOR]
[  133.532037] [COLOR=Red]**render error detected, EIR: 0x00000000**[/COLOR]
[  133.532048] **[COLOR=Red][drm:i915_do_wait_request] *ERROR* i915_do_wait_request returns -5 (awaiting 39247 at 39245)[/COLOR]**
[  147.054381] end_request: I/O error, dev fd0, sector 0
[  147.054389] Buffer I/O error on device fd0, logical block 0
[  161.605205] end_request: I/O error, dev fd0, sector 0
```i915 has to do with my graphics, its either a driver or software integration bit (I'm too ticked to go look).  Notice also that 1) there's alot of those Buffer I/O request errors on either side of that text (like 3x what's printed above) and 2) I don't HAVE a floppy drive, I have no idea why it shows anything to do with fd0! :mad:

Okay, so, issue here is: What can I do? I'm sorely tempted to give up on this LTS at least until my next laptop shows up, and go back to either 9.10 or try 9.04. BfW is really the only reason I'm hanging on, because in the end it's my only source of 2D entertainment (8MB sucks that bad).

I'm going to make some predictions from the above: either my graphics card literally is overloading (makes no sense, and it's triggered by refreshing the updates) or my driver is junk, which would be incentive enough to just build BfW 1.8 from source and distribute it as a .deb for the rest of the 9.10 and 9.04 community. 

I'm posting in the Beginner's forums because I felt that this could be a valuable fix if it turns into a common issue, and I'm a bit noob when it comes to Intel graphics and drivers.

---

### Post by Chronon on 2010-05-11
It seems like a bit of a mega-thread.  I'll just pick one of your points:

Regarding longer boot-times (and possibly related to the fd0 messages), many people have reported much faster boot times after disabling floppy drive in BIOS (whether one exists on their system or not).

---

### Post by admiralspark on 2010-05-13
Eh, sorry for the long thread. It really did turn into half of a useless rant.
Anywho, regarding the floppy, I'll try doing that. 

My biggest concern is making it so that X doesn't crash. I've done some more testing and even with the creation of an xorg.conf file with the right settings, it will still crash if I try to play anything in VLC or the Movie Player. I know it's not a hardware problem, and that it's 10.04 specific: everything worked perfectly fine with 9.10 before. 

I think I'm going to revert to 9.10 and compile Wesnoth 1.8/Openoffice 3.2/anything else from scratch, hopefully making .deb's that I can upload later on. I'll try again with the xorg.conf file again before I do that though.

---

### Post by Catharsis on 2010-05-13
You're suffering from a known bug with i855 graphics cards that was mentioned in the Release Notes. See:
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

---

### Post by admiralspark on 2010-05-14
Yep, and I sort of expected that they'd have it working fine in a Long Term Support version, especially since it was never an issue with 9.04/9.10. *sigh*
I'll live until the new laptop arrives. Thanks for all the help!

---

