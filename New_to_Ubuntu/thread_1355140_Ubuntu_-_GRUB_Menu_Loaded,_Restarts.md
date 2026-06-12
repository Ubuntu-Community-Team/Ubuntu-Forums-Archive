---
title: "Ubuntu - GRUB Menu Loaded, Restarts?"
date: 2009-12-14
forum: New to Ubuntu
---

### Post by UnknownFear on 2009-12-14
Hello all. I just went on Ubuntu last night, so it should be working fine. I went boot into it today and it gets to the GRUB2 menu, asks which generic I want. I choose the top one by default, it looks like it's booting up, than it restarts. Does anyone know why this is happening, and how to fix this? I don't want to re-install Ubuntu.

---

### Post by UnknownFear on 2009-12-14
Any help with this? After I select the OS in GUB2, it immediately reboots the computer. I really don't want to have to re-install Ubuntu.

---

### Post by The_Pirate_King on 2009-12-14
Hmmm... you could try booting into the live CD and reinstalling GRUB.

---

### Post by drs305 on 2009-12-14
> **UnknownFear said:**
> Hello all. I just went on Ubuntu last night, so it should be working fine. I went boot into it today and it gets to the GRUB2 menu, asks which generic I want. I choose the top one by default, it looks like it's booting up, than it restarts. Does anyone know why this is happening, and how to fix this? I don't want to re-install Ubuntu.

Do you have another kernel you can try to boot (other than the top one)? Does the same thing happen?

If you press "e" when the top menu item is highlighted do the menu commands look normal (if you know)?

Have you had a kernel or other software updates after your boot last night?

---

### Post by UnknownFear on 2009-12-14
> **drs305 said:**
> 
Have you had a kernel or other software updates after your boot last night?

Yes, I had software updates and I didn't restart when it told me to. Instead I just shut off the computer. I than booted into Vista. Now it won't boot into Ubuntu :(

---

### Post by ajgreeny on 2009-12-14
Try the older kernel, as drs305 suggested.

---

### Post by UnknownFear on 2009-12-14
> **ajgreeny said:**
> Try the older kernel, as drs305 suggested.

The second one worked!!! Still not sure as to why the first one doesn't :S

---

### Post by drs305 on 2009-12-14
Glad you got it fixed while I was writing this post.  :-)

For posterity:

Without more information, I would suspect this isn't a Grub 2 problem but a problem with something that was updated. 

If your computer boots automatically without displaying the menu, you can display the menu by holding down the SHIFT key during the initial boot. 

If an older kernel isn't displayed on the menu (but is still installed on the machine), highlight the Ubuntu selection and press "e" to display the underlying commands. Change the kernel number (-16 for instance) in both the "linux" and "initrd" lines to a lower number and then press CTRL-X to boot.

If the problem was with the kernel, using an older working kernel should solve the problem. If the problem is with other software updates you have to do some more troubleshooting, in which case I would look for recent posts with similar symptoms.

---

### Post by UnknownFear on 2009-12-14
In that case, I'll just use the older kernel when booting to Ubuntu. Still weird, but least it works :D

---

