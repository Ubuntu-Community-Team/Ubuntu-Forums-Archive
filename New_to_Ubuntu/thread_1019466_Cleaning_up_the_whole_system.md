---
title: "Cleaning up the whole system?"
date: 2008-12-23
forum: New to Ubuntu
---

### Post by pakmor on 2008-12-23
First off -- thanks to all of the helpful people of this forum. I have surely found the answer to the majority of my problems with Ubuntu here.

I have tinkered with Linux off and on for 10 years and always come back to Ubuntu so I'm really not a noob.

Question: When a software program is removed using Synaptic or Apt-Get and purged why are there files still listed in Nautilus? Some of which can't be deleted.

I have googled my eyeballs out searching for this to no avail. Hope someone can give me an answer or point me in the right direction.

HAVE A BLESSED CHRISTMAS TO ALL

---

### Post by Elfy on 2008-12-23
where about's are they listed? Perhaps an example would be of help.

Might be hidden files - config files will be there for various apps, but you should be able toremove them.

---

### Post by pakmor on 2008-12-23
Thanks forestpixie for your reply.
Here's an example: I just did a complete remove of "onboard" in synatic and then the apt-get autoremove --purge thing and autoclean and so on. Rebooted went into Nautilus, did a search for "onboard" and it located 7 files in /usr/share/apt-install/desktop. I then had to run gksu nautilus to move the files to trash.

I'm trying to figure out why when a package is removed and "purged" why is not all the files cleared from the system.

Am I being nit-picky?

---

### Post by shad0w_walker on 2008-12-23
I have seen a couple of things were files aren't removed during a purge, mostly I've tracked it down to files in that folder that it can't account for. I had a folder which was supposed to be entirely removed when the package was uninstalled, however because I had put a couple of files in the folder that it didn't find in it's package listing, it didn't remove the folder. 

I think the issue is mostly due to inconsistencies between what it expects to find and what is really there. If you have changed or added files to it's files/folders then it may simply be playing it safe by not removing then if it can't prove they are the original files.

---

