---
title: "i am planning to install ubuntu7.10 and fedora10 on my comp. which alrdy has win xp."
date: 2009-01-19
forum: New to Ubuntu
---

### Post by tavati on 2009-01-19
am i in danger ?

---

### Post by emarkd on 2009-01-19
of what?  You can install anything you want until your disk is full.  The most dangerous part is the repartitioning.  Back up anything important from your xp install before starting just in case your partition table gets corrupted somehow.  The chances of this are quite small if you take your time and work carefully.

---

### Post by mlentink on 2009-01-19
> **tavati said:**
> am i in danger ?

Yes.

Windows XP is known to be vulnerable to viruses and trojans. It is not really a safe operating system.

And why Ubuntu 7.10? You do realize that 8.10 is the latest version?

---

### Post by emarkd on 2009-01-19
> **mlentink said:**
> You do realize that 8.10 is the latest version?

Good catch.  You should at least be using 8.04, which is the latest version with long term support.

---

### Post by tavati on 2009-01-19
thanks ! i just like trying.

---

### Post by tavati on 2009-01-19
u r right . but my 8.10 cd is corrupted. i was trying this for last 4 hours with all options. now i know it is corrupt. i will try this experiment with 7.10. hope fedora 10 cd is ok.

---

### Post by mlentink on 2009-01-19
> **tavati said:**
> but my 8.10 cd is corrupted. i was trying this for last 4 hours with all options. now i know it is corrupt.

[http://www.ubuntu.com/GetUbuntu/download](http://www.ubuntu.com/GetUbuntu/download)
 You might want to try a different mirror, and check the disk for errors after the burn. Be sure to burn it as an iso, and at the slowest possible speed. Actually, I've never had any problems with the downloads.
You could always order a cd as well, for an astonishingly low price.

---

### Post by emarkd on 2009-01-19
the problems with your cd are probably not related to the download.  you can get the md5 checksum for the iso file and compare it against the one you downloaded using the md5sum command.

if the file you downloaded checks out, reburn it using the slowest speed as suggested above.  if you use k3b to burn the disk, it offers the option to verify the written data when the burn is complete so you can be sure it's correct.

---

### Post by -kg- on 2009-01-19
There's another consideration.  If you use a torrent client to download via torrent, the checksum is done as a part of the torrent download process and a corrupt download will be nigh on to impossible (doesn't guarantee a good burn, but...).

A little way down [this page (the Ubuntu download page)]("http://www.ubuntu.com/getubuntu/downloadmirrors#bt") you will find links to torrent downloads.

---

