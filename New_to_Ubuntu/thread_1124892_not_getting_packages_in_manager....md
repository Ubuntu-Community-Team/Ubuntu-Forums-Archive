---
title: "not getting packages in manager..."
date: 2009-04-13
forum: New to Ubuntu
---

### Post by ishboo on 2009-04-13
Well I just installed xubuntu on my old laptop, and im wanting things like checkgmail, and wireshark. I dont seem to be getting as many programs in the package manager as I can with my ubuntu desktop.

I checked my filter settings. 

and multiuniverse, universe, restricted, and main are checked in the repositories. its set to server from United states.

I'm kind of a newb to linux, so I dunno what to do, when I search, I'm not getting as many packages as I do with my Ububtu desktop.

normally I search gmail, and like 12 come up. On the laptop. None.

---

### Post by skymera on 2009-04-13
open the terminal or xterm:

```
 sudo apt-get update 
```

That will update the package lists.

---

### Post by ishboo on 2009-04-13
> **skymera said:**
> open the terminal or xterm:

```
 sudo apt-get update 
```

That will update the package lists.

I did this just now.

still I don't get packages... not the ones I'm looking for.

This is a fresh install of xubuntu, and I updated it maybe 202 updates or so.

---

### Post by skymera on 2009-04-13
Try looking in Synaptic, you may need to add extra repositories to get them, i'm not sure.

System > Admin > Synaptic Package Manager

---

### Post by RedSingularity on 2009-04-13
System>Admin>Software sources.  Make sure universe and multiverse is checked off.

---

### Post by ishboo on 2009-04-13
> **skymera said:**
> Try looking in Synaptic, you may need to add extra repositories to get them, i'm not sure.

System > Admin > Synaptic Package Manager

thats what I was thinking.

Currently there are three when I go to third-party software tab.

UNCHECKED: **CDROM:[Xubuntu 8.10_intreped lbex_ - release i386 etc...**
CHECKED: **[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) Intreped ***partner*
CHECKED: **[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) Intreped ***parther(source Code)*

---

### Post by RedSingularity on 2009-04-13
Those are fine.....the universe and multiverse are the real key to displaying packages.

---

### Post by ishboo on 2009-04-13
> **Shadow121 said:**
> System>Admin>Software sources.  Make sure universe and multiverse is checked off.
yeah they are checked.

---

### Post by RedSingularity on 2009-04-13
I dont see why you would be getting any less than on your desktop.  Are you using the same version?

---

### Post by ishboo on 2009-04-13
Xubuntu 8.10 on my 700mhz laptop LOL
and ubuntu 8.10 on my desktop.

I previously had ubuntu on my laptop, and it found packages.... Just xubuntu runs smoother on the slowness of the PC. I just installed it, did all updates. And then tried getting the software I wanted...

I didn't mess with package manager. so it must be default configurations. on the left ALL is selected. I went to filter, all are check marked. under the status tab. and checked repositories.

---

### Post by ishboo on 2009-04-13
well i guess since i have nothing else to do, im gonna reinstall the OS.... ill update when i do.

---

### Post by RedSingularity on 2009-04-13
Let me know if that fixed it or not when your done.

---

### Post by ishboo on 2009-04-14
weird.... it seems to be working now... that is so odd.... i never had any problems instlaling or updating on the first install..... weird but it seems to be fixed. now, thanks for all the support.

---

### Post by RedSingularity on 2009-04-14
That is interesting..........i cant see why that would have any effect on it....

---

