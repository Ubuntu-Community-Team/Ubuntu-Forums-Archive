---
title: "No login screen at startup?"
date: 2009-07-17
forum: New to Ubuntu
---

### Post by TStarboy on 2009-07-17
Hi,
I'm running Ubuntu 9.04, and when I start my computer, the boot screen shows up normally, but upon reaching the login screen, the display shows a black screen with the bottom half blue. Pressing Alt+f1 just shows some garbage at the top of the screen. Can anyone help with this?

---

### Post by Sidewinder1 on 2009-07-17
Did you recently make any changes to users or permissions or partitions?
Can you boot with the live CD? Perhaps that way you can find the problem.

Also **Welcome!!!** to Ubuntu Forums!!!

---

### Post by TStarboy on 2009-07-17
I can boot with the live CD. I have not made any changes to partitions, but I have had Windows XP installed on a different hard drive since before I installed Ubuntu, and that works fine.

---

### Post by Sidewinder1 on 2009-07-17
Afraid you'll have to wait 'til someone more knowledgeable than I chimes in as it may be a GRUB issue. Does it give you any error messages?

---

### Post by Wim Sturkenboom on 2009-07-17
It's not clear from your opening post if this always has been the case or if you had a working system and it happened all at a sudden.

What do you try to achieve with <alt><F1> ? It calls up de menu so no surprise that that is garbled when you invoke it as your graphical stuff is a not quite working.

What video card and what monitor (make and model for both).

You can use <ctrl><alt<F1> to get to a console and login. Next you can inspect /var/log/Xorg.0.log to see if there are any clues in there. Specifically check for lines starting with EE to see what it says.

Can you tell us what your level of expertise is?

---

### Post by prshah on 2009-07-17
> **TStarboy said:**
> upon reaching the login screen, the display shows a black screen with the bottom half blue. Pressing Alt+f1 just shows some garbage at the top of the screen. 

Take a look at [ this post with screenshots]("http://ubuntuforums.org/showpost.php?p=7132514&postcount=2") to see if it matches your problem. The solution is also included. Post back if you need more advice.

---

### Post by TStarboy on 2009-07-17
[quote=Prshah]Take a look at [ this post with screenshots]("http://ubuntuforums.org/showpost.php?p=7132514&postcount=2") to see if it matches your problem. The solution is also included. Post back if you need more advice.     [/quote]I seem to have a similar problem as the person in that post, but those screenshots do not match my screen. Pressing Ctrl+Alt+F1 gives me the same garbage. It's just random red squares at the top of the screen. I have an Envision LM-700 monitor, and a VIA/S3G Unichrome IGP that came with my computer. This problem started for me a while after installing Ubuntu (I believe 2 months). I think I may have uninstalled Kubuntu (The desktop environment only) before this, but as I usually hibernate, I had not encountered this problem. I had first installed Ubuntu 9.04 (I have not upgraded). My level of expertise is low, but I am not afraid to go into the Terminal for anything.

---

### Post by mathay on 2009-07-17
Did this occur after an upgrade?

I'm assuming that after installing Ubuntu things worked well. Did you know if anything had altered Xorg prior to your issue?

---

### Post by TStarboy on 2009-07-17
> **mathay said:**
> Did this occur after an upgrade?

I'm assuming that after installing Ubuntu things worked well. Did you know if anything had altered Xorg prior to your issue?
No upgrade. This just happened, I have no idea what happened. Would it be easier to just do a fresh install? I've backed up important data already.

---

### Post by mathay on 2009-07-17
I mean, if your important files are backed up, it shouldn't be a problem but solving it would be more convenient. 

Did you happen to try the fix in that linked thread?

Furthermore, what graphics card are you using?

---

### Post by TStarboy on 2009-07-17
Graphics card is the VIA that came with my HP Pavillion a714x. 

TRIPLE EDIT: I tried Tomdkat's fix method from that thread and it now works. Thank you all.

---

