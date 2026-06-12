---
title: "Old Versions in GRUB After Clean Install &amp; Updates"
date: 2010-01-23
forum: New to Ubuntu
---

### Post by Cody Larson on 2010-01-23
I just completed my first clean install of the latest Ubuntu. After install I performed all of the updates in the Update Manager. However, now in GRUB it shows double the Linux options. I now have:
```
Ubuntu, Linux 2.6.31-17-generic
Ubuntu, Linux 2.6.31-17-generic (recovery mode)
Ubuntu, Linux 2.6.31-14-generic
Ubuntu, Linux 2.6.31-14-generic (recovery mode)
```I suppose I don't need the older -14 versions so can I remove them from the list? Do I have a double OS install some how on accident now?

---

### Post by NCLI on 2010-01-23
You don't need them, no. It's not a double-install though, don't worry. 

[This thread]("http://ubuntuforums.org/showthread.php?t=1195275")(Specifically section 7) should tell you everything you want to know about GRUB2. Please feel free to ask if there's anything in there you need to have explained in more detail.

---

### Post by audiomick on 2010-01-23
You can remove old kernels, but it is not a bad  idea to leave at least two on the machine. That way, if you mess up the one your running, you can still boot into the older one.

---

### Post by Cody Larson on 2010-01-23
Thank you for pointing me to that thread. I completely removed the the 3 header and image packages in Synaptic, however, I still see the the Kernals in GRUB. I am dual booting with Windows 7. The GRUB version is 1.97 beta4.

Any ideas?

---

### Post by drs305 on 2010-01-23
> **Cody Larson said:**
> Thank you for pointing me to that thread. I completely removed the the 3 header and image packages in Synaptic, however, I still see the the Kernals in GRUB. I am dual booting with Windows 7. The GRUB version is 1.97 beta4.

Any ideas?

Yes. You must run "sudo update-grub" to update the menus. Did you do that?

---

### Post by Cody Larson on 2010-01-23
Ah, I didn't realize that must be run every time. Thank you for clearing that up. All set now.

---

