---
title: "Does anyone know if this patch..."
date: 2009-08-24
forum: New to Ubuntu
---

### Post by coldReactive on 2009-08-24
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/110784](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/110784)

Does anyone know if the patch attached to that bug will be applied to the kernel in ubuntu? Because having the battery drained while the machine is off is troublesome.

---

### Post by TheLions on 2009-08-24
> **coldReactive said:**
> [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/110784](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/110784)

Does anyone know if the patch attached to that bug will be applied to the kernel in ubuntu? Because having the battery drained while the machine is off is troublesome.

it seem patch  has been applied to kernels 2.6.27-7.10 and above, you can try with newest kernel available (2.6.31-rc7) at [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.31-rc7/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.31-rc7/)

---

### Post by coldReactive on 2009-08-24
> **TheLions said:**
> it seem patch  has been applied to kernels 2.6.27-7.10 and above, you can try with newest kernel available (2.6.31-rc7) at [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.31-rc7/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.31-rc7/)

But I have 2.6.28 on my UNR, and it still has the problem.

---

### Post by TheLions on 2009-08-24
> **coldReactive said:**
> But I have 2.6.28 on my UNR, and it still has the problem.

according to [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/110784/comments/50](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/110784/comments/50) it has been patched. Find out, install newer kernel.:-\"

---

### Post by coldReactive on 2009-08-24
> **TheLions said:**
> according to [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/110784/comments/50](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/110784/comments/50) it has been patched. Find out, install newer kernel.:-\"

I don't want to destroy it anymore than it is. Will wait for Karmic to see if the issue is fixed *sigh*

---

### Post by coldReactive on 2009-08-24
Which deb would I install first though? ( for 2.6.31 )

---

### Post by TheLions on 2009-08-24
> **coldReactive said:**
> Which deb would I install first though? ( for 2.6.31 )

in this particular order:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.31-rc7/linux-headers-2.6.31-020631rc7_2.6.31-020631rc7_all.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.31-rc7/linux-headers-2.6.31-020631rc7_2.6.31-020631rc7_all.deb)
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.31-rc7/linux-headers-2.6.31-020631rc7-generic_2.6.31-020631rc7_i386.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.31-rc7/linux-headers-2.6.31-020631rc7-generic_2.6.31-020631rc7_i386.deb) **or** [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.31-rc7/linux-headers-2.6.31-020631rc7-generic_2.6.31-020631rc7_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.31-rc7/linux-headers-2.6.31-020631rc7-generic_2.6.31-020631rc7_amd64.deb)
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.31-rc7/linux-source-2.6.31_2.6.31-020631rc7_all.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.31-rc7/linux-source-2.6.31_2.6.31-020631rc7_all.deb)
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.31-rc7/linux-image-2.6.31-020631rc7-generic_2.6.31-020631rc7_i386.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.31-rc7/linux-image-2.6.31-020631rc7-generic_2.6.31-020631rc7_i386.deb) **or** [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.31-rc7/linux-image-2.6.31-020631rc7-generic_2.6.31-020631rc7_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.31-rc7/linux-image-2.6.31-020631rc7-generic_2.6.31-020631rc7_amd64.deb)

---

### Post by coldReactive on 2009-08-24
Sorry, I read wrong, going to test.

---

### Post by TheLions on 2009-08-24
> **coldReactive said:**
> headers can't be installed, [SIZE="7"]it depends on itself[/SIZE]

I installed it several hours ago :confused:

maybe i gave wrong ordering, here is instalation guide: [http://www.ramoonus.nl/2009/06/10/linux-kernel-2-6-30-installation-guide-for-ubuntu-and-debian-linux/](http://www.ramoonus.nl/2009/06/10/linux-kernel-2-6-30-installation-guide-for-ubuntu-and-debian-linux/) just replace 2.6.30 with 2.6.31

---

### Post by coldReactive on 2009-08-24
I re-did it, and now it just shows a blank screen (after the ubuntu splash) when I boot to that kernel, sadly.

---

### Post by TheLions on 2009-08-24
last try: install 2.6.30 instead 2.6.31 since i'm out of ideas. Also on that bug report that you gave me it says that current workaround is to turn off wirelles before shuting

---

### Post by coldReactive on 2009-08-24
> **TheLions said:**
> turn off wirelles before shuting

Yeah, that's... not going to happen. Not when Windows is the only one that can enable wireless.

---

