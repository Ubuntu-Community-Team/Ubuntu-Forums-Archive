---
title: "keep old applications when upgrading (experienced advise)"
date: 2008-12-17
forum: New to Ubuntu
---

### Post by rburkartjo on 2008-12-17
i have been windows free for over 1 1/4 years and just use ubuntu. i have gone thru 3 updates. is there a way to insure that i can use all my old applications when i update. if so what is the best way and how do i do it. 
going to be 60 in a few months and linux is the only way to go!!!/tks cheesemaker

---

### Post by SuperSonic4 on 2008-12-17
Not to my knowledge but it's very unlikely an upgrade will render apps unusable. Even a major upgrade from KDE3.x to KDE4 still runs kde3 apps like amarok and k3b

---

### Post by Hospadar on 2008-12-17
If you update over the network, your old apps should stay installed.

Also you could export your list of currently installed packages (if you re-install with a cd for example) and then import them later after you've re-installed
[http://stackoverflow.com/questions/187629/how-do-i-preserve-installed-applications-when-migrating-ubuntu-to-another-platf](http://stackoverflow.com/questions/187629/how-do-i-preserve-installed-applications-when-migrating-ubuntu-to-another-platf)
This should work fine, but it might cause trouble as it may attempt to install older packages that have been depricated by a new update.  I would think for the most part though that dpkg would just skip depricated packages, or at least that maybe having a couple old packages floating around won't hurt terribly.

---

### Post by rlunger on 2008-12-17
> **rburkartjo said:**
> i have been windows free for over 1 1/4 years and just use ubuntu. i have gone thru 3 updates. is there a way to insure that i can use all my old applications when i update. if so what is the best way and how do i do it. 
going to be 60 in a few months and linux is the only way to go!!!/tks cheesemaker

Upgrading your system shouldn't really have any effect on your currently installed apps.  It could happen that a bug/issue could be introduced into your system this way, but a lot of testing goes into the updates before they are packaged (not that this means it won't happen).  After you've performed a system upgrade, if you're worried about the apps try:

    sudo apt-get update
    sudo apt-get upgrade

This will update your local package list as well as upgrade to the newest versions of your apps (if any) that are available.

---

