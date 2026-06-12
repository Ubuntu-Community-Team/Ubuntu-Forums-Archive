---
title: "Tarballs"
date: 2009-04-15
forum: New to Ubuntu
---

### Post by GSam on 2009-04-15
I recently got a copy of OpenOffice 3.0.1 that is a tarball. I have never worked with tarballs in the past and haven't found a clear explanation of the steps involved. Is there someone who can clearly explain the steps that I need to take to open it and get it usable? I'm not a total newby, but have only used the Synaptic Package Manager.

---

### Post by lamalex on 2009-04-15
I can almost guarantee you do not want to install open office from a tarball, actually since you say you're a noobie I can 100% guarantee this. Why don't you tell us what you're trying to accomplish and we will help you find a better path there?

---

### Post by Yvan300 on 2009-04-15
If it came in a tar ball, then most likely that's the source for open office that you must compile. But this is nt recommended for beginners. But if you still want to then look here [http://thelinuxcauldron.wordpress.com/2009/04/13/how-to-session-compiling-software-from-source-code/](http://thelinuxcauldron.wordpress.com/2009/04/13/how-to-session-compiling-software-from-source-code/)

---

### Post by ostrm on 2009-04-15
I wouldn't do that, the version in the tree is reasonable stable, but if you really like, I won't stop you :-)

If I remember right, the tarball contains deb-packages. 

[EDIT]
Just looked it up, it depends on the suffix. If your file ends with *deb.tar.gz, then the following will work. If not, I don't recommend to install it from sources (making sure you have all dependencies *will* be a pain), Instead you can download it from **[here](http://download.openoffice.org/other.html)**
[/EDIT]

1. Untar the tarball
```

tar xzf [tarball]

```
You'll have a new subdirectory [openoffice.org] or similar. 

2. Change directory to [openoffice.org]/DEBS (cd [openoffice.org]/DEBS). 
There should be two different .dep files, one with gnome and one with kde integration. If you use gnome, delete the one with kde in it and vice versa. 

3. run:
```

dpkg -i *.deb

```

There should also be an installer for the menu entries, but I don't know, (panels are such an overhead ;-) )

---

### Post by freeman2000 on 2009-04-16
Maybe wait a few days.  OpenOffice v3.0.1 comes with Jaunty (9.04).

---

### Post by GSam on 2009-04-16
Thanks, folks...
I think I'll just stick with the 2.4 version that is available through Synaptic. I've been wasting too much time with this download and I have 3.0.1 on my Win XP laptop and as little as I actually use it, it isn't worth the trouble right now.
Thank you all for taking the time to respond. It really helped.
GSam

---

### Post by cbtengr on 2009-04-16
You can follow the instructions here:

[http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml](http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml)

This will add it to your software sources and you can install from Synaptic.

I've done it on my desktop & laptop running 8.10 - works fine.

---

### Post by GSam on 2009-04-26
Thanks to all of you. I was able to get OOo3 as a  free version. Darn sticky tarballs....

---

