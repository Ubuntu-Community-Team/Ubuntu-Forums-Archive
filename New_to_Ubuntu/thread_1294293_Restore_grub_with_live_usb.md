---
title: "Restore grub with live usb"
date: 2009-10-18
forum: New to Ubuntu
---

### Post by jimingkui on 2009-10-18
Today I reinstalled XP,and grub missed.I boot up ubuntu with a live usb,try following to restore grub


[I]sudo grub
root (hd0,6)
setup (hd0)[/I]

But it tells me could not mount the partition.

I can't find my ubuntu live-cd,and these commands should restore the grub if boot from live-cd.

Question:How can I restore grub with this live-USB?

---

### Post by rajeev1204 on 2009-10-18
> **jimingkui said:**
> Today I reinstalled XP,and grub missed.I boot up ubuntu with a live usb,try following to restore grub


[I]sudo grub
root (hd0,6)
setup (hd0)[/I]

But it tells me could not mount the partition.

I can't find my ubuntu live-cd,and these commands should restore the grub if boot from live-cd.

Question:How can I restore grub with this live-USB?

There is a 'rescue a broken system' in the live usb.try that.

---

