---
title: "What Happened to &quot;Linux Restricted Modules&quot;"
date: 2009-11-24
forum: New to Ubuntu
---

### Post by Martin Marshalek on 2009-11-24
Last night there was a kernel update and when I went to remove the old kernel (after restarting) by running ```
sudo apt-get autoremove --purge 2.6.31-14-*
``` it only removed the generic kernel and the two header packages. I then checked synaptic for the restricted modules but they don't seem to exist any more. Did 2.6.31 do away with the restricted modules packages or am I just not looking in the right places?

---

### Post by 73ckn797 on 2009-11-24
Mine still lists the ubuntu-restricted-extras in synaptic after the update.

---

### Post by Martin Marshalek on 2009-11-24
I still have the restricted-extras package but there used to be (Jaunty and earlier) a linux-restricted-modules package that I believe was another package to handle drivers and propriety software in the kernel. It may have been merged into the header packages now though.

---

### Post by 73ckn797 on 2009-11-24
> **Martin Marshalek said:**
> I still have the restricted-extras package but there used to be (Jaunty and earlier) a linux-restricted-modules package that I believe was another package to handle drivers and propriety software in the kernel. It may have been merged into the header packages now though.

I noticed that difference too but figured it may have been merged. I have not looked into whether that is the case or not.

---

