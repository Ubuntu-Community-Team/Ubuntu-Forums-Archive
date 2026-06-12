---
title: "Network file system recommendation?"
date: 2006-10-21
forum: Networking &amp; Wireless
---

### Post by jpdw on 2006-10-21
This is kind of a pre-installation support question! (apologies if this is not the correct place... but it looked the best to me)

Next week I intend to begin replacing my home workstation & server.   Currently a mix of Ubuntu 6.06 (Workstation) & Fedora 3 (server).  

For various reasons (dont flame) I am going to use the same distros as before, but most up-to-date versions.

I currently use _NFS_ to mount all the workstation's non-system drives from the server. (ie /home, music, photos, etc).

NFS seems to do the job, but I have a nagging feeling that it's perhaps not as up-to-date as more recent network file systems.

I also run Samba on the server so that my windowz Photoshop machine can access the same partitions on the server.

I see a number of other options available when I rebuild the kernel but have never tried them.

**My question is** - is NFS still a sensible/good way to go?  

I am sure there is no hard-and-fast answer, but appreciate people's views.

Thanks!

---

### Post by kidders on 2006-10-21
Hi there,

> **jpdw said:**
> NFS seems to do the job, but I have a nagging feeling that it's perhaps not as up-to-date as more recent network file systems.Like what, I wonder.

The hard and fast answer is "Yes", really. NFS is what you want. The only reason to choose anything else -- at least under normal circumstances -- is if you want to opt for Apple or Microsoft filesharing, for the benefit of other systems on your network. Personally, I wouldn't consider alternatives such as the Andrew filesystem, for instance, (albeit technically superior) worth trying.

Hope that helps.

---

