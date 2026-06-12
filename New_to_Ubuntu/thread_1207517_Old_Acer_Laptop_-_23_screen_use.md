---
title: "Old Acer Laptop - 2/3 screen use"
date: 2009-07-08
forum: New to Ubuntu
---

### Post by Ian-on-the-Trent on 2009-07-08
A strange thing happened on the way to the forum...

I'm trying to install Xubuntu 9.04 on an old Acer 213TE laptop. Weirdly, only 2/3 of the LCD screen is used.  It's not as if the screen resolution has been reduced, it is the physical area of the screen that is not being used. However, if I plug a monitor into the laptop, everything is as it should be.

Any thoughts?

(btw, I couldn't install Ubuntu 9.04 desktop; the install would hang at the partition set-up stage. Now with Xubuntu, it seems to have hung up at the "Who are you" stage. I'll report back on this should it permanently hang. BTW, the HDD was completely written with zeros prior to attempting the installation.)

Acer 213TE / 850mhz Celeron / 20gb HDD / 256mb RAM

---

### Post by alexlafreniere on 2009-07-08
If you're having installation problems, try the alternate installation CD, the non-LiveCD version. It doesn't have all the pretty menus, so you know if that doesn't work there's something more serious wrong with it. And just a little clarification on the screen problem, is it displaying the whole image, just squished along the sides? If that's the case, look for the display menu buttons, specifically the "auto-adjust" button. The screen image frequently gets squished along the sides or "falls off" the edges of the screen during installations. Just hit auto-adjust once and you should be fine.

---

### Post by Ian-on-the-Trent on 2009-07-08
> **alexlafreniere said:**
> ...try the alternate installation CD...And just a little clarification on the screen problem...Just hit auto-adjust once and you should be fine.

Hi Alex, thanks for your reply.

Yes, I will download and try the alternate CD. I am beginning to wonder if I may have a damaged CD/DVD player. Hmmm.

The physical screen area is shrunk, that is, I am getting the 1024x768 screen resolution at about an 8inch/20cm screen usage instead of the full screen's 13.4/34cm diagonal. I didn't know my laptop had an auto adjust.

---

### Post by alexlafreniere on 2009-07-08
> **Ian-on-the-Trent said:**
> 
The physical screen area is shrunk, that is, I am getting the 1024x768 screen resolution at about an 8inch/20cm screen usage instead of the full screen's 13.4/34cm diagonal. I didn't know my laptop had an auto adjust.

Almost every laptop does, the buttons are just very nondescript. If it doesn't have a dedicated button it may be on a function key.

---

### Post by Ian-on-the-Trent on 2009-07-08
Started an installation using the Ubuntu alternate CD. Got to the point where an error persisted:

[!!] Install the base system
Debootstrap Error
Failed to determine the codename for the release.

I'll start a new thread on this topic.
(Using this thread for now: [http://ubuntuforums.org/showthread.php?p=7582568#post7582568](http://ubuntuforums.org/showthread.php?p=7582568#post7582568) )

---

### Post by Ian-on-the-Trent on 2009-07-09
**Ubuntu 9.04 desktop now successfully installed.**

Regarding the new debootstrap error, I referred to [http://www.debianhelp.org/node/2031](http://www.debianhelp.org/node/2031). Based on a suggestion in the link, that the DVD/CD drive might be too old, I replaced the drive with a newer one. Lo and behold the alternate install completed...no debootstrap errors.

But with regard to the 2/3 screen usage...so long as an external monitor is plugged in during the boot, I get full screen use even after I remove the monitor. Without it plugged in at the boot though, just 2/3 of the screen is used.  I cannot find an auto-adjust button or function.

---

### Post by Ian-on-the-Trent on 2009-07-09
Back to my original topic: Why the heck does only 2/3 of the LCD screen get used when I boot without a monitor plugged into the laptop. Obviously. the laptop detects the monitor connection and makes an adjustment.

I've gone through the laptop owner's manual but could not find any reference to a screen auto-adjust...or any similar term for that matter. No function/hot keys either.

Any suggestions?

---

### Post by alexlafreniere on 2009-07-09
Could be a graphics driver problem. Because it's an old laptop I'm assuming it's integrated. Try reinstalling graphics drivers?

---

### Post by Ian-on-the-Trent on 2009-07-09
> **alexlafreniere said:**
> Could be a graphics driver problem. Because it's an old laptop I'm assuming it's integrated. Try reinstalling graphics drivers?

Hi again Alex.

I'm assuming that the drivers should be the ones that came with Ubuntu?

---

### Post by LewRockwell on 2009-07-09
> **Ian-on-the-Trent said:**
> A strange thing happened on the way to the forum...

I'm trying to install Xubuntu 9.04 on an old Acer 213TE laptop. Weirdly, only 2/3 of the LCD screen is used.  It's not as if the screen resolution has been reduced, it is the physical area of the screen that is not being used. However, if I plug a monitor into the laptop, everything is as it should be.

Any thoughts?

(btw, I couldn't install Ubuntu 9.04 desktop; the install would hang at the partition set-up stage. Now with Xubuntu, it seems to have hung up at the "Who are you" stage. I'll report back on this should it permanently hang. BTW, the HDD was completely written with zeros prior to attempting the installation.)

Acer 213TE / 850mhz Celeron / 20gb HDD / 256mb RAM

IMHO, I wouldn't be happy with ubuntu or kubuntu on that machine but you may be able to tolerate it, especially if you max the ram.

If the machine were here the first thing I would do is throw a Damn Small Linux and/or Puppy Linux LiveCD in it and see how both of those performed.

I'm guessing that a manual editing will be required if your problem persists.

Side-thought: Is the latest BIOS installed?

keep us posted

.

---

