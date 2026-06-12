---
title: "Problems installing the latest kernel"
date: 2011-09-05
forum: New to Ubuntu
---

### Post by jfed on 2011-09-05
I run xubuntu 10.10 and ran the package updater hoping to update to the latest kernel. But all it did was up me from 2.6.27 to 2.6.30

I thought Linus released 3.0 with Linux's 20th birthday?
How do I update to the latest?

---

### Post by jtarin on 2011-09-05
Keep a working kernel to boot from if things go wrong.

[Words of caution and Procedure.]("https://wiki.ubuntu.com/Kernel/MainlineBuilds")

[Procedure 2]("http://tuxfiction.wordpress.com/2011/06/20/upgrading-your-mainline-kernel-in-ubuntu/")

---

### Post by realzippy on 2011-09-05
You can install kernels manually,as described here eg :
[http://www.unixmen.com/linux-tutorials/780-upgrade-your-kernel-the-safe-way-in-ubuntu-linuxmint](http://www.unixmen.com/linux-tutorials/780-upgrade-your-kernel-the-safe-way-in-ubuntu-linuxmint)

---

### Post by garvinrick4 on 2011-09-05
Next post please wrong link to module-init-tools here.

---

### Post by garvinrick4 on 2011-09-05
You will also need to upgrade "module-init-tools" they have built files in launchpad.
They request module-init-tools_3.13-1ubuntu1_amd64.deb or your 32 bit whichever you use.
Is below  select build and will give you .deb 
[https://launchpad.net/ubuntu/+source/module-init-tools/3.13-1ubuntu1](https://launchpad.net/ubuntu/+source/module-init-tools/3.13-1ubuntu1)

---

### Post by oscarivera9 on 2011-09-05
You want to update to the new kernel 3.0 but you are still using Xubuntu 10.10?  I don't understand.  Actually, I do understand, but still I have to ask, how come you haven't updated yet to Xubuntu 11.04?  The new release 11.10 is out next month and it ships with the new 3.0 kernel.  You can definitely upgrade to the latest kernel manually, but to answer your question as to why you are having a hard time doing it you have to understand that every six months Xubuntu (like all other *buntus) gets updated and part of the update includes the latest (stable) kernel at the time of release.  The key word here is 'stable' because there are times when a new kernel is released and then later found to be unstable, which is why a lot of distributions don't include them at the time of the release.  When you hear that Linus announced the new kernel (3.0) was being released, take it as meaning that from that day forward, distributions may choose to include it with their following release.  It doesn't necessarily mean that an older release will upgrade to that right away.  In fact, many distributions may reach their end of life support and still not have upgraded to that kernel.

---

### Post by jfed on 2011-09-05
> **oscarivera9 said:**
> You want to update to the new kernel 3.0 but you are still using Xubuntu 10.10?  I don't understand.  Actually, I do understand, but still I have to ask, how come you haven't updated yet to Xubuntu 11.04?  The new release 11.10 is out next month and it ships with the new 3.0 kernel.  You can definitely upgrade to the latest kernel manually, but to answer your question as to why you are having a hard time doing it you have to understand that every six months Xubuntu (like all other *buntus) gets updated and part of the update includes the latest (stable) kernel at the time of release.  The key word here is 'stable' because there are times when a new kernel is released and then later found to be unstable, which is why a lot of distributions don't include them at the time of the release.  When you hear that Linus announced the new kernel (3.0) was being released, take it as meaning that from that day forward, distributions may choose to include it with their following release.  It doesn't necessarily mean that an older release will upgrade to that right away.  In fact, many distributions may reach their end of life support and still not have upgraded to that kernel.

Ah thank you, this helped me alot. Though I didn't state it in my first post I was wondering if I could even get the newest kernel for 10.10 (without manually installing, I mean.) And the reason I haven't updated to 11.04 yet is because I was using Gnome2 on 10.10, and have been using Gnome2 since I started using Linux. The new Gnome3 (as far as I know) hasn't been forked yet, except for Arch. So I installed Xfce4 with Gnome2 in 10.10 to get used to it. Although as I'm using it for an alternative to Gnome, not lightweight, I installed Nautilus and compiz etc. I haven't made the change yet because I wasn't ready I guess, haha. Anyway, I'll just install Xubuntu 11.10 when it comes out. And yes I did know that Ubuntu releases another version on the fourth and tenth months of each year.

---

### Post by zika on 2011-09-05
What is happening with /~kernel-ppa/mainline/daily lately...?
It seems to  be dormant...?

---

