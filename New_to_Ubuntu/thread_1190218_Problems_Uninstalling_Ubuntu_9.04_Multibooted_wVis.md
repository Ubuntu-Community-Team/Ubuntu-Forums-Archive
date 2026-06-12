---
title: "Problems Uninstalling Ubuntu 9.04 Multibooted w/Vista 64 bit."
date: 2009-06-17
forum: New to Ubuntu
---

### Post by joelrstevens on 2009-06-17
I've sucessfully installed Ubuntu 9.04 on my Vista laptop. I have a HP that runs Vista Home 64bit and the partioning of the hard drive was done through the Vista disk management tool. I eventualy had to uninstall Ubuntu, and when I restored the Vista partition back to it's original size I had problems booting back to Vista.  I kept getting some sort of GRUB error message. Everything was intact except for the boot loader portion of the Vista O.S.  The only way I could boot into Vista was by using a Ultimate Boot CD utility I found.  I would like to put Ubuntu back on, but just in case I have to uninstall it again I would like to restore Vista fully, boot loader and all!  Is there any way I can acheive a multiboot partition without destroying the boot portion of the vista os?

---

### Post by ptn107 on 2009-06-17
Defrag Vista twice, preferably with another utility besides the one included with windows.  Resize your Vista partition with the disk management console.  Install Ubuntu on the free space.  GRUB will install itself to the MBR and add a link to the vista bootloader program.  If you ever uninstall Ubuntu you will have to restore Vista's bootloader manually using the Vista DVD, that's just the way windows is.

---

### Post by joelrstevens on 2009-06-17
So a third party partitioning application like GParted will not prevent the removal of the Vista boot loader?

---

### Post by LewRockwell on 2009-06-17
you might also find these useful as well:

Super Grub Disk

Parted Magic

Clonezilla

---

### Post by gn2 on 2009-06-17
> **joelrstevens said:**
> Is there any way I can acheive a multiboot partition without destroying the boot portion of the vista os?

Yes. Install Ubuntu using the Alternate CD and when it asks where to install Grub, install it into the /partition, not the MBR.
(Live CD installation might be able to do this now, don't know, I never use it)

You can then use an alternative bootloader like GAG, WinGrub or SuperGrub to boot Ubuntu.

Lots of info on booting at the excellent [Hermanzone website]("http://members.iinet.net/~herman546/index.html").

A [Vista Recovery CD]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/") is worth having if you don't have a Vista installation DVD.

---

### Post by joelrstevens on 2009-06-17
That sounds exactly like the option I'm looking for!!!!!!
The boot ISO I'm using is the AMD 64bit downloaded from the website.  Is this different from this alternate CD you are talking about?
If so, where do I go to get it? I don't remember seeing that option in installation. Is wingrub proprietary to Vista?

---

### Post by gn2 on 2009-06-17
The Alternate CD is an install only disc, you can download it from [here]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate").

[WinGrub]("http://members.iinet.net.au/~herman546/p9.html") isn't proprietary, but it is installed in Windows.
Another option is [EasyBCD]("http://neosmart.net/wiki/display/EBCD/EasyBCD+Documentation+Home").

---

### Post by joelrstevens on 2009-06-17
Will this provide me with a full version of ubuntu or a text version?  Or is the instilation itslef text only?

---

### Post by gn2 on 2009-06-17
Full version, exactly the same system as provided by the regular Live CD.

---

