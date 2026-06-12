---
title: "iBook, wont launch any applications"
date: 2009-02-14
forum: New to Ubuntu
---

### Post by ant2ne on 2009-02-14
Please forgive me; I don't intend to double post. I first posted this problem in the Apple section, then I got to thinking that maybe this problem isn't apple specific. Mods, please remove whichever post is less useful.

My apple post [here]("http://ubuntuforums.org/showthread.php?p=6732181#post6732181") In which I say....

I got this installed, and with some work I can login
[http://ubuntuforums.org/showthread.php?p=6732169#post6732169](http://ubuntuforums.org/showthread.php?p=6732169#post6732169)

My problem now is, clicking on any icon acts like it is going to load the program but the program instantly crashes. I click Applications, Accessories, Terminal and the terminal window pops up for just a second and then poof it is gone. I click the fire fox icon and the cursor spins, and then stops, but nothing loads. I goto Synaptic, and the same thing happens. Now what?

___________

---

### Post by ant2ne on 2009-02-14
Plot thickens. I click Applications | Settings | Desktop and then check Allow Xfce to manage the desktop and icons pop up on the desktop for Filesystem, Home, Trash, etc. Then when I try to launch an app (which crashes) They all go away, until I check the box again. Almost as though it wont let me make xfce manage the desktop.

---

### Post by ant2ne on 2009-02-14
Toyin with my xubuntu emac (yes I have an ibook and emac with xubuntu) it wont load thunar

---

### Post by ugm6hr on 2009-02-14
Try running Terminal:
Alt+F2
Command: xfce4-terminal
Select "Run in Terminal" (if XFCE gives that option).

If that works - try running firefox from there:
```
firefox %u
```

I wonder whether the problem was actually with the original install CD.  Sounds like you had a lot of probelms which are unusual.  Did you check the install CD for errors?

---

### Post by ant2ne on 2009-02-14
I resoled by installing debian's xfce. It worked rather flawlessly. 
[http://cdimage.debian.org/debian-cd/4.0_r7/powerpc/iso-cd/](http://cdimage.debian.org/debian-cd/4.0_r7/powerpc/iso-cd/)

I did have a resolution problem that was sovled by this thread
[http://ubuntuforums.org/showthread.php?t=261241](http://ubuntuforums.org/showthread.php?t=261241)

I'm now moving onto the next phase of my project. Thanks for the attempts/

---

### Post by cyberdork33 on 2009-02-15
this is known problem in the PPC version of Ubuntu. Try the "fix gnome" section here:
[http://ubuntuforums.org/showpost.php?p=6560159&postcount=1](http://ubuntuforums.org/showpost.php?p=6560159&postcount=1)

---

