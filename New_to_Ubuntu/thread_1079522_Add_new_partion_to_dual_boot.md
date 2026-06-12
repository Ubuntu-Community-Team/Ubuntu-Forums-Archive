---
title: "Add new partion to dual boot"
date: 2009-02-24
forum: New to Ubuntu
---

### Post by FreewheelinFrank on 2009-02-24
I have a dual-boot computer with Windows XP and Ubuntu. I would like to shrink the Windows partition so I can play around with other distros.

The Windows partition has bad sectors, so I'll need to use ntfsresize to force a resize.

How can I then create a new partition in the empty space ready for installation?

Do I need to edit GRUB to tell it the Windows partition has shrunk?

Any help appreciated.

Ta!

---

### Post by Therion on 2009-02-24
Your best option, most likely, is to use a Parted Magic LiveCD, available here:

[http://partedmagic.com/](http://partedmagic.com/)

Burn the .iso to a bootable CD and you should be able to fully manipulate all your existing partitions and create a new one as you need.

---

### Post by theozzlives on 2009-02-24
It'd be easier to try other distros in a VM like VirtualBox.

---

### Post by FreewheelinFrank on 2009-02-24
> **Therion said:**
> Your best option, most likely, is to use a Parted Magic LiveCD, available here:

[http://partedmagic.com/](http://partedmagic.com/)

Burn the .iso to a bootable CD and you should be able to fully manipulate all your existing partitions and create a new one as you need.

Thanks.

Can it force a resize where there are bad sectors like ntfsresize?

---

### Post by FreewheelinFrank on 2009-02-24
> **theozzlives said:**
> It'd be easier to try other distros in a VM like VirtualBox.

Thanks, but my Windows partition is sitting mostly empty and unused. There's easily 15G I can chop off it.

---

### Post by Therion on 2009-02-24
> **FreewheelinFrank said:**
> Thanks.

Can it force a resize where there are bad sectors like ntfsresize?
I don't know.  But it's a pretty whizbang application.  I'd start with this and see if it works.  

If still no joy, post back and we'll go from there.

---

