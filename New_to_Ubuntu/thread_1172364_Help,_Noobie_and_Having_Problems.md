---
title: "Help, Noobie and Having Problems"
date: 2009-05-28
forum: New to Ubuntu
---

### Post by Dante311 on 2009-05-28
Hey everyone,

I have recently installed Ubuntu 9.04 and am having problems.  My main problem is that when the dual boot options come up and I select general Ubuntu, it says error message that cannot display login screen and then goes to freeze screen of the graphics although in repeating pattern.  I have sometimes got it to start up but unsure why it worked on those occasions.  I have a feeling it may having something to do with my graphics driver because when I load windows it now says new hardware for my ATI graphics card.  Please help, I would love to start learning and using Linux.

-Using T400 Lenovo
-Complete Linux noob (no command knowledge)
-Had to install twice because i didn't allocate enough memory the first time and do still have old install show up on boot up (this does work but has no memory for updates)

Thanks!

---

### Post by Grafixx01 on 2009-05-28
Hey, welcome! I'm fairly new myself to the forums and to Ubuntu.
 
Have you tried completely wiping your hard drive of BOTH Windows and Ubuntu and then trying to do a fresh reload of Windows and then Ubuntu? I did that on my OQO UMPC and it worked. However, when I did it, I wiped the drive, then loaded Windows XP Tablet on a 35GB partition, but I didn't do any updates or software installs. Then I turned right around, did the Ubuntu install of 9.04, worked without errors. I then went and did updates for both OSes. The ONLY thing that I see sometimes is when booting Ubuntu, I'll get wacky colors on the screen after I select Ubuntu (Normal Mode) and before it loads the screen for my user name and password.

---

### Post by tanjir on 2009-05-28
does your graphics card use intel chipset by any chance?

---

### Post by jerrrys on 2009-05-28
hi Dante311 and welcome to the forum...

im typing and eating breakfast at the same time so someone else will probably post to you before this gets done...at any rate, here's my 2 cents...

sounds like you need to forget about ubuntu for the moment and get windows happy again or you may lose it. hope you got a backup just in case...

if windows is telling you; you got new drivers, you should go to device manager (think thats what it was called) and update drivers. it will give you the option to roll back to old drivers if it does not work. once you have drivers updated or not, that should keep windows happy...

next will come in a few minutes...i have come to the conclusion that i cannot eat, type, and think at the same time...

---

### Post by b@sh_n3rd on 2009-05-28
The "wacky colors" came for me on my intel hardware. It was like, weird coloured lines for me. I noticed that this happens when using the "vesa" driver on X Server. This can be corrected in the "/etc/X11/xorg.conf" file, but that sometimes doesn't show "vesa"...it just shows a bunch of variables :D. On Jaunty, the new X server sets the drivers automatically if not stated in the xorg.conf. So, what we need is to know what your card is exactly...*if* it's a video issue that is. Maybe you could try a reinstall as Grafixx01 mentioned? I'd be groaning if I got to a position like this though :D. The only reason I would mention this is because winblows starts grumbling too... It would be helpful to know the exact model of your video card. If you've got two options on the bootloader, then you must be having like, two versions of ubuntu? anyways, it seems messed up....

Oh yeah, and welcome to the community! :D..

---

### Post by b@sh_n3rd on 2009-05-28
> 
next will come in a few minutes...i have come to the conclusion that i cannot eat, type, and think at the same time...lol, In health class, I've learned that it's not good to do this...dunno why...careful though, your food might get sucked out by your brain before it hits the digestive system :D (srry for being off topic but I found this to be quite amusing :D)

---

### Post by jerrrys on 2009-05-28
ok, back with ya. first let me say thanks for the comment there b@sh_n3rd. with that kind of in site you are no dough seeking a career in the medical community :D

ok, lets say you got driver issue with windows fix.  next did you do a defrag before attempting to install ubuntu? if not, better late then never i guess. im guessing your running XP, if your running vista, let me know. with vista there is one more step i would suggest. 

NEXT...i am once again guessing that you got the ubuntu LIVE cd. if so please just try to run it without installing it.  if it will not run, we need to take a look at that.

back to your partition woes and dual ubuntu install. this in my oponion needs to be cleaned up before reinstalling ubuntu. that can be done using the gparted from the live cd. 

if you want to continue, let me know and give us some specs on your system. how big of a HDD you got, how much ram?

---

### Post by b@sh_n3rd on 2009-05-28
> ok, back with ya. first let me say thanks for the comment there b@sh_n3rd. with that kind of in site you are no dough seeking a career in the medical community :grin:haha, I enjoy being a doctor on computers...and I'd rather continue *selling* books to the medical field instead of actually, jumping into it! (only like health to a *certain* extent...knew too much in IT, so I just selected that in school :D)

---

### Post by Junkieman on 2009-05-28
> **Dante311 said:**
> I have sometimes got it to start up but unsure why it worked on those occasions.  I have a feeling it may having something to do with my graphics driver because when I load windows it now says new hardware for my ATI graphics card.

Hi and welcome!

Okay I'm gonna take a wild guess here: because it 'randomly' started up a few times, and because Windows suddenly says it detected new hardware, there is a small chance that your hardware is faulty.

Or it could even be your GFX card isn't getting enough power. Yes it might have worked before, but it's always worth the check, right?

I might be completely wrong, but I've seen some crazy tings from hw faults, things that I couldn't logically explain. The best thing to do is verify that I am hopefully wrong! Reinstall your GFX drivers in Windows and get them working again. Faulty hardware shows different symptoms and is tricky to troubleshoot. Did you add any new hardware recently? Are you running on a UPS or have choppy power from the mains?

Do you have any applications in Windows that show your PC health status, like temperature/voltage readings? I know Intel chipsets provide such tools, but I'm not sure about ATI. Check if the voltages vary a lot when your PC is under a lot of load/processing.

I hope any of this helps, it's been a looong time since I did any real hardware troubleshooting :p

---

### Post by jerrrys on 2009-05-28
ok b@sh_n3rd, doctor on computers. got a question for you. i have never used gparted on the ubuntu cd.  i instead use my gparted live cd, im guessing its the same...is it?

---

### Post by Elfy on 2009-05-28
I think that some of the older ati cards are no longer supported on either linux or windows - though windows suddenly appearing to see it as a new card would cause me to wonder why.

We will need to know what graphics card you are playing with - run this command from aterminal - Apps >accessories

```
lspci |grep VGA
```

tell us what it says please.

---

### Post by Dante311 on 2009-05-28
Ok, thanks so much for all of the advice but I think it would be best for me to put down some specs because there seems to be a lot of options I could take.

-I have a integrated  Intel® X4500 with ATI Mobility Radeon HD 3470 w/256MB Switchable Graphics
 * I had to look up on this because can't find card listed
-I am running Windows XP
-I have 3GB Ram, and dual core 2+ GHz processer
-I am in Ubuntu now and found it that it only seems to run after I load in windows first and then reboot and then load Ubuntu, it will then load up the graphical login as normal
-Tried to update drivers again in Windows but there is no driver listed on AMD's website for my graphics card :(  

Is it possible to do a print screen at load up so that I can show my dual boot options?

Sorry, I'm really bad at this and do not really want to resort to rebooting both systems just yet.  Thanks!

---

### Post by Dante311 on 2009-05-28
UPDATE:

I have got it to work.  I still have the problem of 2 Ubuntu's showing up in my boot screen but I ran windows and it did a scan disk; said it corrected some errors.  Then when loaded up I was able to run ATI and now works again.  It is not asking for graphics card.  Hopefully, it will just work now everytime I load Ubuntu.  Thanks so much for the help.  I will surely be around the forums to try and learn some Linux skills :D

---

### Post by Elfy on 2009-05-28
> I have got it to work. I still have the problem of 2 Ubuntu's showing up in my boot screenThis is not a problem - you have 2 options because one is the recovery option - it might come in handy - mine certainly has done on more than one occasion :)

When you get a kernel option you will get a further 2 - you can later remove some of these - but I would wait until it becomes a real issue beofre you do that :D

---

### Post by Junkieman on 2009-05-28
Guess it was disk errors then, glad it's working now and hope your Linux journey is a good one :D

---

