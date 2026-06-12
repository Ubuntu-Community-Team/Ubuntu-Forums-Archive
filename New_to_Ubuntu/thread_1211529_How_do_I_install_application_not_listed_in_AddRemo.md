---
title: "How do I install application not listed in Add/Remove?"
date: 2009-07-12
forum: New to Ubuntu
---

### Post by oxf on 2009-07-12
OK I want to install Bibus. I'm not seeing in in Add/Remove Applications or Synaptic Pkg Mgr. I can download it directly but I'm not sure this is the way to do it. Can I add it to Add/Remove or the repositories?

I suppose this question could also apply to other stuff so any general info would also be appreciated!

Thanks!!

---

### Post by philinux on 2009-07-12
From google I'd choose this.

[http://sourceforge.net/projects/bibus-biblio/](http://sourceforge.net/projects/bibus-biblio/)

---

### Post by VCoolio on 2009-07-12
I wrote a post with options and links for installing stuff [here]("http://myubuntu.ning.com/forum/topics/how-to-install-anything").

Don't know if this is the bibus you want but they have instructions on installing it [here]("http://bibus-biblio.sourceforge.net/wiki/index.php/Installation#Ubuntu").

---

### Post by oxf on 2009-07-12
> **VCoolio said:**
> I wrote a post with options and links for installing stuff [here]("http://myubuntu.ning.com/forum/topics/how-to-install-anything").

Don't know if this is the bibus you want but they have instructions on installing it [here]("http://bibus-biblio.sourceforge.net/wiki/index.php/Installation#Ubuntu").

Thanks both Phillinx and vcoolio. Yes that is what I want my concern about just downloading from the site was that it would be more difficult should I want to uninstall it and would not get updates.

---

### Post by VCoolio on 2009-07-12
if you use the checkinstall method you can uninstall easily. Read [here]("https://help.ubuntu.com/community/CheckInstall") why.

---

### Post by oxf on 2009-07-12
> **VCoolio said:**
> I wrote a post with options and links for installing stuff [here]("http://myubuntu.ning.com/forum/topics/how-to-install-anything").

Don't know if this is the bibus you want but they have instructions on installing it [here]("http://bibus-biblio.sourceforge.net/wiki/index.php/Installation#Ubuntu").

OK I think I've done something wrong here!! I followed instructions from above [http://bibus-biblio.sourceforge.net/wiki/index.php/Installation#Ubuntu](http://bibus-biblio.sourceforge.net/wiki/index.php/Installation#Ubuntu) 

I added to /etc/apt/sources.list in Third Party Software:
deb [http://switch.dl.sourceforge.net/sourceforge/bibus-biblio](http://switch.dl.sourceforge.net/sourceforge/bibus-biblio) ./
deb-src [http://switch.dl.sourceforge.net/sourceforge/bibus-biblio](http://switch.dl.sourceforge.net/sourceforge/bibus-biblio) ./

and downloaded public key:
wget -q [http://switch.dl.sourceforge.net/sourceforge/bibus-biblio/pmartino.gpgkey](http://switch.dl.sourceforge.net/sourceforge/bibus-biblio/pmartino.gpgkey) -O- | sudo apt-key add -

But its not showing up in either Add/Remove or Synaptic Pkg Mgr

What have I done wrong?

---

### Post by techstop on 2009-07-12
> **oxf said:**
> OK I think I've done something wrong here!! I followed instructions from above [http://bibus-biblio.sourceforge.net/wiki/index.php/Installation#Ubuntu](http://bibus-biblio.sourceforge.net/wiki/index.php/Installation#Ubuntu) 

<SNIP>

OK, so you have added the repository to your sources.list, and you've imported the public key so you can have authenticated packages.

You don't mention following these steps in the howto;

```
sudo apt-get update
sudo apt-get install bibus libsqliteodbc python-pysqlite2 python-wxgtk2.6 python-uno 
```

The first updates your list of packages, the second actually installs the required software.

Have you done those last two steps (they are quite vital to the whole process)?

---

### Post by oxf on 2009-07-13
> **techstop said:**
> OK, so you have added the repository to your sources.list, and you've imported the public key so you can have authenticated packages.

You don't mention following these steps in the howto;

```
sudo apt-get update
sudo apt-get install bibus libsqliteodbc python-pysqlite2 python-wxgtk2.6 python-uno 
```The first updates your list of packages, the second actually installs the required software.

Have you done those last two steps (they are quite vital to the whole process)?

OK point taken thanks.

I've actually removed the Bibus one for now from Software Sources. This seems a bit of an ordeal just to add one application. I think what I need is a tutorial on the wider subject of adding repositories to my software sources and read up on the whole process.

---

