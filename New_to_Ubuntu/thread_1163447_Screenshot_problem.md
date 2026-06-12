---
title: "Screenshot problem"
date: 2009-05-18
forum: New to Ubuntu
---

### Post by Big Luke on 2009-05-18
I have been having this problem for quite a while and I would like to fix it.  I am fairly certain it is a problem with Compiz but possibly with GNOME.  Whenever I try to take a screenshot with the Screenshot tool that is included with Compiz, I end up with a mess like [this]("http://i42.tinypic.com/35irqix.png") Now I'm not certain if this is because of a bug with the tool or a problem with Jaunty's recognition of .png image files.  However, the latter is highly unlikely because I can view .png files I have created and gotten off the internet with no problem at all.  I would have tried designating a different image format for screenshots to be saved as, but I haven't found a way to do that either. :-k

I would like to be certain that this is a bug with the screenshot tool before I submit a bug report to launchpad.  I am in no way a genius but I learn quickly, so any help would be greatly appreciated.

---

### Post by mprince on 2009-05-18
You could try this.
[I]
System>Administration>Synaptics Package Manager[/I]

Then search for 'libpng' (the png runtime) it should already have a green box.

Right-click on that and choose 'Mark for reinstallation'

Then click the 'Apply' button on the toolbar.

It will reinstall that package.

---

### Post by Big Luke on 2009-05-18
> **mprince said:**
> You could try this.
[I]
System>Administration>Synaptics Package Manager[/I]

Then search for 'libpng' (the png runtime) it should already have a green box.

Right-click on that and choose 'Mark for reinstallation'

Then click the 'Apply' button on the toolbar.

It will reinstall that package.

I reinstalled "libpng12-0" and it did not fix my problem.  However, I hadn't thought of reinstalling anything. #-o  I am going to reinstall compiz and see if that fixes it.

---

### Post by Big Luke on 2009-05-18
Sorry all, I had been searching for others that have had this problem and I just came across [this]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/327345") about 2 minutes ago. :oops:  Apparently, it is in fact a bug in compiz.

---

