---
title: "Getting rid of GRUB and going back to Vista from dualboot"
date: 2009-01-29
forum: New to Ubuntu
---

### Post by pyrofyr on 2009-01-29
Right now I have Ubuntu and Vista dualbooting, but I want to get rid of Ubuntu due to previous problems with it, and not wanting to try it on this particular machine.

I made a bootcd of the super grub, however after I activate and 'fix' Windows (MBR), it tells me that BOOTMGR is missing. Is there something simple I'm forgetting to do Super Grub first, or am I better off just going to find my friggin' Vista CD and using that, because I'll have to download extra stuff and what not?

It has no problem using GRUB, and I've yet to get rid of the Ubuntu partition, but I want to go single boot, because GRUB just adds to the load time for me for now.

---

### Post by kansasnoob on 2009-01-29
> **pyrofyr said:**
> Right now I have Ubuntu and Vista dualbooting, but I want to get rid of Ubuntu due to previous problems with it, and not wanting to try it on this particular machine.

I made a bootcd of the super grub, however after I activate and 'fix' Windows (MBR), it tells me that BOOTMGR is missing. Is there something simple I'm forgetting to do Super Grub first, or am I better off just going to find my friggin' Vista CD and using that, because I'll have to download extra stuff and what not?

It has no problem using GRUB, and I've yet to get rid of the Ubuntu partition, but I want to go single boot, because GRUB just adds to the load time for me for now.

You'll need to restore Vista's mbr. If you have no disc you can get one here:

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

Instructions here:

[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

You want to "fix boot" and "fix mbr"!

---

### Post by pyrofyr on 2009-01-29
Kay, thanks. Ended up finishing that up in less than 5 minutes.

Now I just have to figure out how to get this free space added to my main partition (where Vista OS is) but I'll google that.

--
Which I also figured out, I figured it would be something simple, always is with Vista, it's just one of those things not explained.

Thank you very much for your help, finally got this stuff fixed, and now I can go back to just using this laptop for school soon.

---

