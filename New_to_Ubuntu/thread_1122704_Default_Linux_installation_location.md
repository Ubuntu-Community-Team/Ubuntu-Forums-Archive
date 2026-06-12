---
title: "Default Linux installation location?"
date: 2009-04-11
forum: New to Ubuntu
---

### Post by EvanKroske on 2009-04-11
I constantly see applications mentioning that if another program isn't in its default installation location, you'll have to alter the path, config file, etc. I'd like to know where this is before I install too many programs in the wrong places! Where do you usually put the program files you download in a .tar.gz archive before you un-archive them?

---

### Post by taurus on 2009-04-11
You can unpack .tar.gz (or .tar.bz2) anywhere you want.  If you want to install somewhere besides the default, usually /usr/local, then you need to specify the path when you run the ./configure --PREFIX=/where_you_want_to_install.

---

### Post by HermanAB on 2009-04-11
If you install packages using Synaptic, then you need not worry about it.  They will be installed correctly.

If you build software yourself however, then the convention is to install it in /usr/local.

---

### Post by Xispa on 2009-04-11
You can see the linux filesystem hierarchy here: 
[http://aliyev.ws/wp-content/images/filesystemhierarchyhb8.jpg]("http://aliyev.ws/wp-content/images/filesystemhierarchyhb8.jpg")

If you install apps using synaptic or Add/Remove option (Applications menu) you shouldn't be worried about the location in which the program is installed. Commonly, the applications using synaptic are installed in /usr/lib/ folder. For applications installed manually, is commonly used /usr/local/bin

---

### Post by EvanKroske on 2009-04-11
Thanks for the tips; it's nice to know that I have to override something to mess up my installations.

@Xispa Thanks for the hierarchy diagram. I can always learn concepts better when I have a pretty picture to look at. :D

---

### Post by Paqman on 2009-04-11
> **EvanKroske said:**
> Where do you usually put the program files you download in a .tar.gz archive before you un-archive them?

Installing from tar.gz is a recipe for hassle. You're far better off using Synaptic. If something isn't available in the normal Ubuntu repos, see if there's a .deb file (which is a one-click install) or a PPA (which will allow you to get that app from Synaptic). Either of those will sort you out.

---

