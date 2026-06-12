---
title: "how to create img files for grub"
date: 2009-08-28
forum: New to Ubuntu
---

### Post by suoko on 2009-08-28
hi,
i have the following question:
I'd like to create a geexbox version which can be booted from grub just like xpud works [see below]
i'd also like to do that with android [[http://www.android-x86.org/dowloads]](http://www.android-x86.org/dowloads])

tnx

-----

Install xPUD on Linux

Download image for Linux: [http://download.xpud.org/xpud-0.9-image](http://download.xpud.org/xpud-0.9-image)

We don't have installer for Linux yet, but you can do it manually by configure your boot loader. For example, if you're using GRUB on first partition:

title		xPUD 0.9
root		(hd0,0)
kernel	/xpud-0.9-image noisapnp lang=en quiet

[http://www.xpud.org/download.en.html](http://www.xpud.org/download.en.html)

---

### Post by Mighty_Joe on 2009-08-28
I spent some time looking at getting grub4dos to boot ISO images (my experience summed up [here]("http://ubuntuforums.org/showpost.php?p=7687493&postcount=30")).  Basically, if the developers of the distro Do The Right Thing, it's no problem.  If the developers of the distro haven't taken Grub into consideration when building their image, you're out of luck.
Maybe check with the Android mailing list or forum?

---

### Post by suoko on 2009-08-29
many thanks
must try this liveXP too in year 2001

---

### Post by loomsen on 2009-08-29
You may want to visit my signatures tutorial on grub as well.

Basically you can boot everything with grub...

---

### Post by Mighty_Joe on 2009-09-01
> **loomsen said:**
> You may want to visit my signatures tutorial on grub as well.


I don't see your tutorial addressing booting IMG or ISO disk images.  Am I missing something?

---

