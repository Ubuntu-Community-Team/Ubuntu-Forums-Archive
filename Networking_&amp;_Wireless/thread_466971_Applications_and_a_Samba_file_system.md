---
title: "Applications and a Samba file system"
date: 2007-06-07
forum: Networking &amp; Wireless
---

### Post by matthewboh on 2007-06-07
I've got my LAMP server up and running, a Samba share too and am happily working between my Ubuntu PC (more and more) and occasionally on my Windows XP PC.  However, I find that some applications don't or can't find the Samba share and I'm forced to copy files back and forth.  One such application is Bluefish.  Is there an add-in or plug-in to Gnome that helps these applications find the Samba share?

Thanks,

Matt Burkhardt
[http://www.imparisystems.com](http://www.imparisystems.com)

---

### Post by kidders on 2007-06-29
Hi there,

Assuming they're properly mounted, not many applications can distinguish between Samba shares and other filesystems ... after all, using them is a matter of navigating to the right place (eg /media/myshare). What sort of problem are you having exactly?

Incidentally, Bluefish seems to have gnome-vfs support (useful for accessing network shares without mounting them) ... in fact it *requires* it afaik.

---

