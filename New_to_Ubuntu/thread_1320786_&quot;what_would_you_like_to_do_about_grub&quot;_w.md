---
title: "&quot;what would you like to do about grub&quot; window?"
date: 2009-11-09
forum: New to Ubuntu
---

### Post by ave2 on 2009-11-09
I just installed the latest updates and I get a window saying
debconf
configuring grub-pc
what would you like to do about grub
I have the following options:
1)install the package maintainer's version
2)keep the local version currently installed
3)show the differences between the versions
4)show a side-by-side difference between the versions
5)show a 3-way difference between available versions
6)do a 3-way merge between available versions (experimental)
7)start a new shell to examine the situation

what does this mean- which one should I choose?

---

### Post by karimruan on 2009-11-09
I would keep the original version. Not sure what would happen if you updated the version, could possibly cause some compatibility errors?

---

### Post by ranch hand on 2009-11-09
Go with the maintainers version.  Grub2 is a work in progress.  Each update (so far) has improved something and hurt nothing on the several OS' I am using it on (9.04, 9.10, 10.04testing and PhatDebian).

Read the link in my sig.  Check the links in it, particularly the first 3.

---

### Post by mikewhatever on 2009-11-09
Actually, the maintainer's version improves nothing at all in GRUB. That message usually shows when the kernel is update, and if you choose maintainer's, the new kernel should be added to the menu, but if keep current, the menu will not be updated.
Edit: In this particular case, it wasn't the kernel, but Grub itself, so that there is no need to edit the menu manually after keeping the current version.
I have to say, it's a rather confusing message, and I can't understand the purpose of it. I always end up keeping the current version, and add the new entries manually.

---

### Post by philinux on 2009-11-09
> **ranch hand said:**
> Go with the maintainers version.  Grub2 is a work in progress.  Each update (so far) has improved something and hurt nothing on the several OS' I am using it on (9.04, 9.10, 10.04testing and PhatDebian).

Read the link in my sig.  Check the links in it, particularly the first 3.

You have to be careful with this. The package maintainers version overwrites /etc/default/grub and probably other custom files.. This is fine if you have no custom entries. Even if you do it makes a copy of the old one in /etc/default/grub.ucf-old. You just need to be aware.

---

### Post by ranch hand on 2009-11-09
I have never had a custom file over written.  Neither have I lost my configuration in /etc/default/grub.

---

### Post by philinux on 2009-11-10
> **ranch hand said:**
> I have never had a custom file over written.  Neither have I lost my configuration in /etc/default/grub.

I got an update to grub-pc in karmic a couple of days ago, I told it to use the package maintainers version. It overwrote /etc/grub/default and created a backup file. 

Next time I'll choose keep mine. :lolflag:

---

### Post by ranch hand on 2009-11-10
Can't fault you for that.  Probably what I would do too.

---

### Post by Perturbed Penguin on 2009-11-10
From my experience if you have custom settings it will keep those even when you select the 'Maintainers Version' setting. There could easily be exceptions to this that I am not aware of though.

---

### Post by mahy on 2009-12-22
I'd have another question: how do I re-invoke that Debconf window again? I selected the second option, but now I want the first one :)

---

