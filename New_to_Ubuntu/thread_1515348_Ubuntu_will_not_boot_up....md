---
title: "Ubuntu will not boot up..."
date: 2010-06-22
forum: New to Ubuntu
---

### Post by BluBird on 2010-06-22
Hello.  I have only a little experience with Ubuntu, as I have it on my dell Inspiron b130.  Anyway, I recently got a new computer, a Toshiba Satellite A505.  I believe the sub-model is 6033.  Anyway, some of it's specs: it's an i7 with a 500gb hard drive, wireless N, and has a NVIDA GeForce Graphics card.  I've run Ubuntu 10.04 off of the disk when I set it to "nomodeset," and it worked very well and I was extremely impressed.  Alas, when I installed Ubuntu in place of windows (I was informed that windows 7 does not take well to having an operating system installed over it for a dual boot system, that it works best to install Ubuntu and then reinstall windows next to it.), it does nothing.  I don't even see the BiOS screen.  I load up the computer, the screen goes black with a white blinking dash to inform me that it's still working, then some writing pops up real quick, too quick to read, and the screen goes blank.  the lights on the computer are still on, but nothing.  I'm lost.  please help!

[edit] by sticking the Ubuntu Live CD in the computer, I got it to stop at the writing.  it says:

[          10.109748]  [drm]   mouveau 0000 :01 :00 .0 Pointer to BIT loadval table invalid

What does this mean?

[edit 2] i've gotten the bios screen back.  apparantly i had gone into bios and set it to fast boot, and the screen itself doesnt show up.  now that I have set it back to normal, it looks like i can load up the ubuntu Live CD, but still not ubuntu off of the hard drive.

---

### Post by Paqman on 2010-06-22
When you install Windows, it will have nuked Grub. You'll need to [reinstall Grub]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows").

---

### Post by BluBird on 2010-06-22
Good to know, but unfortunately, I'm not up to that point yet.  First, I need to get Ubuntu up and running.  I tried re-installing Ubuntu 10.04, but yield the same results of blank screen after BiOS

---

### Post by philinux on 2010-06-22
> **BluBird said:**
> Good to know, but unfortunately, I'm not up to that point yet.  First, I need to get Ubuntu up and running.  I tried re-installing Ubuntu 10.04, but yield the same results of blank screen after BiOS

Does the livecd run ok?

---

### Post by BluBird on 2010-06-22
when i'm prompted as to what I want to do (ex: run ubuntu without installing, test hard drive, check disk for errors, install ubuntu, etc), as long as I hit f6 and select "nomodeset," it runs fine.  It takes a little while to boot up off the disk, but once booted up, its faster than windows 7 was.  the problem only seems to be running it off of the hard drive.

---

### Post by Paqman on 2010-06-22
Ok, so you can get it installed, but you can't actually boot it? You need to edit your Grub entries so that they include the "nomodeset". To get booted you can hit "e" at the Grub prompt and add that to the line with the kernel on it. If that gets you to a working desktop we can point at the file to modify to make the change permanent.

---

### Post by BluBird on 2010-06-22
i remember the grub prompt on my old laptop, where it counts down from 5 before going to the ubuntu splash screen.  on this computer, I don't seem to have that.  for only a fraction of a second, it seems to display this message:
 
[ 10.109748] [drm] mouveau 0000 :01 :00 .0 Pointer to BIT loadval table invalid
 
before going to a blank screen.  I've tried reloading ubuntu, but to the same effect.

---

### Post by BluBird on 2010-06-22
Anyone?

---

### Post by wilee-nilee on 2010-06-22
Post the bootscript in my signature. Paste the results to a reply highlight the txt and click on the # (code tags) in the reply panel.

---

### Post by BluBird on 2010-06-23
ok, but how do I get to terminal?  I don't get a chance to do anything.  After I push the power button, the bios loads, the writing "[          10.109748]  [drm]   mouveau 0000 :01 :00 .0 Pointer to BIT  loadval table invalid" appears for a brief moment, and then it goes to a blank screen.

---

