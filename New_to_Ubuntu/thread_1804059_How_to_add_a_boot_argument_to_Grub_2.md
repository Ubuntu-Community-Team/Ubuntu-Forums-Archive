---
title: "How to add a boot argument to Grub 2?"
date: 2011-07-14
forum: New to Ubuntu
---

### Post by gamma-andromedae on 2011-07-14
Hello everyone,
 
I'm still new to Ubuntu (v11.04). It works fine so far, except that on my Lenovo Idea U160, the screen does not wake up again from suspend mode, which is a well-known issue.
 
Now I wonder *where* to place the proposed workaround
 
**i915.lvds_use_ssc=0** (disabling the SSC functionality of the i915 chipset).
 
As far as I seem to understand now - but please tell me if I'm wrong - this line ought to be added in the file **'/etc/default/grub'**, followed by a **'grub-update'** in order to forward this change to the file '/boot/grub/grub.cfg' and then a restart!?
 
Can anyone confirm that this is the right way to proceed, or else tell me what to do instead!? Thank you very much!

---

### Post by mcduck on 2011-07-14
Yes, /etc/default/grub is the right place and indeed you'll need to run "sudo grub-update" afterwards to generate the actual config file Grub uses when booting.

---

### Post by gamma-andromedae on 2011-07-14
"Kiitos" for the immediate reply!!! :D

---

