---
title: "Persisting Problem Of Random Kernel Panics"
date: 2011-07-08
forum: New to Ubuntu
---

### Post by zorbama on 2011-07-08
Hello,
I have already posted on this, but since then I didn't find any solution.
I'm having a problem of kernel panics appearing randomly on my computer. I tried many things, like cleaning the hardware, installing a different graphic driver, deleting and configuring some files, but as of yet nothing really works. This happens in the Ubuntu classic no effects mode as well.
I realized that it might have something to do with the kernel having a hard time connecting with the graphic card, and that upgrading the kernel to 2.6.39 could fix this issue. I tried doing that according to the guide here: [http://ubuntuguide.net/ubuntu-11-04-upgrade-linux-kernel-to-2-6-39-0](http://ubuntuguide.net/ubuntu-11-04-upgrade-linux-kernel-to-2-6-39-0), but I wasn't successful, as the kernel has been removed from the repository they're describing.
So now I'm pretty much stuck, and I have no idea what I should try next to stop this. Does anyone have an idea?
Thanks in advance! :)

---

### Post by zorbama on 2011-07-09
Anyone? I'm really stuck here, and I'd love to figure this out.

---

### Post by mrhhug on 2011-07-09
where is this kernel attack error comming from? a log file? you say your in a panic, did you try a reinstall? you shouldn't have to reinstall but how is it telling you that your having kernel errors?

---

### Post by jtarin on 2011-07-09
[Try 3.0 rc6 instead.]("http://ubuntuguide.net/how-to-install-linux-kernel-3-0-rc2-in-ubuntu-11-04-natty-narwhal") The article says rc2 but its a month old and rc6 is out. There's a [link ]("http://kernel.ubuntu.com/~kernel-ppa/mainline/")on the page.

---

### Post by zorbama on 2011-07-09
> **jtarin said:**
> [Try 3.0 rc6 instead.]("http://ubuntuguide.net/how-to-install-linux-kernel-3-0-rc2-in-ubuntu-11-04-natty-narwhal") The article says rc2 but its a month old and rc6 is out. There's a [link ]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/")on the page.

Thank you for the reply. :)
I tried to install it, but I couldn't: the second file installed, but it had a mysterious problem which I didn't quite understand, and the third file just couldn't be installed at all. I tried installing several other kernels with the method described in that article, but I couldn't find them in the startup manager, and I wasn't able to switch to them.

---

### Post by jtarin on 2011-07-09
As you can see it has been installed on 10.10 following instructions and behaving great, I should say.:P

---

