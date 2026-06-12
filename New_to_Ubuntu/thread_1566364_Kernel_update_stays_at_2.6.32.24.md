---
title: "Kernel update stays at 2.6.32.24"
date: 2010-09-02
forum: New to Ubuntu
---

### Post by Insertion_Epsilon on 2010-09-02
Every time the time for Kernel upgrades come, the Kernel Update always shows the 2.6.32.24 version. I think it may have something to do with the /dev/src folder since the error message said that it was inaccessible while inquiring the disk space.

---

### Post by CharlesA on 2010-09-02
The last two kernel updates were minor builds. They are staying on 2.6.32-24 for lucid, I believe.

Anyway, it went from 2.6.32-24.41 to 2.6.32-24.42.

---

### Post by Insertion_Epsilon on 2010-09-02
Oh, I thought I had a problem with my laptop. So when's the next major build coming, if you don't mind me asking? By the way, what about the latest stable kernel (2.6.34 or something)? Is the next Ubuntu going to use that?

---

### Post by egalvan on 2010-09-02
If you are running 10.04, don't expect major kernel updates.

Lucid 10.04LTS is Long Term Support, where Security, Stability and Reliability is first and foremost.
"New-ness" is at the bottom of the list.

For instance, Hardy 8.04LTS is using kernel 2.26.24
gparted is at v0.3.5
OpenOffce is v2.4

these are all older, but stable and reliable, versions.

FireFox was a rare exception...
it was bumped up to  v3.6.8, I believe due to security & reliability issues.


It IS possible to run the "latest & greatest" on an LTS release,
but it requires work-a-rounds,
and you are probably better served by another release, such as the upcoming 10.10.

---

### Post by inameiname on 2010-09-02
10.04 will not upgrade to a later kernel through the Repos. Thus, 2.6.32 will be the latest. 

But if you desire a newer kernel, I suggest doing this:

sudo add-apt-repository ppa:kernel-ppa/ppa
sudo apt-get update
sudo aptitude install linux-headers-2.6.35-19-generic linux-image-2.6.35-19-generic

It is what I use and works just fine for me to get the most recent kernel.

Oh, and unfortunately, you must occasionally check for the latest kernel, by:

sudo apt-cache search linux-image

to see if there is a newer kernel in the PPA, as it doesn't update automatically.

---

