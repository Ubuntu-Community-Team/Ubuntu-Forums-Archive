---
title: "Can I install a newer version of a program if it's not in the repos"
date: 2009-02-25
forum: New to Ubuntu
---

### Post by xinman on 2009-02-25
Ok, so I'm still very new to linux on the desktop.  I am currently running ubuntu 8.04 and I would like to play with the latest f-spot, the only one in the repos is 0.4.3.1 is there any way for me to get the latest version installed safely?

Thanks in advance, I'm really trying to give linux on the desktop a good go and give every hurdle a fair chance to be worked out.

---

### Post by hansdown on 2009-02-25
Hi xinman.

Generally it is safer to use the packages in the repositories, but if you like something that plays animated gifs, try gthumb from synaptic.

---

### Post by mkvnmtr on 2009-02-25
Yes you can almost always install a later version. You will probably need to remove the old version first. You might want to check a tutorial on installing before you start.

---

### Post by xinman on 2009-02-25
Thanks handsdown, I'm looking for more though.

mkvnmtr: could you elaborate a little, do you mean installing from source?  That's one of the things that has really kept me away from linux on the desktop for so long.

---

### Post by mkvnmtr on 2009-02-25
Either installing from source or a deb file. there are some programs you need to download first. I can't explain how to do it as well as some of the tutorials do. It is really not hard you just need to follow instructions. I seldom save bookmarks for this sort of thing I just google it and it usually brings me back to the forum and somebody that has explained it really will.

---

### Post by sgosnell on 2009-02-25
Download the .deb file for the program you want to install, open file manager, navigate to it, right-click on it, and select Open with GDebi.  Then click on Install Package, and it will be installed.  Just like in Windows, just different app names.

---

### Post by spcwingo on 2009-02-26
Not only can you install it, you can add a launchpad ppa for it.  This way updates will come with regular system updates.  :D  Check out this link:

[https://launchpad.net/~michelinux/+archive/ppa]("https://launchpad.net/~michelinux/+archive/ppa")

If you need help adding this repository, just ask.

---

### Post by xinman on 2009-02-26
sgosnell: There wasn't a deb file to download, I know how to do simple installs but if there isn't a package I get lost and I really don't like compiling software (too many headaches when it doesn't work or filling in dependencies)

spcwingo:  thanks very much that did it!  Are there other PPAs for other applications?

---

### Post by kanikilu on 2009-02-26
> **xinman said:**
> spcwingo:  thanks very much that did it!  Are there other PPAs for other applications?
Sure, lots. It of course depends on what applications you want, but personally, I use:

[https://launchpad.net/~openoffice-pkgs/+archive/ppa](https://launchpad.net/~openoffice-pkgs/+archive/ppa)
[https://launchpad.net/~banshee-team/+archive/ppa](https://launchpad.net/~banshee-team/+archive/ppa)
[https://launchpad.net/~do-core/+archive/ppa](https://launchpad.net/~do-core/+archive/ppa)
[https://launchpad.net/~shutter/+archive/ppa](https://launchpad.net/~shutter/+archive/ppa)

---

### Post by LowSky on 2009-02-26
[http://www.getdeb.net/](http://www.getdeb.net/)

a great place to get some newer versions of apps, that are easy to install for Ubuntu, soory I look and it doesn't have F-spot

also using Ubuntu 8.10 will give you a newer version of F-spot (0.5.03) if you dont want to install it by source code

---

### Post by xinman on 2009-02-26
Thanks LowSky and kanikilu!  I've bookmark all of those for future references.

---

