---
title: "Flash Installation Error - Wrong architecture i386"
date: 2009-11-08
forum: New to Ubuntu
---

### Post by ashwat on 2009-11-08
I am trying to install Adobe Flash on Ubuntu 9.10 but when I try to run the .deb using the package installer it says Wrong Architecture i386. Whats the trouble here and whats the remedy:mad:

---

### Post by The Funkbomb on 2009-11-08
i386 is the 32bit version.

I assume you're using 64bit Ubuntu?  Check out the 64bit forum on the site.  They have everything you need to know about 64bit flash.

---

### Post by lidex on 2009-11-08
What's wrong with synaptic/apt package manager? They will both give the proper packages for your system automatically.

Try this:

```
sudo apt-get remove swfdec-mozilla
sudo apt-get remove mozilla-plugin-gnash
sudo apt-get remove adobe-flashplugin
sudo apt-get remove flashplugin-nonfree
sudo apt-get install flashplugin-installer

```

One line at a time please.

---

