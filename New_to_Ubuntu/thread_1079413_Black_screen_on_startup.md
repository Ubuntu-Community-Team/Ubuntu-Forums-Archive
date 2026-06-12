---
title: "Black screen on startup"
date: 2009-02-24
forum: New to Ubuntu
---

### Post by Wotcher on 2009-02-24
I just installed Ubuntu 8.10 from XP (as a program). And now when I choose Ubuntu on the boot menu all I get is a black screen.

What's gone wrong? I've tried seeing other posts regarding a black screen on startup, but they have other problems. I performed a simple install from XP and after choosing Ubuntu on the boot menu the screen just stays black. There's no splash, no progression bar, no sign of any graphics at all.

---

### Post by avtolle on 2009-02-24
Well, the mere fact that you installed through Wubi doesn't make your problem any different than if the installation had been to a separate partition creating a "true" dual boot. That said, can you boot into recovery mode and get a command line? If so, then see if typing startx will get you a desktop.

---

### Post by Wotcher on 2009-02-24
Ok, so I entered recovery mode, it went throught a list of actions, and the last one on the screen was "Activating swapfile swap." It's stayed like this for a couple of minutes. So I wrote startx on that screen. Hasn't done anything. I don't think this is a command line. How do I get it?

---

### Post by avtolle on 2009-02-24
Thinking out loud here; have you done a "hard" shutdown of your system recently? If so, you might run chkdsk -r from the XP side to see if that fixes anything. Actually, to be precise, I'd recommend removing Ubuntu using the Windows tool for that; run the above command; also, defrag the drive (at least twice, using the Windows tool); then reinstall Ubuntu with Wubi (should you desire to do so). It sounds like there's a problem with the swap partition, which is often caused by a badly fragmented HDD prior to installation.

---

### Post by Wotcher on 2009-02-24
Yes I've had to force the computer to shut down.

Alright, thanks for the advice.

---

### Post by Wotcher on 2009-02-24
Ok, I've done all you told me to do. And I've reinstalled Wubi. Now on boot up, after I choose Ubuntu, it takes me to a screen with some writing on it. It tells me that I can hit TAB for a list of acceptable commands and it has a prompt that looks like this:

GRUB>

So, Ubuntu isn't even loading I guess. Any help will be greatly appreciated.

Wotcher

---

### Post by Wotcher on 2009-02-25
BUMP

If anyone has any ideas, please help.

---

### Post by avtolle on 2009-02-25
Take a look at [http://ubuntuforums.org/showthread.php?t=960740](http://ubuntuforums.org/showthread.php?t=960740) and see if this helps.

---

### Post by Wotcher on 2009-03-08
> **avtolle said:**
> Take a look at [http://ubuntuforums.org/showthread.php?t=960740](http://ubuntuforums.org/showthread.php?t=960740) and see if this helps.

Thank you for your help. But this is just too much hassle to have Ubuntu. I always have to be fixing something so that it will work.

Maybe when it's more user friendly...

Wotcher

---

