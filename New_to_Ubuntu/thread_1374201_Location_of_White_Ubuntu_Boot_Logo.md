---
title: "Location of White Ubuntu Boot Logo"
date: 2010-01-06
forum: New to Ubuntu
---

### Post by Groucho Marxist on 2010-01-06
I'm customizing my Ubuntu 9.10 system into my fictional distro Batbuntu ("Linux For Dark Knights"). As such, I'm interested in changing the white boot logo to my custom Batbuntu image. Does anyone here know the path to the white Ubuntu boot logo?

---

### Post by warfacegod on 2010-01-06
At a guess:

/usr/share/themes

---

### Post by Groucho Marxist on 2010-01-06
> **warfacegod said:**
> At a guess:

/usr/share/themes

Thanks for the suggestion; I checked and couldn't find it :(

---

### Post by warfacegod on 2010-01-06
Try searching for splash or xsplash or something like that.

---

### Post by Groucho Marxist on 2010-01-06
> **warfacegod said:**
> Try searching for splash or xsplash or something like that.

Searched splash and couldn't find it; I've already edited my xsplash login image, but that was a helpful suggestion nonetheless.

---

### Post by bodhi.zazen on 2010-01-06
I am not sure, but I think it is somehow compiled into initrd, but I do not know how exactly.

---

### Post by Groucho Marxist on 2010-01-06
> **bodhi.zazen said:**
> I am not sure, but I think it is somehow compiled into initrd, but I do not know how exactly.

D'oh! Well, until we can figure out how to edit it, I am in no way going to mess around with any boot-related files.

---

### Post by AlexanderDGreat on 2010-03-16
I came from a Minimal Install in Karmic. Installed xsplash for that nice Ubuntu, darkish-silver-black thingy. But I don't know how to make the white logo appear each time I boot. So my station now says, fsck Linux=, etc... I hope it was as easy to install in Synaptic.

---

### Post by AlexanderDGreat on 2010-03-25
Found that white logo it's in the package usplash in Synaptic.

---

### Post by towheedm on 2010-04-29
> **Groucho Marxist said:**
> I'm customizing my Ubuntu 9.10 system into my fictional distro Batbuntu ("Linux For Dark Knights"). As such, I'm interested in changing the white boot logo to my custom Batbuntu image. Does anyone here know the path to the white Ubuntu boot logo?

You will not find a file containing the graphics of the logo.  The screen it shows up on is called the Usplash screen.  The logo is part of the Usplash theme which is compiled as a [COLOR=Red]shared object[/COLOR] file.

If you are interested in changing or creating your own Usplash theme check out the link at the beginning of this thread:
[http://ubuntuforums.org/showthread.php?p=9068333#post9068333](http://ubuntuforums.org/showthread.php?p=9068333#post9068333)

If you need help post a reply the above thread.

---

