---
title: "cairo dock"
date: 2009-05-17
forum: New to Ubuntu
---

### Post by davarse on 2009-05-17
hey is any body know how to install cairo dock on jaunty?
i runned cairo dock on intrepid ibex before, but lots of features not avalaible, and i just upgrade to jaunty, and it still the same..
i realy like cairo dock
i need some help.
much appreciated
davarse

---

### Post by lovinglinux on 2009-05-17
Run the following command:

```
sudo apt-get install cairo-dock
```

You must have the Universe repository enabled.

---

### Post by fabounet on 2009-05-18
don't do this as you will get the Ubuntu version of cairo-dock, which is broken (and very old).
You need to add the cairo-dock's repository first :
[http://www.cairo-dock.org/ww_page.php?p=From%20the%20repository&lang=en#8-32%20bits%20AND%2064%20bits]("http://www.cairo-dock.org/ww_page.php?p=From%20the%20repository&lang=en#8-32%20bits%20AND%2064%20bits")

---

### Post by lovinglinux on 2009-05-18
> **fabounet said:**
> don't do this as you will get the Ubuntu version of cairo-dock, which is broken (and very old).
You need to add the cairo-dock's repository first :
[http://www.cairo-dock.org/ww_page.php?p=From%20the%20repository&lang=en#8-32%20bits%20AND%2064%20bits]("http://www.cairo-dock.org/ww_page.php?p=From%20the%20repository&lang=en#8-32%20bits%20AND%2064%20bits")

It's not broken and it's not very old. It's just a little bit more than 6 months old.

If you want the latest version, then adding the repository is the best way, but I have version 1.6.3.1 and it works on Jaunty, without problems.

---

### Post by davarse on 2009-05-18
the dock is installed now. thank you guys..
but i still have a problem. i have no themes for the dock. the dock is working with my old themes, pretty much it is, no other choices of other themes..
how do you get some more themes? is there way to install new themes?
and also everytime i turn my comp on, it always says something about Open Gl to run the dock with, or something like that. and sometimes the dock isn't work properly. if i choose no when the box came out, the docks is running well but some of the effect doesnt work.
is any1 has the same thing?
ta
davarse

---

### Post by davarse on 2009-05-18
by the way, im using cairo dock version 2.0.0

---

### Post by s.fox on 2009-05-18
Hi,

You can get themes from [here]("http://ubuntuforums.org/showpost.php?p=7301374&postcount=8").  The link also includes installation instructions.

Hope it helps,  if not please post again.

-Ash R

---

### Post by davarse on 2009-05-28
i tried that link but it doesnt work. it says i have no permission

---

### Post by fabounet on 2009-05-29
consider updating to v2.0.3, it correct some bugs.

---

### Post by Hamchan on 2009-05-29
I just downloaded the .deb files for the dock and the plugins from [here]("http://developer.berlios.de/projects/cairo-dock/") and they are working great on my system.

---

### Post by davarse on 2009-05-30
thank you, its all fixed now..

---

