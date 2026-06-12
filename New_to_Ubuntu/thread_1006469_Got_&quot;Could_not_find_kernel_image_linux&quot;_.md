---
title: "Got &quot;Could not find kernel image: linux&quot; error from external drive installation"
date: 2008-12-09
forum: New to Ubuntu
---

### Post by bodzasfanta on 2008-12-09
I decided to install Ubuntu 8.10 to my 20 GB external HDD.

I tried the installation from Ubuntu (the official startup disk creator) and from Windows (UNetBootIn) too.

The problem is that always got the "Could not find kernel image: linux" error message when try to boot.

I've read that there is a solution to copy isolinux.cfg from /isolinux library to the root and then overwrite syslinux.cfg file.
That doesn't help me.

Do you know any solution?

---

### Post by gettinoriginal on 2008-12-09
I did a google search of ubuntu forums for kernel error, and it seems that it depends on what type of disc you used and the burner used.  To many posts to repeat here, but if you google > ubuntu forums could not find kernel error, you can pick through those to see if anything helps.

Good luck :p

---

### Post by klausthorn on 2008-12-15
I had the same error and I could help myself by looking for the filenames of the kernel (a file with linu or kern in its name) and the initial ramdisk (most of the tiem it has init in its name) and reading the isolinux.cfg.

Together I quickly had a working line that I typed in after the "boot:" prompt, appearing right after the error. This was the line in my case:

ubnkern initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper

in your case it will be different, but the syntax will be the same. first the filename of the kernel, then options similar to the above

---

