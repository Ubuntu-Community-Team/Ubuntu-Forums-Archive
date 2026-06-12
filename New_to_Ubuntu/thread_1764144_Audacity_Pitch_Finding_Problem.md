---
title: "Audacity Pitch Finding Problem"
date: 2011-05-21
forum: New to Ubuntu
---

### Post by r3bol on 2011-05-21
Hi, I have Audacity 1.3.12 and am trying to find the pitch of a sound clip. 
I googled and found someone saying to select the sound clip, right click > Pitch. Problem is, when I do this, the view goes blank and nothing happens. 

Is this feature working on Linux? Is there anything I'm doing wrong?

---

### Post by tgalati4 on 2011-05-21
I find:

gtkguitune - Guitar and other instruments tuner

works pretty well for finding major key signatures in sound files.

sudo apt-get install gtkguitune

You may have to play with your volume control to get correct patching so that the tuner picks up what you are playing.

An alternative in audacity is to grab a selection of the clip and use the spectrum analyzer and pick out the resonant peaks using the mouse.

---

