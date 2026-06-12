---
title: "Install goes to command line"
date: 2009-01-04
forum: New to Ubuntu
---

### Post by dabellator on 2009-01-04
Ok, I could just be a HUGE beginner and missing something obvious, but in the docs I have read it seems as though the install process is graphical, and I can't find any command line instructions.  When my computer boots the CD it asks what language I prefer, then I select Install Ubuntu, then it gives me a Ubuntu graphic and progress bar, but when it fills up it sends me to a UBUNTU@UBUNTU command line.  What should I do next?
-JB

---

### Post by jimmy the saint on 2009-01-04
hmmm
try typing "startx" and see if that loads the desktop?

---

### Post by dabellator on 2009-01-04
I'll give that a try, but in the meantime I want to clarify something.  You said desktop, but I'm trying to install Ubuntu, not get to my current desktop.  Is that what you meant?  In any case, ill give it a shot and see what I come up with.
-JB

---

### Post by overdrank on 2009-01-04
> **dabellator said:**
> Ok, I could just be a HUGE beginner and missing something obvious, but in the docs I have read it seems as though the install process is graphical, and I can't find any command line instructions.  When my computer boots the CD it asks what language I prefer, then I select Install Ubuntu, then it gives me a Ubuntu graphic and progress bar, but when it fills up it sends me to a UBUNTU@UBUNTU command line.  What should I do next?
-JB
Hi and welcome, as jimmy the saint pointed out you may try that command. Also it may have to do with the ProSavage8 graphics of your system. Have you checked the cd for defects from the start/install screen?
You may also try some of the options under the F4 keys at that screen.

---

### Post by jimmy the saint on 2009-01-04
If you are using the normal cd, startx should attempt to load the ubuntu live cd desktop envrironmnet.  However, as overdrank pointed out, your video card could be the issue.

---

### Post by dabellator on 2009-01-04
I just tried it and I get a message saying something along the lines of no screen found or something like that.  finally it said "giving up" (i thought that was pretty funny) and went back to the Ubuntu command line.  Any more ideas?
-JB

---

### Post by jimmy the saint on 2009-01-04
Download the alternate install cd and use it instead.  It does not use a graphical environment.  Don't worry, you still get menus, but they are like and old DOS program as opposed to a shiny new gui program.  This should eliminate the need for you to be able to load a full x environment in order to do the install.

---

### Post by halitech on 2009-01-04
did you download and burn the Live CD or the Alt install cd or the server cd? if you went with the server cd, it is command line only. if you went with the live cd or alt install cd, you may have an issue with some of your hardware (normally the video card) that ubuntu doesn't like.

---

### Post by jimmy the saint on 2009-01-04
> **halitech said:**
> did you download and burn the Live CD or the Alt install cd or the server cd? if you went with the server cd, it is command line only. if you went with the live cd or alt install cd, you may have an issue with some of your hardware (normally the video card) that ubuntu doesn't like.

Yeah, but even the server cd loads menus not a straight command line prompt.

---

### Post by halitech on 2009-01-04
I know but the OP isn't totally clear by what they are seeing so just brought it up to get clarification on exactly what they downloaded and are trying to install. I agree it sounds more like the Live CD and not liking the video but just wanted to rule things out. :)

---

### Post by dabellator on 2009-01-04
just to clarify, I believe I am using the LiveCD because i went to the download section, picked 8.10, then hit the download button, so I didn't select any other options.

as for the command line I am getting there is some information above it first.  I get few lines saying Ubuntu is free and I can read more in a certain file, then it explains sudo and says if I want to learn more i should use the command sudo root something (sorry, I'm trying to remember what it says).  the command line i believe says UBUNTU@UBUNTU`$.
-JB

---

### Post by jimmy the saint on 2009-01-04
Yeah, try the alternate cd
for 64 bit:
[http://ubuntu.osuosl.org/releases/8.10/ubuntu-8.10-alternate-amd64.iso](http://ubuntu.osuosl.org/releases/8.10/ubuntu-8.10-alternate-amd64.iso)
for 32 bit:
[http://ubuntu.osuosl.org/releases/8.10/ubuntu-8.10-alternate-i386.iso](http://ubuntu.osuosl.org/releases/8.10/ubuntu-8.10-alternate-i386.iso)

This is a us mirror. If you are somewhere else, you may try going to this link and selecting a server where you are.
[http://www.ubuntu.com/getubuntu/downloadmirrors#mirrors](http://www.ubuntu.com/getubuntu/downloadmirrors#mirrors)

---

### Post by oldos2er on 2009-01-04
> **dabellator said:**
> just to clarify, I believe I am using the LiveCD because i went to the download section, picked 8.10, then hit the download button, so I didn't select any other options.
  

 You should probably run 'Check CD for defects' before trying to install.

---

### Post by dabellator on 2009-01-04
I did a cd check earlier and it come back that everything was fine, and the install seemed to go through just fine.  When it went to boot it gave me two errors, which confirms the video error I thought I had:
(EE) savage(o): no valid modes found
(EE) screen(s) found, but none have a usable configuration

I really hope we can get this to work, I don't want to load windows!  What should I do next?
-JB

---

### Post by dabellator on 2009-01-04
I should point out that I have tried running in low graphics mode and the screen just goes blank while the fans keep spinning.  Does this mean that my savage video just isn't compatible with Ubuntu?
-JB

---

