---
title: "How to link windows to ubuntu if forgot it to do in ubuntu installation?"
date: 2011-03-05
forum: New to Ubuntu
---

### Post by eilhart on 2011-03-05
Hi. I installed Ubuntu Netbook Remix 10.10 on my LG X130 netbook. It has also Windows 7. I had arranged partitions for it earlier on Windows as one for actual Ubuntu OS -~25 gb- and one for swap -~1,5 gb-. I installed and now it's doing some after installation updating.
 
My problem is I forgot to link (I don't know if it's the right word, I installed Ubuntu in another language) Windows by specifying the disk's root as "/windows" for instance. My questions:
 
1. Is there a way I can access Windows installed disk without installing Ubuntu again?
2. I have a portable game on Windows working only by double-clicking the .exe file. To run it on Ubuntu, do I have to install it or should I run the .exe only with Wine without installing? I don't care if it doesn't run on Linux. I just want to try to run it please tell me if it's possible.
 
My experience is Linux is very limited BTW. I once installed Linux Mint on my desktop with Windows but had some hardware driver problems then uninstalled it. This is the second time I installed a Linux distro.

---

### Post by maqtanim on 2011-03-05
1. Yes you can access the windows partitions. Go to **Places**. Then go to **Computer**. There you'll find your windows partition.
2. No, you have to install the game again with WINE. But be sure that the game runs in wine. Check the [wine database]("http://appdb.winehq.org/").

By the way, welcome to the community! :)

---

### Post by eilhart on 2011-03-05
Thanks for quick reply. 
 
I first ran Disk Tool from applications. There I saw other partitions and linked windows. I couldn't go to Places because File Manager wasn't accessible by default on the sidebar. After linking windows I clicked on path in Disk Tool. File Manager started then I fixed it on sidebar. Of course I'm assuming File Manager is the only way to go to Places etc on Ubuntu Netbook remix.
 
I checked Wine database as you suggested. Thanks for that. Looks like Torchlight runs with Wine. It says download winetricks first. 
 
Is it a standalone app or do I need to install Wine first? If so which one? Ubuntu App Center lists two. One says Binary Emulator and Library the other is dummy package. Also there is something called Q4Wine. Do I need to install that as well?

---

### Post by JKyleOKC on 2011-03-05
> **eilhart said:**
> Ubuntu App Center lists two. One says Binary Emulator and Library the other is dummy package. Also there is something called Q4Wine. Do I need to install that as well?I'm not familiar with Wine's needs, but the "dummy package" approach is widely used in Ubuntu to simplify keeping things up to date. Each package includes a list of any other packages that may be required for this one (if you haven't encountered "dll hell" in Windows you're one of the fortunate few). These dummy packages contain ONLY such a list, no actual files, and each time the corresponding real packages get updated, so does the dummy, with its list changed to reflect the latest versions of the real packages.

Thus you can simply install the dummy, and the package manager will automagically pull in all the other required packages and install them. It's a great help, but somewhat confusing when you first encounter it. By installing the dummy, you get notified each time it is updated, and this keeps you from overlooking updates to your real packages.

---

### Post by eilhart on 2011-03-05
So, if I install dummy I don't have to install other package, am I right? Just to be sure. 
 
I learned winetricks is something like a plugin that I have to install for that specific game to run BTW. It's not standalone, not to run without Wine I guess.
 
EDIT: I installed dummy. I see it also installed the other package by itself. I'll also install Q4Wine. It's got some GUI enhancements for Wine I understand looking it's description.
 
Thanks JKyleOKC.

---

### Post by JKyleOKC on 2011-03-05
You're quite welcome!

---

