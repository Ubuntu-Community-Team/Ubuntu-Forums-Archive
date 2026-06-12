---
title: "Suppositries needed for command line?"
date: 2009-10-09
forum: New to Ubuntu
---

### Post by smileyguy on 2009-10-09
I know that to get apps from the Synaptics package manager I need to add suppositories (or use the ones already installed) but I used the command line to download an app from this page

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

command: 
 sudo apt-get install libdvdread4
My question is - does using the command line go to the suppositories? AND if it does, why can't I find libvdread4 in Synaptics Package Manager?

---

### Post by smileyguy on 2009-10-09
Sorry - I did just find libdvdread4 but still am curious about the command line & repositories

---

### Post by MelDJ on 2009-10-09
the command line is like a CLI version of synaptic. if you want to see all the programmes you can get in a not fully text version, type sudo aptitude

---

### Post by Paqman on 2009-10-09
Lol, it's repositories. [Suppositories]("http://en.wikipedia.org/wiki/Suppository") are something else entirely ;)

To get libdvdread4, make sure you have the Universe repo enabled. In Synpatic, go to Settings > Repositories and make sure Universe is checked. Reload your sources and it should be there.

Synaptic Package Manager and the apt-get command are both exactly the same thing. The underlying package manager is called [APT]("http://en.wikipedia.org/wiki/Advanced_Packaging_Tool"). That's whay it's called Syn**apt**ic.

All the different ways to install software (Synaptic, Add/Remove, Ubuntu Software Centre, apt-get, aptitude, Update Manager, gdebi) all use APT. If the software is available from a repo, that's where APT gets it from, unless you've already got the .deb cached on your system.

---

### Post by smileyguy on 2009-10-09
Thanks - very clear.

No wonder my doc looked at me funny when I asked for a repository!

---

### Post by Captain_tux on 2009-10-09
> **Paqman said:**
> Lol, it's repositories. [Suppositories]("http://en.wikipedia.org/wiki/Suppository") are something else entirely ;)

Hehehehe... glad someone caught that!

---

### Post by laceration on 2009-10-09
Sometimes Ubuntu can be a pain in the ***, but its not so bad where you actually have to take something up it!:lol:

---

### Post by MrWES on 2009-10-09
Thanks for that one; I started my day with a smile this morning.

~Bill

---

### Post by guriinii on 2009-10-09
Haha, brilliant. Humorous and informative.

---

### Post by Diabolis on 2009-10-09
> **laceration said:**
> Sometimes Ubuntu can be a pain in the ***, but its not so bad where you actually have to take something up it!:lol:

:lolflag:

---

### Post by slakkie on 2009-10-09
Hi, please have a look here: [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu). I suspect it will answer your questions and maybe raise a couple of new ones :)

---

### Post by LewRockwell on 2009-10-09
> **smileyguy said:**
> I know that to get apps from the Synaptics package manager I need to add suppositories (or use the ones already installed) but I used the command line to download an app from this page

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

command: 
 sudo apt-get install libdvdread4
My question is - does using the command line go to the suppositories? AND if it does, why can't I find libvdread4 in Synaptics Package Manager?

[http://en.wikipedia.org/wiki/Suppository](http://en.wikipedia.org/wiki/Suppository)

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

ROTFL

.

---

### Post by jerome1232 on 2009-10-09
I think the joke has run it's course, you were a bit late on that there lewRockWell. :p

---

