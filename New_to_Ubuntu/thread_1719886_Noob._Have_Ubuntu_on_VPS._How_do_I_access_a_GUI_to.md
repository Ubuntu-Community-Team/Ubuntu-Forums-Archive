---
title: "Noob. Have Ubuntu on VPS. How do I access a GUI to install and run apps?"
date: 2011-04-02
forum: New to Ubuntu
---

### Post by realmanmag on 2011-04-02
I have a VPS with Ubuntu 8.04 pre-installed.  I've been accessing it via Putty.

Does Ubuntu have some sort of GUI that I can access to load, view, and launch apps?

If so, how do I access it?

I installed TightVNC, but again, it shows a basic GUI, but I can't see where to view and launch any apps.

Finally, in the process of trying to install a GUI, I've loaded all sorts of crap onto the server.  What's the best way to delete everything that is not part of the Ubuntu O/S?

Thanks very much for any help!

---

### Post by Paqman on 2011-04-02
I'm assuming you have the server version installed, in which case, no, it doesn't have a GUI by default.

You can install any package you want using the command line:
```
sudo apt-get install package1 package2 package3
```

You might like to take a look at Aptitude, which does have a slightly nicer interface for installing apps on the command line. IIRC it's already installed on the server version, but if it's not then a simple:
```
sudo apt-get install aptitude
```
...will sort you out. To open it:
```
sudo aptitude
```

I can't really help you remove all the extra packages you installed unless you know what they are. If you really, really need a graphical desktop on your machine then:
```
sudo apt-get install xorg gdm gnome-core gome-themes network-manager-gnome synaptic
```

This will give you a desktop environment you can log into and use the Synaptic Package Manager from. It'll add a lot of junk to your machine that it doesn't need to run efficiently as a server though, and mean you'll have to download bigger updates to keep the machine secure.

---

### Post by realmanmag on 2011-04-02
Thanks.  Really appreciate the help.

Yes, the server version is installed.

I installed Aptitude.  Looked over the menu.  I'm still not sure how to proceed.

I'd like to install a couple of applications.  They have 'setup.exe' files for installation.

I'm not sure how to / if I can install these on ubuntu.  Once installed, I'm not sure how to launch them and see their GUI.  Do I install and launch these from Aptitude?

Appreciate any help you can provide.

---

### Post by davidmohammed on 2011-04-02
setup.exe type stuff is obviously windows based applications.  You cannot directly run those in any linux based system without the help of "wine".

What windows applications are you trying to install?  Maybe there is an equivalent (or better) native linux application you can try.

---

### Post by Paqman on 2011-04-02
> **realmanmag said:**
> 
I'm not sure how to / if I can install these on ubuntu.  Once installed, I'm not sure how to launch them and see their GUI.  Do I install and launch these from Aptitude?


As davidmohammed says, these are Windows apps, not Linux ones. On Linux the normal way to install software is from the repositories. Aptitude connects to these repositories and can download and install anything in Ubuntu's vast repos. There's tens of thousands of packages available.

We really need to know what you're trying to install before we can help.

---

### Post by realmanmag on 2011-04-02
Thanks again for the input.

The apps I'm trying to install are internet marketing type apps - all windows based it seems.

I looked into Wine.  It looks like I need to upgrade my Ubuntu to install it.  I'll look around the forum for the 'how to' on upgrading.

Really appreciate the help.

---

### Post by Paqman on 2011-04-02
> **realmanmag said:**
> 
The apps I'm trying to install are internet marketing type apps - all windows based it seems.


Can you be more specific?

> 
I looked into Wine.  It looks like I need to upgrade my Ubuntu to install it.  I'll look around the forum for the 'how to' on upgrading.


You shouldn't need to upgrade, Wine is available for all the currently supported versions of Ubuntu.

Having said that, Wine is a bit of a kludge, and a lot of Windows apps don't work well (or at all). Installing a native Linux app will be far easier and work better. We can suggest some if you tell us what you want.

---

### Post by realmanmag on 2011-04-02
One of the apps is Scrapebox.

Based on the Wine download page looks like it requires 9.10 or above for Ubuntu.
[http://www.winehq.org/download/](http://www.winehq.org/download/)

Thanks!

---

### Post by Paqman on 2011-04-02
To install Wine, just log into your box and:
```
sudo apt-get install wine
```

Easy as that. As I mentioned above, on Linux you don't go to a website and download your app, you get it straight from the online repos. No mess, no fuss, and the package manager will handle updates for all your software too.

---

### Post by realmanmag on 2011-04-02
Perfect.  Thanks!

---

