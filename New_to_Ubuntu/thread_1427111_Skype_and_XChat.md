---
title: "Skype and XChat"
date: 2010-03-11
forum: New to Ubuntu
---

### Post by Captain Pissweak on 2010-03-11
Hi, I'm new to Ubuntu, and I was just wondering if there is any way to get Skype and XChat to work on it. Skype seems to not work when I try to install the Ubuntu version of it, and XChat seems to only be for Windows and Fedora. I've probably missed something obvious, but help is appreciated. If it helps, I'm running Ubuntu 9.10.

---

### Post by arochester on 2010-03-11
> Skype seems to not work

Why? What exactly happens?

---

### Post by gradinaruvasile on 2010-03-11
xChat is in the Ubuntu repositories for ages.

And Skype - what exactly is wrong with it? I use it on 3 computers with Debian (before was Ubuntu, but it was the same) and installed on 5 more computers with Ubuntu 9.10/8.10 - all work perfectly... 
Voice, webcams, desktop sharing - i even tested it with Mac and Windows and worked perfectly.

BTW i use the version that can be downloaded from the Skype site.

---

### Post by wojox on 2010-03-11
I use xchat. In the terminal Applications > Accessories > Terminal

```
sudo apt-get update && sudo apt-get install xchat
```

---

### Post by Captain Pissweak on 2010-03-11
Erm... This is a bit embarassing... It would appear that Skype in fact <b>does</b> work now... Disregard that part of it...

Also, could you possibly link me to the repositories? I'm an absolute newcomer to Ubuntu, and can't seem to locate such a thing. < This line is now a derp.

Okay, I've checked the software centre, and when I checked XChat, it said it was not available in the current data. Also, the sudo command thing didn't seem to work.

---

### Post by spiderbatdad on 2010-03-11
Instead of the software center, try synaptic package manager under System>>Administration.
When it opens go to Settings menu and select repositories...make sure they are all checked but the source code: multiverse and universe are most important for software extras. If they are not checked...check them and hit the reload button. Then in the search window type xchat. Check the box next to xchat, mark for installation, and click apply at the top of the window.

---

### Post by Captain Pissweak on 2010-03-11
Thanks spiderbatdad, that got everything working. This can be closed, or whatever it is that you do to solved threads in this forum.

---

### Post by arochester on 2010-03-11
You need to mark it as solved! Click the Edit Button on one of your posts. This will allow you to edit the heading.

Mark it as: [solved] Skype and XChat

---

