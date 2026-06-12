---
title: "How to update drivers?"
date: 2011-05-02
forum: New to Ubuntu
---

### Post by listerdl on 2011-05-02
If I go to System > Admin > Hardware Drivers - it says that I have no proprietary drivers.

This seems wrong.

I am very keen to update my drivers and cannot understand how else to do it.

Thanks

---

### Post by beew on 2011-05-02
Which driver? For what? 

You have to give more specific information for people to help you.

---

### Post by listerdl on 2011-05-03
Yup sorry about that.

The chipset is as follows: Mobile Intel(R) 4 Series Express Chipset Family

The reason why I am keen to solve and upgrade this, (if possible) is b/c my SSD freezes every now and again. I have run several SMART tests that all come back 100% healthy, in linux and windows, and I have never had a crash in windows, (I dual boot).

My hunch is that the linux ubuntu kernel does not like the SSD and is trying to restrict the read and write speeds. Perhaps upgrading the chipset will rememdy this?

Thanks!

---

### Post by 3rdalbum on 2011-05-03
> **listerdl said:**
> Yup sorry about that.

The chipset is as follows: Mobile Intel(R) 4 Series Express Chipset Family

The reason why I am keen to solve and upgrade this, (if possible) is b/c my SSD freezes every now and again. I have run several SMART tests that all come back 100% healthy, in linux and windows, and I have never had a crash in windows, (I dual boot).

My hunch is that the linux ubuntu kernel does not like the SSD and is trying to restrict the read and write speeds. Perhaps upgrading the chipset will rememdy this?

Thanks!

You don't have any proprietary drivers on your system, which is correct. Proprietary means "closed-source", basically; all the drivers you're using are open-source.

The Linux kernel does not try to restrict SSDs at all. An SSD is just another "block device" and the kernel doesn't really make distinctions between these sorts of devices. Also, there's no driver specific to SSDs either (they communicate with the computer using standard mass storage drivers).

I don't know what the problem is, but drivers are not the problem and you *really* shouldn't be fiddling around with them. Perhaps a BIOS setting might be wrong - your system might be set to use IDE compatibility mode rather than full SATA speeds?

---

### Post by listerdl on 2011-05-03
> **3rdalbum said:**
> your system might be set to use IDE compatibility mode rather than full SATA speeds?

thanks for your message - is this within the BIOS?

---

### Post by 3rdalbum on 2011-05-03
Yes, it's in the BIOS - sorry I wasn't more clear on this.

---

