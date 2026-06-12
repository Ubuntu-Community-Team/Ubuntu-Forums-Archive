---
title: "How Do I Get A List Of All My Ubuntu Apps?"
date: 2010-02-07
forum: New to Ubuntu
---

### Post by Roger Allott on 2010-02-07
I've just installed Ubuntu on a second-hand desktop PC I bought from someone. It's hardware is of course completely different to that of my laptop, on which I've got a nice mature installation of 9.10.

What I want to do is to duplicate my laptop's Ubuntu on my new desktop PC.

The first task is to duplicate the Software Sources. No problem there.

My second task is to duplicate the packages I've installed that are not hardware-specific. And that's where I'm hitting a problem.

I've tried doing a Save Markings As thing in Synaptic, but all I get is an empty file. But that's not really what I want anyway, as it'll list the hardware-specific packages that I don't want, and all the dependencies that I don't need.

So, does anyone have any idea of how I can get a list of all my non-hardware-specific top-level software apps?

The third task is to copy across my home directory from one disk to the other. No problem there I think.

---

### Post by presence1960 on 2010-02-07
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)

---

### Post by tom.swartz07 on 2010-02-07
> **presence1960 said:**
> [http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)

+1 for that script.


Personally, Ive never had trouble with the "save markings" route, maybe its because the file is owned by root? Did you perhaps try changing the owner?

---

### Post by Chris Edgell on 2010-02-07
Oh, so interesting!  Yes, Presence, great link!

And tom.swartz07 you made me go and explore Synaptic setup.  (Sometimes I forget to look around)...now I've found that save markings...I'm glad you say it works.  What do you think of that History feature...?  I'm thinking if I have a file of all the markings, I wouldn't need that.

---

### Post by warfacegod on 2010-02-07
This should produce a list of all packages:

```
dpkg --get-selections | gawk '{ print $1 }' > ~/InstalledPackages.txt
```

---

