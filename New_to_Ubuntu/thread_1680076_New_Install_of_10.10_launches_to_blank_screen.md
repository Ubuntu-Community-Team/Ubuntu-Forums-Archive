---
title: "New Install of 10.10 launches to blank screen?"
date: 2011-02-01
forum: New to Ubuntu
---

### Post by AtlantaGaNoob on 2011-02-01
Total Newbie here. First Ubuntu, first Linux system. I downloaded the 10.10 edition. I installed it on an older computer. I did the install from the CD and it went fine. When it was finished it asked me to restart. I clicked the button to restart. The screen went blank and the computer never actually restarted. So I held in the power button for 5 seconds, and it restarted. It launched from the CD (I forgot to remove that). So I removed it and did a restart again. I get nothing. The screen is blank and there's a blinking cursor in the upper lefthand part of the screen. I thought it might be configuring itself so I left it alone. I came back an hour later to the same thing.

Is there something else I'm supposed to do? The computer is about 7 years old but has a 250 gig HD, a 256 MB video card. I told it to do a clean install (use the whole disk). 

Any idea's suggestions and a total newbie could understand? Thanks.

Update: It has a 2.7 Ghz Celeron processor. Is that too slow for 10.10?

---

### Post by taseedorf on 2011-02-02
It should work fine, not too slow at all.  Once installed, you might want to do some tweaks to make it perform a bit better.  try doing a ctrl + alt + 2 and see what happens

does it give you a login screen?

---

### Post by AtlantaGaNoob on 2011-02-02
> **taseedorf said:**
> It should work fine, not too slow at all.  Once installed, you might want to do some tweaks to make it perform a bit better.  try doing a ctrl + alt + 2 and see what happens

does it give you a login screen?
No, unfortunately, no login screen. It does the usual POST but then I just get a blank screen with the flashing cursor. If nothing else works I can always try re-downloading the *.iso file and then re-installing. It's just weird because it installed without an issue (other than the constantly refreshing screen when launching from the CD). But once it asks me to "restart" after installation then I get nothing. Maybe it has something to do with a 5+ year old video card?

Me so confused :(

---

### Post by AtlantaGaNoob on 2011-02-02
A friend who is using Ubuntu says he has never seen this happen. He suggested I download 10.03 (.04?). He said that is what he's using and he had no problems installing that on a system similar to mine. I guess I'll try re-installing 10.10 and see if that makes a difference. Otherwise I'll try 10.0x. I'm sure it's something I did wrong or something wrong with my computer but needless to say it's not the way I anticipated my first Ubuntu experience to go. 

I'll let everyone know if anything changes.

---

### Post by Mark Phelps on 2011-02-03
I've found that 10.10 doesn't boot for me over half the time -- and I've been booting Ubuntu distros on this machine without problems for over five years!

Next time, try the following:
1) When booting the machine, hold down the SHIFT key.  This should force a GRUB menu to display
2) When that menu is on screen, select the Recovery option
3) When another selection is display, select the option to repair broken packages.
4) If that goes OK, you will eventuall get to a command prompt.
5) At that point, enter "startx"

If this worked OK, you should see a desktop.  Simply shut down normally and you should be OK for a while.

---

