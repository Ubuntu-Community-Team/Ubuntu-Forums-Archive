---
title: "sound problems"
date: 2009-06-27
forum: New to Ubuntu
---

### Post by leemajors on 2009-06-27
hi there,

i was wondering if someone out ther might be able to help me troubleshoot why my sound doesn't work any more?

it was working just fine (9.04) just a week or so ago, and now there's no sound any more.

i've got a dual boot and when i boot into windows the sound works as it should. 

i've checked the volume control, switched to all the available playback devices in the volume control preferences (and yes, made sure the volume is set to above zero and not muted) but i don't know what else to check.

thanks in advance!

Lee

---

### Post by candtalan on 2009-06-28
Do you know if it works using a live cd? There might be some reassuranceif it does, and some other mileage, although I do not know enough to suggest more.

---

### Post by leemajors on 2009-06-30
i don't know unfortunately. i will download one and have a look but does anyone have any more suggestions while i get it?

---

### Post by leemajors on 2009-07-03
just booted up a live session and yes, the sound worked perfectly.

how then do i find out what the problem is and how to fix it, and also importantly how did it happen as I really can't see what could have happened to cause the problem in the first place?

---

### Post by leemajors on 2009-07-10
can anyone help me with this? i'm completely at a loss as to how to repair whatever it is that's gone wrong.

a live boot cd worked perfectly.... so there's definitely nothing wrong with the sound!

---

### Post by louieb on 2009-07-10
Because sound stopped working on my laptop (running Jaunty), I subscribed to this thread a few days ago. Just to see what answers you got.

After playing around with System>Preferences>Sound: right and left clicking on the speaker icon, checking and changing settings, pushing the volume button on the keyboard finally got sound again. 

Think my problem was caused by having a separate home and doing a fresh install of Jaunty over Intrepid. Guess the configuration files for sound might have changed. 

While running the live CD check settings in System>Preferences>Sound , right click the speaker and check the settings  in preferences  and  the volume control.  Just make sure they are the same in the hard drive install.

---

### Post by leemajors on 2009-07-10
louie thank you so much!

i had tried so many things to get the damn sound to work but in the end it was just the simplest thing that fixed it -- matching the preferences in all of those places in the live cd settings to the ones that weren't working in jaunty.

a restart had to happen after i matched as well.

thanks. i didn't know there were so many places i had to check! 

i don't know what i did to make that stop working, i've been on jaunty for quite a while and sound was working fine, but who cares, yay, i've got sound again :D

---

