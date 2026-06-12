---
title: "Fresh install, can't run update manager"
date: 2009-02-22
forum: New to Ubuntu
---

### Post by viergeame on 2009-02-22
I just installed Ubuntu on a friends computer, and I had to install Feisty because he happened to have a disc for it lying around and no way to make a more current one.  I didn't think it would be a big deal though since I could just run the update manager and upgrade it right away anyway.  Well, it installed smoothly and everything seems to be working alright.  The internet even works (I am posting from his computer).  The only problem is that when I try to run the update manager it won't connect to any of the repositories.  Everything else internet related works fine, though.

---

### Post by Temposs on 2009-02-22
Feisty Fawn is no longer a supported version of Ubuntu. I don't know for sure if the repositories have been taken down, but it's possible. 

You should download a supported version of Ubuntu from the Ubuntu website and install it over the 7.04 version, or at least run an upgrade to version 7.10 like so:

```
sudo apt-get dist-upgrade
```

If you did that then your friend would have version 7.10 and that's still a supported version until April.

---

### Post by viergeame on 2009-02-22
Here is what I got when I tried that.

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

