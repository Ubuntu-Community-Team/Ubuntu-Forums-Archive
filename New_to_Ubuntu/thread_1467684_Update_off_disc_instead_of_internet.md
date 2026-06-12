---
title: "Update off disc instead of internet"
date: 2010-05-01
forum: New to Ubuntu
---

### Post by TK-Tex on 2010-05-01
I would like to see a change in the operating cd's. It would be nice if you could just upgrade your system with the cd's instead of having to download the upgrade from the internet. I just want to upgrade and not swipe my drive all over again. If this is already possible, then tell me how to do it please. Thanks!

---

### Post by arpanaut on 2010-05-01
Here is a link to a page that outlines the many possible ways to upgrade.

Scroll down to: Upgrading Using the Alternate CD/DVD

Seems to be what you are looking for.

[http://www.ubuntu.com/getubuntu/upgrading#Upgrade%20from%208.04%20LTS%20to%2010.04%20LTS](http://www.ubuntu.com/getubuntu/upgrading#Upgrade%20from%208.04%20LTS%20to%2010.04%20LTS)

---

### Post by hansdown on 2010-05-01
Hi TK-Tex.

You can upgrade from the alternate install CD, but please keep in mind, that you still need an internet connection.

---

### Post by TK-Tex on 2010-05-01
> **arpanaut said:**
> Here is a link to a page that outlines the many possible ways to upgrade.

Scroll down to: Upgrading Using the Alternate CD/DVD

Seems to be what you are looking for.

[http://www.ubuntu.com/getubuntu/upgrading#Upgrade%20from%208.04%20LTS%20to%2010.04%20LTS]("http://www.ubuntu.com/getubuntu/upgrading#Upgrade%20from%208.04%20LTS%20to%2010.04%20LTS")

This is a good link, but it looks like you still have to download an ISO. I want to know how you can upgrade from the Live Desktop CD's disc.

---

### Post by hansdown on 2010-05-01
> **TK-Tex said:**
> This is a good link, but it looks like you still have to download an ISO. I want to know how you can upgrade from the Live Desktop CD's disc.

The live CD will have a pop-up stating, "A medium with upgrades has been found", or some such.

I haven't investigated how this will play out, though. You still need an internet connection, to get all the good, wholesome updates, though.

---

### Post by cap10Ibraim on 2010-05-01
The moment I insert the CD, the package manager in my Ubuntu detected it and offered an option to upgrade

---

### Post by arpanaut on 2010-05-01
> **TK-Tex said:**
> This is a good link, but it looks like you still have to download an ISO. I want to know how you can upgrade from the Live Desktop CD's disc.

Sorry, I'm in the habit of using the alt. CD...
and don't have bandwidth issues. My ISP is pretty generous.

I've found that in early days of release using the alt. CD works faster than online, especially if you use torrents to DL the CD

If the live CD works like that now it's news to me.

P.S. The Alt. CD works as a good rescue CD also.

---

### Post by ugm6hr on 2010-05-01
> **TK-Tex said:**
> This is a good link, but it looks like you still have to download an ISO. I want to know how you can upgrade from the Live Desktop CD's disc.

Easy (ish).

Just backup your /home folder including hidden files (use rsync -av to simplify if you want), install (as usual), and copy back /home (making sure you install with the same username).

If you have a separate /home partition (recommended) - you can just install using Live CD, making sure not to format that partition.

If you have non-standard applications, you will have to reinstall.  It is possible to get a list of installed debs, but it is easy enough to just install them manually unless you have 100s of apps.

If this doesn't make sense - just post back regarding your specific situation, and I can go into more detail.

---

### Post by TK-Tex on 2010-05-01
> **arpanaut said:**
> Sorry, I'm in the habit of using the alt. CD...
and don't have bandwidth issues. My ISP is pretty generous.

I've found that in early days of release using the alt. CD works faster than online, especially if you use torrents to DL the CD

If the live CD works like that now it's news to me.

P.S. The Alt. CD works as a good rescue CD also.

Thanks for this info. Now I'll be able to bit torrent faster, plus I'll be able to create an ISO recovery CD. Thanks again.

?-- Is the alternate cd a gui install or a terminal style interface?

---

