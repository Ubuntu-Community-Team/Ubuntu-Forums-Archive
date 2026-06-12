---
title: "Which way to install for duel-boot"
date: 2010-04-26
forum: New to Ubuntu
---

### Post by joenewtzie on 2010-04-26
Ok, so i'm really fed up with windows 7 right now and I just want to duel-boot.  Here are my questions:
1) Which installation method should I use? I looked online at Ubuntu help and they say to install using the disk and use the first option BUT this guy on YouTube ([http://www.youtube.com/watch?v=m5Jxfj6tu_U](http://www.youtube.com/watch?v=m5Jxfj6tu_U)) does it a completely different way. 
2) If I duel-boot using whichever method, do I lose anything from windows 7? 

Please let me know which way is the best to duel-boot especially for a beginner Linux user. 

Also,
I did attempt to install Linux on my USB flash drive and now I have to have that USB drive in to load GRUB and to select Windows 7 or Linux BUT when I pick Linux it flashes and asking me for my username and password. I can put my username in BUT not my password.  It won't let me type anything.  Not sure if thats a problem or not but i'm sure if we just reinstall it again somehow on the hard-drive then it will work fine.  Please let me know you opinions and sorry for the long question, I really don't know where else to go.

---

### Post by pricetech on 2010-04-26
I'm not sure why you're having a problem with your thumbdrive install, but here's my advice on dual booting.

Go ahead and install to the hard drive.  Use guided partitioning and read carefully what it says about allocation space for Ubuntu.  Others might recommend manual partitioning, but I don't for a beginner.

BEFORE you install Ubuntu, defrag your hard drive under windows.  The first time you boot windows after you resize and install Ubuntu, it will want to run check disk.  Let that run and windows should be happy.

Have fun and welcome.

---

### Post by HarrisonNapper on 2010-04-26
Also if Windows is installed to the entire drive, you will need to shrink the primary partition from the Windows MMC.

---

### Post by joenewtzie on 2010-04-26
Ok, so the plan is to use the first option like the ubuntu help page recomends and then defrag the hard drive under windows before the install. Just to make sure, I can't remember but the defrag won't delete everything on the hard drive right?

---

### Post by HarrisonNapper on 2010-04-26
No, defrag will only fix things. You will need to shrink it, as I said, if Windows is the only partition. Otherwise, your Windows data could get messed up.

---

### Post by joenewtzie on 2010-04-26
Ok awesome, I'll give that option a shot then! Thanks alot everyone!

---

### Post by Hospadar on 2010-04-26
Be sure to back up your windows data!

I think the installer is pretty straight-forward and if you pay attention to what it says, there's very little chance you'd wipe out important data.  That said, if you aren't sure what you're doing (for example installing ubuntu for the first time) it's very possible you could wipe something out that you didn't want to loose.  The best defense against that kind of scenario is to back up all your important documents (which isn't a bad idea anyways since your traitorous hard drive could die at any moment)

---

### Post by joenewtzie on 2010-04-26
Well, I have a large hard drive and I recently purchased a external hard drive and backed EVERYTHING up to it and then re-installed Windows 7, so there really isn't much to lose. I just want to make sure I don't fully un-instal windows because I do want to use it for some programs.

---

