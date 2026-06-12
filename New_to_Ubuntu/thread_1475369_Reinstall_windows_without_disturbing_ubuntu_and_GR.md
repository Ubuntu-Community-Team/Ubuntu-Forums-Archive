---
title: "Reinstall windows without disturbing ubuntu and GRUB?"
date: 2010-05-06
forum: New to Ubuntu
---

### Post by nash black on 2010-05-06
Hi

I am running ubuntu and windows in a dual boot. They are on separate drives, but they can both access one partition of the drive on which linux is installed. 

I would like to reinstall windows (keeping my old windows files). I've done this once before, but not with a dual boot. Is there a way to go about doing this without disturbing GRUB and the linux partition? Will it just automatically install only on the partition that currently has windows?

Thanks
Nash

---

### Post by quixote on 2010-05-07
If grub is currently on the drive with the windows OS, then reinstalling windows will overwrite it.  But then all you have to do is [reinstall grub afterwards]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202"), which is really easy.  (Honest!)

Is the partition accessed by windows which is on the linux drive a data partition of some kind?  Unless it has operating system files on it (which seems unlikely), then it wouldn't be affected by a reinstall of windows.

---

### Post by mister_playboy on 2010-05-08
> **quixote said:**
> If grub is currently on the drive with the windows OS, then reinstalling windows will overwrite it.  But then all you have to do is [reinstall grub afterwards]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202"), which is really easy.  (Honest!)

Windows isn't interested in playing nicely with grub... you'll have to reinstall it afterwards.

---

### Post by booshire on 2010-05-08
If grub is on a separate drive from windows you can pull the linux HD and install windows by itself. Plug the linux drive back in and update grub with the new information. You will have to use the drive mapping function, which is pretty straight forward, to make windows think it is actually on hd0,0 like when you installed it. I used to do this all the time on a test server with hot swappable drives and never had any issues with it. You will just have to add the shared partition after you get it up and running, windows makes that part pretty easy.

---

### Post by sadaruwan12 on 2010-05-08
If you have the grub on another drive then it's much easy remove the cable and install windows then reinsert the cable but if you have the grub on the same drive as the windows you've to reinstall afterward.

But don't worry it's quite easy.

---

### Post by nash black on 2010-05-08
The set up is like this
HD1) Windows XP pro
HD2) Ubuntu 10.04, GRUB and another partition that can be accessed by either os. It doesn't have system files from either on it

It sounds like unplugging the second HD would be the way to go. I just did some cleaning on the windows partition and its working pretty well now, so I actually won't be doing this now... But I'm sure I will need to in the future, so thanks a lot.

---

