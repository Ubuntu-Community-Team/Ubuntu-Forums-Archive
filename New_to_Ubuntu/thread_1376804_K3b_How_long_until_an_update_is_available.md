---
title: "K3b: How long until an update is available?"
date: 2010-01-09
forum: New to Ubuntu
---

### Post by held7over on 2010-01-09
The K3b (ver. 1.68.0) in Ubuntu 9.10 has this bug ([http://bugs.kde.org/show_bug.cgi?id=204333](http://bugs.kde.org/show_bug.cgi?id=204333) ) which says CdRecord doesn't have permission to access the cdrom device....unfortunately after it has already started writing to disc....which means your cd or dvd disc is wrecked.

I checked at [http://k3b.plainblack.com/](http://k3b.plainblack.com/) and they have a "K3b 1.69.0 alpha4" release that fixed this bug.

My question is, is there a way I can guesstimate when Ubuntu will release a binary update for this? (-or for that matter in the future on other problems that rise up, so that I know whether to set it out and wait or look for a different solution?)


Also, they seem to indicate there is a Debian release available, but I am not sure how I find it...and I worry that it might cause things I need for 9.10 to be replaced...

Thanks for your advice and thoughts! :)

---

### Post by oldos2er on 2010-01-09
Maybe try here: [http://k3b.plainblack.com/](http://k3b.plainblack.com/)

---

### Post by SuperSonic4 on 2010-01-09
Arch uses K3B 1.69 so there is an update.

You may be able to get it from the *Kubuntu-beta-PPA* but this will install a load of KDE4.4 stuff so it may be wise to disable it straight after K3B if you so wish

```
deb http://ppa.launchpad.net/kubuntu-ppa/beta/ubuntu karmic main
```

Otherwise it appears your last option is to compile from source. If you bear with me I'll take a look around

---

### Post by held7over on 2010-01-09
Thanks SuperSonic4! But I went to sources, clicked on add, and added your apt line, then refreshed the sources, closed, and went to synaptic and searched on K3b, but it only brought up what I already had when I ran the search without the new apt line. Did I do something wrong, or do I need to add yet another different apt line for Kubuntu stuff?

---

### Post by Perfect Storm on 2010-01-09
You need to add a key first, note that repository you're going to use is marked as **beta** and may have stability issues and more.

```
gpg --keyserver keyserver.ubuntu.com --recv 2836CB0A8AC93F7A
gpg --export --armor 2836CB0A8AC93F7A | sudo apt-key add -
sudo apt-get update
```

---

