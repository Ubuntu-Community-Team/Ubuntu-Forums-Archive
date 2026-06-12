---
title: "Update ?"
date: 2010-12-06
forum: New to Ubuntu
---

### Post by nu2this2 on 2010-12-06
After DL'g 10.04 and going on line, my version  needs to be updated. Having read about different problems people have had after doing updates, I am wondering if I should bite the bullet and install everything or not. Are there some things that I shouldn't DL?

---

### Post by CharlesA on 2010-12-06
Are you being prompted by Update Manager?

---

### Post by ajgreeny on 2010-12-06
If I were you I would do all the normal updates for 10.04, but not the distribution update to 10.10.

---

### Post by tommcd on 2010-12-06
> **nu2this2 said:**
> After DL'g 10.04 and going on line, my version  needs to be updated. ... I am wondering if I should bite the bullet and install everything or not. Are there some things that I shouldn't DL?
If you are just getting the updates for 10.04, then there is nothing to worry about. Just install the updates as they become available. The updates are mostly fixes for security issues and bug fixes, so you should install them.

If you are talking about doing a *dist-upgrade* to Ubuntu 10.10, then this is an upgrade to the next Ubuntu version. My own preference is to do *clean installs* of new Ubuntu versions instead of doing dist-upgrades. This is the best way to avoid problems when upgrading to a new Ubuntu version in my experience. 
The updating problems you are referring to are probably about doing dist-upgrades instead of just updating your current version. 

Note: If you want to avoid problems with updating or upgrading Ubuntu, then just stick to the Ubuntu repositories that are supported by Canonical (i.e., the repositories that are present on a fresh Ubuntu install). Avoid 3rd party repositories, including those all to often problematic PPA repositories. 
I believe that many, if not most of the problems that people have with updating and upgrading Ubuntu are caused by the ever growing multitude of 3rd party repositories that so many people add to their 
*/etc/apt/sources.list* file. This is the file where your Ubuntu repositories are listed. The exception here is the *Medibuntu* repository for proprietary codecs and stuff:
[http://medibuntu.org/](http://medibuntu.org/)
Using the Medibuntu repositories is fine.

Write back if you need more help.

---

### Post by marin123 on 2010-12-06
10.04 is lts, so you dont have to update if you dont want to. i'm updating to new releases since 9.10 and never had problems. if you depend on that computer i suggest you stay with 10.04. because if something gets broken during upgrade, the fastest and easiest solution is a fresh install. if you decide to upgrade, backup your files first (on separate partition or external hdd)...

---

