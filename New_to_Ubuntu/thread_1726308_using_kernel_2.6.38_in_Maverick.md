---
title: "using kernel 2.6.38 in Maverick"
date: 2011-04-11
forum: New to Ubuntu
---

### Post by beew on 2011-04-11
I have an installation of Maverick on an external drive which I use as a portable as well as for testing purpose. I am wondering if there is a way to use Linux kernel 2.6.38 in it.

---

### Post by wolfen69 on 2011-04-11
Enable backports and see if it's there. If not, there a kernel ppa.

---

### Post by beew on 2011-04-11
Not in the backport (I have  enabled it from the start) The ppa you speak of only backports the kernel to Lucid [https://launchpad.net/~kernel-ppa/+archive/ppa]("https://launchpad.net/%7Ekernel-ppa/+archive/ppa") I am wondering will it be backported to Maverick in the future or is it only for LTS.

---

### Post by coolbrook on 2011-04-11
[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

I'm running 2.6.38.2. I've used the rc and .1.  There's no looking back on Maverick for me, but I still have the 2.6.37 kernel installed and in my grub list, just in case.

---

### Post by beew on 2011-04-11
> **coolbrook said:**
> [http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/")

I'm running 2.6.38.2. I've used the rc and .1.  There's no looking back on Maverick for me, but I still have the 2.6.37 kernel installed and in my grub list, just in case.

You mean you're running 2.6.38.2 in Maverick? The link says it is for Natty.

---

### Post by Locke_99GS on 2011-04-11
```

locke@cerberus:~/.gvfs$ uname -a
Linux cerberus 2.6.38.2-locke-bfs #1 SMP PREEMPT Mon Mar 28 01:10:21 EDT 2011 x86_64 GNU/Linux

locke@cerberus:~/.gvfs$ lsb_release -c
Codename:	maverick

```


Works just fine for me, as did .37 and .36, previously.

---

### Post by coolbrook on 2011-04-11
Yes. I installed the package on my notebook running 10.10 Maverick.

linux-image-2.6.38-02063802-generic_2.6.38-02063802.201103281246_amd64.deb

---

### Post by beew on 2011-04-11
> **coolbrook said:**
> Yes. I installed the package on my notebook running 10.10 Maverick.

linux-image-2.6.38-02063802-generic_2.6.38-02063802.201103281246_amd64.deb

Thanks. I think I should get the 32 bit.

No problem so far? Do these kernels have the Ubuntu patches?

---

### Post by coolbrook on 2011-04-11
No problems.   There was a readahead error during the boot process, but it had no affect on the OS.  I'm not sure what those patches are, but the files are hosted by Ubuntu, so I can only assume that they do.

---

### Post by beew on 2011-04-11
> **coolbrook said:**
> No problems.   There was a readahead error during the boot process, but it had no affect on the OS.  I'm not sure what those patches are, but the files are hosted by Ubuntu, so I can only assume that they do.

Sweet. :) But in case something goes wrong can I just boot into an old kernel and remove the new one (like with Ubuntu tweak's clean kernel function)?

---

### Post by coolbrook on 2011-04-11
Yeah that's true.  I have 2.6.38.2, 2.6.38.1, and whichever 2.6.37 is the most recent in the repositories for Maverick.  They're in my Grub menu.  You can use Synaptic to remove the kernels (images) too.

---

### Post by beew on 2011-04-11
So I would need to download and install the linux image .deb and the linux header .deb that goes with it, right?

Thanks

---

### Post by coolbrook on 2011-04-11
I would unpack both of them.  I'm not sure if the header did anything significant.

---

### Post by beew on 2011-04-12
I have installed the kernel and both headers. No good. Firefox, google earth , Cairo dock and VLC all have problems. Most likely problems with the nouveau driver. So I uninstalled them and now everything is back to normal. :)

Thanks for everyone who has helped out, especially coolbrook. At least I tried. :)

---

