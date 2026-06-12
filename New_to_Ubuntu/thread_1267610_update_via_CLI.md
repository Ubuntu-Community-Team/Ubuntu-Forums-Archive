---
title: "update via CLI"
date: 2009-09-15
forum: New to Ubuntu
---

### Post by k33bz on 2009-09-15
On my server, I know there is numerous files by now that need to be updated. However I do not know how to list those files nor update them. Is there a way (CLI only) that I can view what needs to be updated and how do I update them.

---

### Post by scrooge_74 on 2009-09-15
sudo apt-get update

then 

sudo apt-get upgrade

It takes care of itself after that

---

### Post by k33bz on 2009-09-15
> **scrooge_74 said:**
> sudo apt-get update

then 

sudo apt-get upgrade

It takes care of itself after that

Thanks for the reply, however I want to see what I am upgrading before I upgrade it. Some things I may not want to upgrade.

---

### Post by scrooge_74 on 2009-09-15
Easy, after doing the apt-get upgrade it is going to present you with a list of stuff to upgrade and then ask you if yey or nay for the upgrade.

And usually everything in the list for updates is there for a reason.

You can also just do **sudo aptitude** and then you get a nice display to choose stuff

---

### Post by k33bz on 2009-09-15
> **scrooge_74 said:**
> Easy, after doing the apt-get upgrade it is going to present you with a list of stuff to upgrade and then ask you if yey or nay for the upgrade.

And usually everything in the list for updates is there for a reason.

You can also just do **sudo aptitude** and then you get a nice display to choose stuff

Thank-you :)

---

### Post by scrooge_74 on 2009-09-15
Any time

---

