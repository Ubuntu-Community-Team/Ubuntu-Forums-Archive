---
title: "icons in appearance menu messed up"
date: 2010-02-27
forum: New to Ubuntu
---

### Post by labatts on 2010-02-27
Hi all.  Thanks in advance for the help.

I am having a problem with the icons in the appearance menu.  Instead of showing the appropriate folder and color, it only shows a black square (see attachment).  So questions are:

1.  What can I do to get them to show correctly?
2.  Anyone have any idea what I did to screw it up (lol) in the first place so that I can avoid repeating the mistake?

What I have already tried / noticed

The changes take place immediately in the netbook switcher interface (at the top of the screen, I forget what it is called), but require a log out and log in to effect the menu interface.  I THINK that is not normal, but I don't really know.  You can see this behavior in the attachment.

I labeled this a UNR issue, but it also happened on my desktop that has ubuntu desktop installed via Wubi.  

I installed the extra icons via gnome art manager.  I have no idea if that is part of the problem, because I wasn't configuring the appearance very often before that.  In an effort to fix it I uninstalled the icon packages via synaptic.(this actually worked on the desktop version for SOME of the icons, but not on UNR).

Some people in a different place suggested that it may be due to KDE stuff, so I tried to get rid of all things KDE (I was using Ocular and Semantic), but I have no idea if I was successful or if it is even relevant (doubtful). 

Again, thanks for any help.

---

### Post by spiderbatdad on 2010-02-27
the appearance looks to me like missing files...as you probably thought.
Is this install also wubi?
not sure what the problem is but it might be worth looking for default installed themes in synaptic to make sure you have them...like:
gnome-themes-ubuntu, gnome-themes-selected, hicolor-icon-theme, humanity-icon-theme,

---

### Post by labatts on 2010-02-27
To answer your question, the UNR is not from Wubi.  It is a clean install.  I will check the files you suggested to make sure they are present and post a further response. 

Thanks

---

### Post by labatts on 2010-02-27
Okay, I checked and yes.  I do have all the files you mentioned installed.  For 'S&G', I reinstalled these packages (synaptic) to see if it would help.  Now I have an x instead of a black square (see attachment).  

Aside from having to log out, they do seem to be working.  I simply can't tell what the heck they will look like (gnome-wine is fairly obvious, but who knew that gnome-wise would be green?)

---

### Post by labatts on 2010-02-27
Yes, well.  Your mac4lin Icons inspired me to download some macish icon sets from art manager.  Now, all the sudden, everything looks great (i still have to log out to get the full menu change, but I can deal with that.  it might even be standard, I just never noticed it before. see updated screenshot i guess).  

At any rate, I suspect you are right about there being some missing package.  It must have been reinstalled when gnome art manager did its thing.  If anyone thinks there is some other reason why all this happened (I would like to avoid a repeat) please let me know.  

Otherwise, Thanks for the help!

---

### Post by spiderbatdad on 2010-02-27
glad to hear you are mostly sorted out. Tricky trying to guess at what might have happened...bad theme installed broke the gtk app that manages the themes. I really have no idea. :p

---

