---
title: "Ubuntu wants to remove before KDE install"
date: 2009-03-06
forum: New to Ubuntu
---

### Post by longtom on 2009-03-06
I'd like to get KDE going on my Ubuntu installation - just to check it out.
However, when I want to install with Synaptic it says:

To be removed:

Openoffice.org-debian-menus

to be installed:

....

What does that mean? I don't want to have anything changed....

Please advise!

longtom

---

### Post by t0p on 2009-03-06
It's difficult to advise without knowing precisely what you're trying to do and precisely what the package manager wants to remove and install.

If you want to try the KDE desktop environment while still retaining the original Gnome stuff, you can install it by typing into the terminal:

```
sudo apt-get install kubuntu-desktop
```

Once that is installed, you'll be able to choose which desktop environment to run when you're at the log-in screen.  Just click on the button in the corner that is labelled **Sessions** (I think), and you'll be given the option of choosing KDE or Gnome.

When you install that meta-package **kubuntu-desktop**, the package manager will tell you that it wants to also install a great long list of applications (most of which begin with the letter "K").  These are the apps which go with KDE, so just agree to installing them.  But be warned, your Applications menu will become rather long and unwieldy - though you will be able to prune it later.  If you want to know how, just ask!

---

### Post by longtom on 2009-03-06
> **t0p said:**
> IBut be warned, your Applications menu will become rather long and unwieldy - though you will be able to prune it later.  If you want to know how, just ask!

I'll get back on your offer.  

Thank you in the meantime.

longtom

---

### Post by Big_Croc7 on 2009-03-06
There are other options too, try looking at this page first

[http://psychocats.net/ubuntu/kde-core](http://psychocats.net/ubuntu/kde-core)

---

### Post by longtom on 2009-03-06
> **Big_Croc7 said:**
> There are other options too, try looking at this page first

[http://psychocats.net/ubuntu/kde-core](http://psychocats.net/ubuntu/kde-core)

Will do.  Thank you.

---

