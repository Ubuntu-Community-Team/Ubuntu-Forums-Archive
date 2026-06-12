---
title: "Unwanted Update Manager packages"
date: 2010-01-23
forum: New to Ubuntu
---

### Post by blues2use on 2010-01-23
I have no idea why these Thai language packages showed up and the Update Manager wants me to install them:

**libthai-data** and **libthai0**

"Data needed by LibThai library. It is usually automatically installed."

"LibThai is a set of Thai language support routines aimed to ease developers' tasks to incorporate Thai language support in their 
applications. It includes important Thai-specific functions e.g. word breaking, input and output methods as well as basic character and string 
supports. This package contains the shared libraries needed to run programs that use the LibThai library."

**How do I remove these from the Update Manager or exclude them from being shown as an update?**

Thanks for the help

---

### Post by chuina on 2010-01-23
Have u tried with synaptics ?

Synaptics is in System>administration>Synaptic Package Manager

use the search tab to deal with these packages

---

### Post by Mornedhel on 2010-01-23
```
$ apt-cache rdepends libthai0
libthai0
Reverse Depends:
  libthai-dev
  libthai-data
  firefox-3.5
  scim-thai
  thunderbird
  libthai-dev
  libthai-data
  libpango1.0-0
  libm17n-0
  gtk-im-libthai
  firefox-3.5

```

In all likelihood, Firefox needs this to properly display Thai characters.

Removing this package will uninstall Firefox. Pinning this package so that it doesn't get upgrades will possibly force Firefox not to receive upgrades either, and if security upgrades are released for libthai (to close security holes, etc.) you will not receive them.

I recommend applying the upgrades.

---

### Post by blues2use on 2010-01-23
> **Mornedhel said:**
> ```
$ apt-cache rdepends libthai0
libthai0
Reverse Depends:
  libthai-dev
  libthai-data
  firefox-3.5
  scim-thai
  thunderbird
  libthai-dev
  libthai-data
  libpango1.0-0
  libm17n-0
  gtk-im-libthai
  firefox-3.5

```

In all likelihood, Firefox needs this to properly display Thai characters.

Removing this package will uninstall Firefox. Pinning this package so that it doesn't get upgrades will possibly force Firefox not to receive upgrades either, and if security upgrades are released for libthai (to close security holes, etc.) you will not receive them.

I recommend applying the upgrades.

Okay...I'll do that. I'm still a noob and didn't know about the **apt-cache rdepends** command. I'll put that in my notes...

Thanks for the help

---

### Post by warfacegod on 2010-01-23
Try installing localepurge, it will remove all of the language support from your system except the ones you specify:

```
sudo apt-get install localepurge
```

It will ask you which language packages you wish to keep. For example, I'm from the U.S. and I speak English so I would select en_US.utf8 (something like that anyway). If you want to, you can save as many as you like.

---

### Post by blues2use on 2010-01-23
> **warfacegod said:**
> Try installing localepurge, it will remove all of the language support from your system except the ones you specify:

```
sudo apt-get install localepurge
```

It will ask you which language packages you wish to keep. For example, I'm from the U.S. and I speak English so I would select en_US.utf8 (something like that anyway). If you want to, you can save as many as you like.

Thanks for the tip. I installed it and run it and picked en.US...looks okay to me.

Thanks again

---

### Post by Costas100 on 2010-01-23
I had exactly the same problem and was solved very easy. See thread:
[http://ubuntuforums.org/showthread.php?t=1387200](http://ubuntuforums.org/showthread.php?t=1387200)
Solution near the end

Good luck
Costas

---

