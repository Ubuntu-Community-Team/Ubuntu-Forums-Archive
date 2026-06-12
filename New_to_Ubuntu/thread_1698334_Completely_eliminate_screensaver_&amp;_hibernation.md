---
title: "Completely eliminate screensaver &amp; hibernation on desktop PC?"
date: 2011-03-02
forum: New to Ubuntu
---

### Post by 2CV67 on 2011-03-02
As part of a so-far-fruitless attempt to fix another problem:
[http://ubuntuforums.org/showthread.php?t=1579256](http://ubuntuforums.org/showthread.php?t=1579256)

I have been trying to completely eliminate all screensaver effects.

I started by completely removing Gnome-Screensaver using SynApt.

Following that, I was surprised to find that after exactly 10 minutes, my screen briefly said "No Signal" then went black.
It woke up immediately on mouse movement.

Looking for other screensaver-type mechanisms, I found:
System > Preferences > Power Management > On AC Power > Display > Put display to sleep when inactive for: 0:15
I suppose that should shut down after 15 minutes, but my screen shuts down after 10 minutes.
I re-set to 1 minute & it did shut down after about a minute.
I re-set to "Never" but that did not make any difference, my screen still shuts down after 10 minutes.

Can anybody tell me what is causing this behaviour?
Is it normal (surely not) ?
What do I need to do to stop all screen shut-downs?

If anybody has any suggestions on my original problem:
[http://ubuntuforums.org/showthread.php?t=1579256](http://ubuntuforums.org/showthread.php?t=1579256)
that would be very welcome too!

Thanks!

---

### Post by mastablasta on 2011-03-02
it's certianly not normal. ther eis porbably a setting in some file that tells the screen to shut off.
back to original problem - plenty upgrades done there :-) have you tried with a clean install? 
 
My dad has 9200 but i haven't tried latest Ubuntus there i think i gave 9.10 a spin, but i am not sure.
 
Ok here is a silly suggestion (if you can easilly afford to erase system partition) - try to make a fresh install but go KDE. Just to see if the login, logout bug is there as well. or XFCE if you htink KDE would be too heavy. At leats then you know if desktop is at fault. 
 
KDE works a bit different. some things are done better, some are stupid or half done. but it's still a nice environment. I just instaleld Kubuntu (LinuxMint even uses latest 4.6 version). I am knowcking donw issues one by one and so far progress is good and at the moment it all works better than in Ubuntu's gnome. I kept Gnome on ald notebook, cause i don't have problem with it there.
 
KDE even asks if you want to autologin -  i mean why not since it's only one user using it. LOL. I use an old Radeon 9600XT. works very nice. almost all effect work, though i have them disabled. even the power management, suspend, hibernation, autooff... now work. i had other problems but as i said slowly i am solving them. today's topic will likely be WINE :-)

---

### Post by grahammechanical on 2011-03-02
There are power saving settings in the BIOS program. Perhaps it is one of these that is shutting down the display after 10 minutes.

Or, if the monitor is an LCD screen TV/monitor combined as is my screen then there are power saving settings in the monitor itself. It is most probably a legal requirement for manufacturers to provide these functions.

Regards.

---

### Post by 2CV67 on 2011-03-04
I did a bit more digging.

I visited my XP OS on the same PC.
I found the screensaver set to off & the monitor switch-off set to 20 minutes.
Sure enough, it switches off after 20 minutes, not 10 minutes.

Presumably that rules out anything in BIOS or in the monitor ?

Then I looked in my "other" Ubuntu OS (LTS 10.04).
There I found the screensaver set for 5 minutes & the Power Mangement for 30 minutes.
And that was exactly what happened.
Both screensaver & power management will do exactly what I choose to set them to.
Next, I used Synapt to uninstall gnome-screensaver.
After reboot, power management could be used OK to set times less than 10 minutes, but if set beyond 10 minutes (or "Never") the screen still went black after 10 minutes.
That was exactly the situation I had in my main Ubuntu at the start of this thread.

So I went back to 10.10 & re-installed gnome-screensaver.
Now (after reboot) I can set power management to anything I like & it does what I ask...

Conclusion:
If I uninstall gnome-screensaver, then power management is over-ruled by something else if set beyond 10 minutes.
I wonder what is doing that?

---

