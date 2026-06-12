---
title: "sperate boot partition ?"
date: 2009-11-18
forum: New to Ubuntu
---

### Post by gridd on 2009-11-18
hi I want to install 5 Ubuntu os on a 150 gb drive.
 Should I install a separate boot partition?
 can i use one encrypted  home partition for them all?
 Should I install karmic last?
 I lost gnewsense after the last attempt with karmic so a how to or  pointer + advise would be most appreciated.

---

### Post by spikyjt on 2009-11-18
Sorry did you say you want to install 5 versions of ubuntu on the same disk? If so may I ask why?

To answer your questions - no don't do a separate boot partition and yes you could use one home partition for them all, but it could cause you problems. The order shouldn't matter if all the OSes are linux.

If you want to try out lots of other versions, I highly recommend you install one version (stock ubuntu or kubuntu ideally) and use a virtualisation product such as VirtualBox to test the others.

Hope that helps

---

### Post by gridd on 2009-11-19
Thanks can you save downloads, programs, etc from virtual box into an encrypted partition?

---

### Post by indytim on 2009-11-19
From another perspective yes you can do a separate GRUB partition and I would recommend it based on the number of ops you want to host. I have authored a small tech paper on how to do this.  Check my signature for a link.

IndyTim

---

### Post by gridd on 2009-11-20
> **indytim said:**
> From another perspective yes you can do a separate GRUB partition and I would recommend it based on the number of ops you want to host. I have authored a small tech paper on how to do this.  Check my signature for a link.

IndyTim
wow thanks I wont put solved until I have tried it out though. will Karmic behave the same way as the other distros?

---

### Post by anaconda on 2009-11-20
> **gridd said:**
> Thanks can you save downloads, programs, etc from virtual box into an encrypted partition?

yes you can, Because when in use the encrypted partition would be un-encrypted.....

---

