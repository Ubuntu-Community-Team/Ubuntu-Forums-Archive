---
title: "use ubuntu for gparted with pxe"
date: 2008-12-18
forum: New to Ubuntu
---

### Post by tedpenner on 2008-12-18
I need to resize the partitions on about 1000 Windows machines (NTFS) across our network.  I understand that a tool called gparted [http://gparted.sourceforge.net/livepxe.php](http://gparted.sourceforge.net/livepxe.php) can operate via pxe boot, but that first a machine must be set up to serve as a pxe server for which a product called DRBL [http://drbl.sourceforge.net/one4all/](http://drbl.sourceforge.net/one4all/) is recomended.  Has anyone here ever served out gparted via ubuntu?  I have the 8.10 desktop running in vmware and need some assitance getting this set up.  What are the steps I should take?

---

### Post by Hospadar on 2008-12-19
You should probably ask in a different forum.  I know this is possible, at my old work we used a debian version over pxe to deploy images.

Also, I don't know exactly what your task looks like, but I suspect you could save a lot of time by using command line tools (like ntfsresize, fdisk, etc) in a script to take care of what you want to do.  Then someone wouldn't need to interactively size every single machine.  Certainly writing a good safe and functional script could take a little research and doing, but I think the payoff for you would be worth it.

---

