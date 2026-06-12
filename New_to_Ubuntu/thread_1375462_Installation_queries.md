---
title: "Installation queries"
date: 2010-01-07
forum: New to Ubuntu
---

### Post by hungryOrb on 2010-01-07
Hi all,
Have a query, it's really about GRUB.
My friend just installed UBU on a USB spare HD that he had (only place with space). And I'm just wondering, if GRUB can be used what will happen? Will GRUB install on the spare? If so, that means if the USB is unplugged, then the motherboard will just request the old boot right? And boot windows? if he wants to actually boot UBU from spare, then he's gotta set the motherboard to boot the USB as primary right? and if he wants windows just restart (with windows as secondary boot) and make sure the spare is unplugged.. 
Is that right?
Hope so...
Really don't want his first experience to be bad :(
If any help or suggestion or info, would be FANTASTIC :D
Thanks!

---

### Post by theozzlives on 2010-01-07
I installed a full install on a Flash Drive. I disconnected the HD so GRUB would only go on the USB. When I boot to it, I just select USB as my boot device. That should work in your friend's case.

---

### Post by hungryOrb on 2010-01-07
Thanks man,
My friend didn't DC the main HD, and it seems GRUB is installed on the main HD. And he has an error when attempting to load VISTA even with the spare turned off. Is there a way to quickly reinstate the windows boot? Or better still, to make GRUB use windows boot properly?

---

### Post by hungryOrb on 2010-01-07
The error when trying to access the windows partition is:

grub-probe: error: cannot find a device for /.

---

