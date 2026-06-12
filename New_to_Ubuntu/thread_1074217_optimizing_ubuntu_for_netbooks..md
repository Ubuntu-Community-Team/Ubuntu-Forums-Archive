---
title: "optimizing ubuntu for netbooks."
date: 2009-02-19
forum: New to Ubuntu
---

### Post by jarongg on 2009-02-19
i just purchased a msi wind and installed a fresh copy of ubuntu 8.04 on it. i have spent the last few days customizing it to my liking. i new to linux though, and still limited to what i can do. what i would like to know is, what are some good ways i can optimize my os to run the best it can for my system. think in terms of limited battery, processor power, ram, speed etc. etc. i would really like to do a lot of this through command line to get to know it more, but, again, am limited to what i know so far, so i would need a walk through it all. i am really excited about running ubuntu on my netbook, and being a part of this community. thanks for any and all help.

---

### Post by benhur99ph on 2009-02-19
Have you tried the Ubuntu Netbook Remix?
Its a gui designed with netbooks in mind. 

You can install the Ubuntu Netbook launcher via Synaptic.

---

### Post by jarongg on 2009-02-19
yea, i am aware of that, but i am not really interested in it. it is my understanding that they don't offer the optimization for the processor in hardy. and it's mostly just tweaks to make the most of the screen space. what i am looking for is tweaks for processr, ram, battery, and so on.

---

### Post by jarongg on 2009-02-19
bump.

---

### Post by Mercury_Alpha on 2009-02-19
If you're really serious about optimization, there's compiling the kernel. But even with the right tools, it's not for the faint of heart.

In the short run, you may just want to try a less taxing desktop environment like OpenBox, XFCE, or LXDE. Gnome and KDE are pretty heavy for netbooks.

---

### Post by jarongg on 2009-02-19
how about puppy? i don't know anything about all the distros out there. one thing i like about ubuntu is there is tons of support for it. i feel like it makes learning the system a lot easier when i can usually google the problem, and fix it myself.

---

### Post by zevans on 2009-02-19
I find KDE3 quite usable on my MSI Wind - much better than GNOME on the desktop, frankly.

Make sure you have laptop-tools installed and go through setting up all the power profiles in the GUI. I get almost 50% more battery life under Linux than I do under Windows, because the on-demand CPU seems to work properly.

The biggest thing I miss from Windows is the lack of panning. My netbook has 1024x600 but plenty have even smaller resolutions - easily fixed if you set up  a virtual desktop somewhat larger, but unfortunately X.org won't let you do that right now. (It used to, and it will again, but it seems like it's always "in the next release.")

---

### Post by Mercury_Alpha on 2009-02-19
> **jarongg said:**
> how about puppy? i don't know anything about all the distros out there. one thing i like about ubuntu is there is tons of support for it. i feel like it makes learning the system a lot easier when i can usually google the problem, and fix it myself.

If you want Ubuntu support and a lightweight desktop environment, there's Xubuntu, which uses the XFCE environment.

Crunchbang Linux is supposed to be quite fast, and it's based on Ubuntu, but its designers don't appear to have any contact info on their website, or even some basic info about themselves.

---

### Post by binbash on 2009-02-19
> **Mercury_Alpha said:**
> If you want Ubuntu support and a lightweight desktop environment, there's Xubuntu, which uses the XFCE environment.

Crunchbang Linux is supposed to be quite fast, and it's based on Ubuntu, but its designers don't appear to have any contact info on their website, or even some basic info about themselves.

Xubuntu is not a light distro, in fact it is the heaviest xfce distro i have ever seen.

---

### Post by Mercury_Alpha on 2009-02-19
> **binbash said:**
> Xubuntu is not a light distro, in fact it is the heaviest xfce distro i have ever seen.

It would appear that the thread starter desires Ubuntu support and a lightweight environment.

> 
how about puppy? i don't know anything about all the distros out there. one thing i like about ubuntu is there is tons of support for it.


XFCE is the only lightweight environment offered as a built-in DE for Ubuntu. Since we're in Absolute Beginner Talk, that appeared to be the safest route.

Perhaps you have some suggestions for this user?

---

### Post by pmenefee on 2009-02-19
Nobody has mentioned eeebuntu.  I haven't tried it, but was planning to when my new netbook arrives soon.  [http://www.eeebuntu.org/](http://www.eeebuntu.org/)

I have no idea if it's good, not so good, or what, but thought I'd bring it up for discussion so I could learn from the responses.

---

### Post by bossdak on 2009-03-15
Anybody got any idea how to make everything on the screen display smaller? Something like displaying 2048x1200 on the 1024x600 screen so that everything looks 50% smaller, maybe not 50% but something 70-80%.

---

### Post by ChadeFarseer on 2009-04-05
If you've got good eyes you can reduce the DPI of fonts to 83 (system -> preferences -> appearance. Then in the fonts tab click details).

You can also install a new GTK theme that optimizes screen space. Check out [[COLOR="Blue"]_this_[/COLOR]]("http://martin.ankerl.com/2007/11/04/clearlooks-compact-gnome-theme/") page for both clearlooks and human varieties.

---

