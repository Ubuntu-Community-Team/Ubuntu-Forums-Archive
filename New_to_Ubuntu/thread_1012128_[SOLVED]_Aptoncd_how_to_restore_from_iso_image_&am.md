---
title: "[SOLVED] Aptoncd: how to restore from iso image &amp;amp; install?"
date: 2008-12-15
forum: New to Ubuntu
---

### Post by mapes12 on 2008-12-15
I'm going around in circles with this. Been googling for ages but can't seem to find a solution.

I have an iso image created by aptoncd of my installed packages but I don't have a cd writer to create a cd from it. I know that if I could burn to a cd then I could go into Synaptic package manager and select the cd as the source to install from, via the origin button. But I can't.

Therefore, in the restore part of aptoncd I selected restore from iso which very nicely places all the packages in /var/cache/apt/archives but doesn't install them to my system. How do I get them to install??

---

### Post by logos34 on 2008-12-15
In Synaptic look for 'aptoncd-metapackage':

> [http://aptoncd.sourceforge.net/doc-manual.html](http://aptoncd.sourceforge.net/doc-manual.html)

Metapackage
    With Metapackage option it's possible to create a package whose dependences are all packages included in the APTonCD media. It's useful to restore all packages easily, so you can just install the matepackage instead of install each package by hand.

Install the metapackage and hopefully it will install all the others as dependencies.

[https://answers.launchpad.net/aptoncd/+question/3523](https://answers.launchpad.net/aptoncd/+question/3523)

---

### Post by Michaelg14 on 2008-12-15
if your packages are all in the archive folder you could try this

```
sudo dpkg -i /"path to your archive folder"/*.deb
```

---

### Post by mapes12 on 2008-12-16
> **Michaelg14 said:**
> if your packages are all in the archive folder you could try this

```
sudo dpkg -i /"path to your archive folder"/*.deb
```That solved it. Thanks!!

---

