---
title: "Virtualbox Failed download"
date: 2010-01-28
forum: New to Ubuntu
---

### Post by GazRockK on 2010-01-28
Hello, 

I tried installing virtualbox to my Ubuntu 9.10, and same to an error.
This is what I was using for installation reference 

[http://www.howtoforge.com/installing-virtualbox-3.1-on-an-ubuntu-9.10-desktop](http://www.howtoforge.com/installing-virtualbox-3.1-on-an-ubuntu-9.10-desktop)

I really don't know what happened. It said to check /var/log/vbox-install.log to see what happened so here you go.

> Attempting to install using DKMS
  removing old DKMS module vboxdrv version  3.1.2

------------------------------
Deleting module version: 3.1.2
completely from the DKMS tree.
------------------------------
Done.

Creating symlink /var/lib/dkms/vboxdrv/3.1.2/source ->
                 /usr/src/vboxdrv-3.1.2

DKMS: add Completed.

Error! Your kernel source for kernel 2.6.31-14-generic cannot be found at
/lib/modules/2.6.31-14-generic/build or /lib/modules/2.6.31-14-generic/source.
You can use the --kernelsourcedir option to tell DKMS where it's located.
Failed to install using DKMS, attempting to install without
Makefile:152: *** Error: unable to find the sources of your current Linux kernel. Specify KERN_DIR=<directory> and run Make again.  Stop.

Anyways, if theres an alternative to vbox then feel free to give it to me. I'll take anything.

If there isn't enough info just ask and I'll do my best. thx.

---

### Post by Hospadar on 2010-01-28
I would think it'd be pulled in by dependencies, but try installing the kernel source package:
```
sudo apt-get install linux-source
```

---

### Post by A&#11375;A on 2010-01-28
I don't know of any GOOD alternatives to vbox. VMware Workstation is ok, but vbox is free and has better features.

---

### Post by GazRockK on 2010-01-28
I followed what hospadar said and entered the code and downloaded the file. the error is still the same. any other solutions?

---

### Post by weichimaster on 2010-01-28
Hi 

Why don't you download it through synaptic? I did this recently, and it worked fine. I think there's a metapackage to get the necessary bits, but I've forgotten its name. I have virtualbox-ose; virtualbox-ose-source and virtualbox-ose-qt installed.

---

### Post by GazRockK on 2010-01-28
> Error! Your kernel source for kernel [COLOR=Red]2.6.31-14-generic[/COLOR] cannot be found at
/lib/modules/2.6.31-14-generic/build or /lib/modules/2.6.31-14-generic/source.
You can use the --kernelsourcedir option to tell DKMS where it's located.
Failed to install using DKMS, attempting to install without
Makefile:152: *** Error: unable to find the sources of your current Linux kernel. Specify KERN_DIR=<directory> and run Make again. Stop.This is from the previously posted error log..
i noticed the "2.6.31-14-generic" bit in there.. just recently i ran "system janitor" (I think that's what it's called) and found three files that could be deleted. The files are pretty vague to me so i can't remember any of them except one, it was similar to an entry as an os boot choice in GRUB. 

When GRUB loads, Ubuntu appears twice, theres "Ubuntu [jumble of numbers and letters ]-17", and Ubuntu [jumble of numbers and letters ]-14. [COLOR=Red]Note the 17 and 14[/COLOR]. I'm always booting the 17 one as my gut tells me that higher numbers = more updates, so when I saw -14 as an entry to be deleted, I went right on ahead, as I really only wanted one Ubuntu boot option in there.

I now realise deleting that "something something -14" might have been the reason for the error. Any way to get it back? [I still have two Ubuntu boot options btw. both 17 and 14.]

Please help. :\

---

### Post by halitech on 2010-01-28
check synaptic for kernel-source and you should find one for -14, install it and see it that helps

---

### Post by Paqman on 2010-01-28
Try reinstalling linux-generic, it'll pull in any of the dependencies you're missing for your current kernel.

---

### Post by GazRockK on 2010-01-29
Do i download them all?

---

### Post by halitech on 2010-01-29
just the -14-generic for either x86 or x86_64 depending on which one you are running

---

### Post by GazRockK on 2010-01-29
I've made some progress.. [see the screenshot]

What's the problem here now?

---

### Post by Paqman on 2010-02-03
> **GazRockK said:**
> Do i download them all?

You should only need linux-generic, it will do all the rest by magic.

---

