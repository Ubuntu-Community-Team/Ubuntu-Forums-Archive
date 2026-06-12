---
title: "MoBlock help please"
date: 2008-05-28
forum: Networking &amp; Wireless
---

### Post by FranzyPants on 2008-05-28
I would like to install MoBlock on my computer... the problem is I'm on a 64 bit system. I tried to follow the instructions on the MoBlock site ([http://moblock-deb.sourceforge.net/](http://moblock-deb.sourceforge.net/)) but I always get this message after I type "sudo apt-get build-dep moblock" in the terminal: "E: Unable to find a source package for moblock". I am not sure how to continue. If anyone can help please do, I am about one year into using Ubuntu and I still am not very skilled with the terminal.

---

### Post by jre on 2008-05-29
moblock-deb.sf.net already does provide amd64 packages. So you just have to follow the normal instructions and install the pre-built deb.

For your current problem I guess you did not insert the "deb-src ..." line to your sources.list.

jre

---

### Post by FranzyPants on 2008-05-29
Correct, I'm not sure how to add it. I was expecting a .txt document I had to edit but instead I got a window with different options. How do I add the "deb-src ..." line to the sources.list file?

---

### Post by jre on 2008-05-30
> **FranzyPants said:**
> Correct, I'm not sure how to add it. I was expecting a .txt document I had to edit but instead I got a window with different options. How do I add the "deb-src ..." line to the sources.list file?
Don't know what you did. But here are the instructions, I just edited them a bit ;-)
[https://help.ubuntu.com/community/MoBlock#head-480068c0e1dee45dc2a87da3d1c052b9a7fd1ac9](https://help.ubuntu.com/community/MoBlock#head-480068c0e1dee45dc2a87da3d1c052b9a7fd1ac9)

jre

---

### Post by FranzyPants on 2008-05-30
Two more things: first, I just wanted to make sure that MoBlock is used through the terminal and second, I get an error during install: 'Couldn't find any package whose name or description matched "moblock"'

-Sorry for all the questions, I'm still used to the graphical installers on my Mac.

---

### Post by jre on 2008-05-31
> **FranzyPants said:**
> I get an error during install: 'Couldn't find any package whose name or description matched "moblock"'
Argh, sorry. There was a copy&paste error in the wiki.
To add the two sources lines you have to do this:
```
gksu gedit /etc/apt/sources.list
```
I accidentally advised you to edit /etc/default/moblock instead ...

Now just make sure you follow all steps in the wiki.
jre

---

