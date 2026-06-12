---
title: "upgrade kubuntu to kde 4.5 or 4.6?"
date: 2011-02-02
forum: New to Ubuntu
---

### Post by cairnzi on 2011-02-02
hi people, can some kind person suggest how to upgrade to atleast kde 4.5? or possibly even 4.6 if that is possible? 

Cheers.

---

### Post by cairnzi on 2011-02-02
Ah! just found out how, have to upgrade to 10.10 first.

---

### Post by FlameReaper on 2011-02-02
Is there any other way other than having to upgrade to 10.10? I'd like to keep 10.04 for at least until 12.04 comes out I guess.

---

### Post by ankspo71 on 2011-02-03
Hi,
It looks like KDE 4.5.3 is available for Lucid in the Kubuntu Backports PPA: [https://launchpad.net/~kubuntu-ppa/+archive/backports/](https://launchpad.net/~kubuntu-ppa/+archive/backports/)

It's not that uncommon for people to run into some problems while upgrading KDE through the PPAs, so be sure to make backups of your important files first.

To do the upgrade through the terminal, paste the following commands:
```
sudo add-apt-repository ppa:kubuntu-ppa/backports
sudo apt-get update
sudo apt-get dist-upgrade
```

Or if you prefer using a graphical interface, you can add the following repository to Synaptic's or Kpackagekit's software sources list (see screenshot below)
```
ppa:kubuntu-ppa/backports
```
Then refresh/reload the repositories and get your updates through your package manager.

Hope this helps.

---

### Post by arch0njw on 2011-05-17
Be forewarned... I have a laptop on which I run 10.04 and have installed KDE from the PPA.  I tried to upgrade to 11.04 and it failed due to that.

I have filed a bug on this and hopefully this will get fixed.  Otherwise, the path is pretty ugly.  (i.e., complete reinstall or uninstall a lot of software and manually reinstall after an upgrade)

---

