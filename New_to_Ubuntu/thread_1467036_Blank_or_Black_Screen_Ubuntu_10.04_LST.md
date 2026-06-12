---
title: "Blank or Black Screen Ubuntu 10.04 LST"
date: 2010-04-30
forum: New to Ubuntu
---

### Post by Don Mega on 2010-04-30
This is for those of you who have had this problem with installing Ubuntu 10.04 LST
I followed this for my old laptop with Intel 852/855GM also works for NVIDIA graphic cards
don't worry very simple


So, here is what should work:
Download and create a CD Image for Ubuntu 10.04 LTS
Insert Cd, then Reboot

 At the very first screen, the one with just the rectangle (it’s meant  to be a keyboard) and a human figure, at bottom of screen -press spacebar 

 Then choose your language.
 Then make sure you have “Try Ubuntu without any changes” selected,  and then press F6
 Then Press arrow button to the right you will see the command terminal section at mid bottom of screen with white text 

Add this to the end of the command line:
 [INDENT]i915.modeset=0 xforcevesa
[/INDENT] Then press enter and it should boot successfully.

Then WOLLAH!:p 
Simply let it load, be patient and install or test the NEW and excellent Ubuntu 10.04 LTS!!!

This was all thanks to this forum at [http://www.ubuntugeek.com/how-to-fix-ubuntu-10-04-lts-lucid-blank-screen-at-startup.html ]("http://www.ubuntugeek.com/how-to-fix-ubuntu-10-04-lts-lucid-blank-screen-at-startup.html")
Thanks ALOT YOUR THE BOMB!!!

---

### Post by madjr on 2010-04-30
i dont have that problem, but thanks for sharing

---

