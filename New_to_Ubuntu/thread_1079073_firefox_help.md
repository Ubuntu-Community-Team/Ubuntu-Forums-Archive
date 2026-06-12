---
title: "firefox help"
date: 2009-02-24
forum: New to Ubuntu
---

### Post by trinidadflores on 2009-02-24
Ok call me dense if you want to But i hate the current version of firefox that is preinstalled in ubuntu 8.10 and prefer f.f. 2.0.0.20 and i would like to install that version  as my extensions all work with that install.  I have downloaded the f.f. 2.0.0.20 tar.gz but i dont know how to install it from there.  This is where i need help.  If someone would pleasee give me step by step directions on how to do this i would appreceiate it alot.

Trinidad

---

### Post by swoll1980 on 2009-02-24
If your compiling you need to install build essential
```
sudo apt-get install build-essential
```
then you would extract the folder to your desktop (right click>extract here)
open the folder, and read the "read me" file it will tell you what to do.

---

### Post by gackt on 2009-02-25
Try googling with this keyword " how to install anything in ubuntu" it will come up with some tutorial how to install such file package you described.

---

### Post by kansasnoob on 2009-02-25
> **trinidadflores said:**
> Ok call me dense if you want to But i hate the current version of firefox that is preinstalled in ubuntu 8.10 and prefer f.f. 2.0.0.20 and i would like to install that version  as my extensions all work with that install.  I have downloaded the f.f. 2.0.0.20 tar.gz but i dont know how to install it from there.  This is where i need help.  If someone would pleasee give me step by step directions on how to do this i would appreceiate it alot.

Trinidad

That's a very bad idea security wise!

But you should be able to use Ubuntuzilla and designate what version of Firefox you want to install:

[http://ubuntuzilla.wiki.sourceforge.net/?f=print#tochome3](http://ubuntuzilla.wiki.sourceforge.net/?f=print#tochome3)

Basic script:

> lance@lance-desktop ~ $ ubuntuzilla.py -a install -p firefox

Welcome to the Ubuntuzilla Firefox script version 4.6.0

Ubuntuzilla is built only for Ubuntu Linux and other distributions derived from Ubuntu (such as Linux Mint, e.g.)

This script will now install the latest release of the official Mozilla build of Firefox on your Linux system. If you run into any problems using this script, or have feature requests, suggestions, or general comments, please visit our website at [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/)

Retrieving the version of the latest release of Firefox from the Mozilla website...
The most recent release of Firefox is detected to be 3.0.5. Please make sure this is correct before proceeding. (You can confirm by going to [http://www.mozilla.org/](http://www.mozilla.org/))
If no version number shows, if the version shown is not the latest, **or if you would like to install an older release, press 'n'**, and you'll be given the option to enter the version manually. Otherwise, press 'y', and proceed with installation. [y/n]?

---

### Post by HittingSmoke on 2009-02-25
> **kansasnoob said:**
> That's a very bad idea security wise!

But you should be able to use Ubuntuzilla and designate what version of Firefox you want to install:

[http://ubuntuzilla.wiki.sourceforge.net/?f=print#tochome3](http://ubuntuzilla.wiki.sourceforge.net/?f=print#tochome3)

Basic script:

Second to that... You should **always** use the latest version of any browser. By using older versions you open yourself up to all sorts of security holes.

What extensions are you using that don't work with FF 3+? All of the even half decent add-ons work with the most recent release.

---

### Post by kansasnoob on 2009-02-25
> **HittingSmoke said:**
> Second to that... You should **always** use the latest version of any browser. By using older versions you open yourself up to all sorts of security holes.

What extensions are you using that don't work with FF 3+? All of the even half decent add-ons work with the most recent release.

That's the funniest sig I've ever seen!

From this day on I'll refer to repos as suppositories!!!!!!!!!

---

