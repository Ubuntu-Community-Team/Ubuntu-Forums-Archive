---
title: "what happened here?!"
date: 2009-06-07
forum: New to Ubuntu
---

### Post by Matt26 on 2009-06-07
ok, i don't know what's going on with my ubuntu system right now, but for some unknown reason, all of a sudden things have gone rather wrong here... it started with my pidgen application becoming unresponsive, so i decided to restart the computer- harmless, right?

no, not quite- since rebooting my computer, i now have the following issues:

- my evolution email client no longer has my configuration settings, and is now asking me to reconfigure it- which means (if i'm correct) that ALL of my saved emails, directories, contacts (i could go on here) are all lost.

- firefox freezes on session startup now, and even if i choose the last good session and restart firefox, it still crashes the same way.

- ALL of my firefox bookmarks are gone- the bookmarks menu is next to empty now.

- pidgin is STILL unresponsive and will not do a thing when i click on it.

this is what i have discovered thus far- i wouldn't be surprised to find more along the way...

so can anyone shed any light on this particular matter and please tell me what i can do to fix any of these issues?

i have not installed or removed any hardware and otherwise the only things i have done recently are completely reinstalled openoffice.org and run a system backup with remastersys.

as a result of this whole mess, i'm writing this post from one of my Windows XP systems because firefox does not seem to respond when i click the Log in button on the ubuntu forums site!

oh, and i just noticed that sleep mode has just kicked in on my ubuntu system monitor- i do NOT have sleep mode set up!

---

### Post by furialis on 2009-06-07
I've never tried [this]("https://help.ubuntu.com/9.04/installation-guide/amd64/rescue.html"), but it might help.

---

### Post by QIII on 2009-06-07
Firefox (I'm sure) and Evolution (I would guess) should have configuration files somewhere.  You might be able to recover those, put them somewhere you can find them later, reconfigure or reinstall both apps and then restore your configurations.

Have never used remastersys, but if your problem started after that, it might be suspect.

I wouldn't think uninstalling and reinstalling OOO would cause a problem, but I do recall a post about it as I was surfing through posts one night.

I'd never be able to tell you where it was.

(I hate it when people tell me this, but ...) see if you can google something about where each of those applications keep their configuration/preference files in whatever version of Ubuntu you are using.

And if you find a solution,  PLEASE post it back here as solved so we can all learn how to help the next guy.

Let us know if you run into a roadblock and I'm sure everyone will be happy to pitch in with more ideas.

---

### Post by pspsampsp on 2009-06-07
have u changed any settings lately or installed anything ? cause those are some pretty major problems , sorry i cant help more.

---

### Post by ad_267 on 2009-06-07
It could be an issue with the hard drive. You can boot from a LiveCD and use fsck to check the file system.

---

### Post by presence1960 on 2009-06-07
Hopefully you are a prudent computer user and have a backup of your home partition or directory. All your config files for FF, pidgin, etc are in there. If you do have a backup restore it. You could also try removing and reinstalling programs after restoring home if they still act goofy.

---

### Post by Matt26 on 2009-06-07
i'll try booting with a live cd and doing a file system check for now...

where do evolution and firefox keep their configuratoin files?

---

### Post by Bearly Able on 2009-06-07
Firefox keeps its files in a hidden folder called .mozilla inside your home folder. (Press Ctrl+h to view hidden files.)

I had to do a fresh install yesterday after problems with Jaunty, but I just copied over my Firefox and Thunderbird files and everything was still there - beautiful.

---

### Post by Matt26 on 2009-06-07
anyone know where Evolution keeps it's configuration files?

---

### Post by yoda2031 on 2009-06-07
> **Matt26 said:**
> anyone know where Evolution keeps it's configuration files?

> 
c@war1ock:~$ ls -la | grep evolution
drwxr-xr-x  8 c    c          4096 2009-05-03 21:35 .evolution
c@war1ock:~$


It appears that evolution version 2.26.1 stores them in ~/.evolution/

---

### Post by oldsoundguy on 2009-06-07
I had all types of issues similar to those described on one computer and it turned out to be HARDWARE RELATED. Eventually it would not even boot.  Turns out it was a defective CMOS chip and I had to replace the mother board.  (so I upgraded) Once that was accomplished, everything worked fine and is still working fine.

Not ALL issues are software related as the stuff DOES wear out!

Two good tools to have are "Ultimate Boot disk" and "Hiren's Boot disk".  Both free from the web.  Burn the ISO and boot to them and use the various utilities to test your hardware  (that is provided the board will boot to POST (CMOS).

At least you know where you stand then and can go from there.

---

