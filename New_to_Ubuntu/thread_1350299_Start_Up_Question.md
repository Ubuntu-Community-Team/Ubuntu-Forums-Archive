---
title: "Start Up Question"
date: 2009-12-09
forum: New to Ubuntu
---

### Post by jaxx21 on 2009-12-09
I have been using Ubuntu dual booted with Windows 7 for a couple of weeks now and I am very pleased with it. However I do have one question, When grub loads I am given the option to boot in Windows or 2.6.31-14-generic, 2.6.31-15-generic, and as of my most recent update 2.6.31-16-generic. Which one is suggested I boot with, and if I only need one how do I remove the others? Please be thorough with the answer as I am very new to Ubuntu. Thanks in advance.

---

### Post by m4tic on 2009-12-09
What version of ubuntu are you on now,

---

### Post by JBAlaska on 2009-12-09
Always choose the top (Highest number kernel), in this case 2.6.31-16-generic, unless you have a problem booting that kernel, then you can try a earlier one.

---

### Post by sisco311 on 2009-12-09
> **m4tic said:**
> What version of ubuntu are you on now,

linux-image-2.6.31-16-generic is the Karmic kernel.


@OP:

Search for *linux-image* in Synaptic and remove the unneeded version(s). **Be careful, don't remove the current kernel!**

For detailed instructions see:
[thread=1195275]The Grub 2 Guide[/thread] *#7. Removing Entries from Grub 2*

---

### Post by m4tic on 2009-12-09
never happened when i updated a kernel or ubuntu version b4

---

### Post by jaxx21 on 2009-12-09
Thank you to all that posted, this was very helpful.

---

### Post by presence1960 on 2009-12-09
remove linux-image-2.6.31-x & linux-headers-2.6.31-x from Syanaptic.

It is not mandatory but considered prudent to leave a backup (usually the next most recent kernel) as a backup in case you can't boot the newest kernel for whatever reason.

After uninstalling from Synaptic open a terminal and run ```
sudo update-grub
``` to generate an updated grub.cfg if you are using GRUB 2

---

### Post by sisco311 on 2009-12-09
> **presence1960 said:**
> remove linux-image-2.6.31-x & linux-headers-2.6.31-x from Syanaptic.

It is not mandatory but considered prudent to leave a backup (usually the next most recent kernel) as a backup in case you can't boot the newest kernel for whatever reason.

After uninstalling from Synaptic open a terminal and run ```
sudo update-grub
``` to generate an updated grub.cfg if you are using GRUB 2

+1 for the backup kernel.


You don't have to run update-grub, it's executed by the postrm script of the kernel image. ;)

---

