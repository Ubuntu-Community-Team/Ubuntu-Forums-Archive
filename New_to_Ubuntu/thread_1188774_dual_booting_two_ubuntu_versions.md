---
title: "dual booting two ubuntu versions"
date: 2009-06-16
forum: New to Ubuntu
---

### Post by chf on 2009-06-16
Hello,

I have a question about dual booting two ubuntu versions on my computer (no windows on disk). I looked a bit around on the internet and there are quite different opinions about it - so I wanted to ask if someone has experience with it using the newer ubuntu versions 8.10 - 9.04.

Currently I'm running one ubuntu version (8.10) and I have set it up so I can be productive with it for my studies. However I also want one partition with a newer version so I can test a bit and make some experiments.

Will it give me any difficulties if I just install a newer version on a second partition. Will there be any difficulties with GRUB?

Hope someone can answer.

Best regards

chf

---

### Post by briguy47 on 2009-06-16
> **chf said:**
> Hello,

I have a question about dual booting two ubuntu versions on my computer (no windows on disk). I looked a bit around on the internet and there are quite different opinions about it - so I wanted to ask if someone has experience with it using the newer ubuntu versions 8.10 - 9.04.

Currently I'm running one ubuntu version (8.10) and I have set it up so I can be productive with it for my studies. However I also want one partition with a newer version so I can test a bit and make some experiments.

Will it give me any difficulties if I just install a newer version on a second partition. Will there be any difficulties with GRUB?

Hope someone can answer.

Best regards

chf


I don't think you will run into any problems if you install the newer version to it's OWN partition.  It should play nice with Grub.  I think, that worse case scenario, you might need to fiddle with Grub, but I doubt that.

Also, if things go bad, it shouldn't be too hard to revert back.  It would be a matter of removing the second partition and fixing up your Grub menu.  ( I can help with that, if things don't go well.)  :D

---

### Post by HereInOz on 2009-06-16
What about installing Virtual Box on your 8.10 machine, then installing 9.04 in a virtual machine.  

If you use bridged networking, rather than NAT (you can still use NAT but I have found it a bit slow), you can set up a connection to your home folder on the 8.10 machine so that you can access the home folder on the 8.10 machine from the 9.04 machine.  You would have to use either NFS or Samba to accomplish this, but it works well.  

Just a thought.

---

### Post by chf on 2009-06-16
thanks for the answers.

I think I will try to install it on the second partition. I hope GRUB will work correctly.

I will post my experience here later.

Best regards

chf

---

### Post by The Cog on 2009-06-16
Installing on the second partition will normally reinstall GRUB to use the menu.lst on that second partition. No real problem there.

It will normally set that second menu.lst to offer an option to boot from the first Ubuntu. But it wants to load a particular version of kernel (the version in use at the time of the second install). This means that if you update the first kernel, the second menu.lst is left pointing to the old version. I always fix my menu.lst to point to /vmlinuz and /initrd, which are symlinks to the real ones and always point to the latest version.

If you want to revert to the original menu.lst on the first install, boot up the original version and run:
sudo grub-install /dev/sda
which overwrites the existing GRUB with one for the first install again. You may then need to manually add the second install as an option in XXXXXXXXXXXX Correction: /boot/grub/menu.lst. A bit of a brain-fart there. Thanks for the correction Celauran.

---

### Post by Celauran on 2009-06-16
> **The Cog said:**
> You may then need to manually add the second install as an option in /etc/init.d/menu.lst.

/boot/grub/menu.lst

---

### Post by chf on 2009-06-16
hello again,

I'm a bit confused now. Which problems will I have when the GRUB points to the old kernel version? Is it possible to give an example of how the menu.lst should look like with /vmlinuz and /initrd?

best regards

christoph

---

### Post by philinux on 2009-06-16
Here is how I dual boot on two disks.

This is the first discs menu.lst, the end bit, using the stanza configfile.

```
## ## End Default Options ##

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		40558149-061d-43bc-9068-9c34dbdfa6c7
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=40558149-061d-43bc-9068-9c34dbdfa6c7 ro splash vga=792 quiet 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		40558149-061d-43bc-9068-9c34dbdfa6c7
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=40558149-061d-43bc-9068-9c34dbdfa6c7 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		40558149-061d-43bc-9068-9c34dbdfa6c7
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

title        SDB Jaunty
configfile   (hd1,0)/boot/grub/menu.lst 
```

---

### Post by H2SO_four on 2009-06-16
This guide may be helpful to you.

[http://www.iball.id.au/node/26](http://www.iball.id.au/node/26)

---

### Post by chf on 2009-06-16
hmm...maybe I wait a bit with the install. I have a version running right now, which I really need and I don't want to mess something up.

but thank you for all the good answers.

best regards

chf

---

### Post by tea for one on 2009-06-16
Good evening

When you install your second Ubuntu OS on the same hard drive with a new partition, the second OS will probably take control of Grub - i.e. you will easily be able to boot into your second OS.

So far, so good.

Your first OS is very important with all your data etc; therefore you will probably need to follow this tutorial to allow your first OS to control Grub:-

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

When you have successfully allowed your first OS to control Grub, you can then navigate to /boot/grub/menu.lst of your second OS and copy the instructions to the menu.lst of your first OS.

The example below is an installation of Puppy Linux, which I have installed on a flash drive but access is controlled by Grub via my principal Ubuntu OS, located on my internal hard drive.

title           Puppy Linux 400
root		(hd1,0)
kernel          /vmlinuz root=/dev/hd1 ro vga=normal
initrd		/initrd.gz

If you follow the advice on the above tutorial, you should always manage to boot to your principal OS and it will allow you to experiment confidently with alternative OS installations.

Good luck with your endeavours

---

### Post by Miljet on 2009-06-16
The easiest solution for me is when you install the second version do NOT install a boot manager. There is a tab labeled "Advanced" that you can click during install that gives you the option of installing GRUB or not. That way your GRUB and menu.lst for the partition you are now using is not affected. Then it is a simple matter of editing the original menu.lst file to add the new version.

Btw, I always install each new version this way to make sure that everything works before switching. When I am satisfied, I copy over my files and leave the old version in place until the next version is released.

---

### Post by bodhi.zazen on 2009-06-16
> **philinux said:**
> Here is how I dual boot on two disks.

This is the first discs menu.lst, the end bit, using the stanza configfile.

```
## ## End Default Options ##

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        40558149-061d-43bc-9068-9c34dbdfa6c7
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=40558149-061d-43bc-9068-9c34dbdfa6c7 ro splash vga=792 quiet 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        40558149-061d-43bc-9068-9c34dbdfa6c7
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=40558149-061d-43bc-9068-9c34dbdfa6c7 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        40558149-061d-43bc-9068-9c34dbdfa6c7
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root

title        SDB Jaunty
configfile   (hd1,0)/boot/grub/menu.lst 
```


+1 this is the way to go.

I find, for some reason, I need to specify the root partition with configfile

```
title Ubuntu 9.10 Alpha2
root (hd0,1)
configfile (hd0,1)/boot/grub/menu.lst
```

I posted a thread on how to multiboot [How to Multi-boot (Maintain more then 2 OS) - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=724817")

---

