---
title: "Create LiveCD with latest kernel"
date: 2009-06-02
forum: New to Ubuntu
---

### Post by furialis on 2009-06-02
Just like the title says, I followed [this]("http://ubuntuforums.org/showthread.php?t=311158") thread, but I'd like to have a LiveCD with the latest kernel. Thanks.

---

### Post by LewRockwell on 2009-06-02
> **furialis said:**
> Just like the title says, I followed [this]("http://ubuntuforums.org/showthread.php?t=311158") thread, but I'd like to have a LiveCD with the latest kernel. Thanks.

123 pages spanning two years, yikes, my condolences to your eye-strain.

---

### Post by philinux on 2009-06-02
This might help.

[http://www.geekconnection.org/remastersys/remastersystool.html](http://www.geekconnection.org/remastersys/remastersystool.html)

---

### Post by furialis on 2009-06-02
I tried remastersys, but the LiveCD drops to a intramfs shell at startup. And for some reason, I haven't had any luck with remastersys on Jaunty.

---

### Post by furialis on 2009-06-02
I did a fresh install, updated, rebooted, updated the kernel, opened Synaptic and removed all references to the old kernel, rebooted, ran sudo apt-get update-initramfs, then installed remastersys and made a dist copy.

The dist .iso is huge, 2.8 GB. Is that because the new kernel has a bunch of new stuff, or is that because the old one is still there? 

I think I completely removed the old kernel, but I'm not sure. Is there an official procedure that I'm missing?

When the DVD boots it drops to a busybox shell. What does that mean?

Thanks for all the help.

---

