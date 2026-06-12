---
title: "Can't install drivers for internet connection"
date: 2010-01-27
forum: New to Ubuntu
---

### Post by Noob2010 on 2010-01-27
I install Ubuntu correctly but the package that I downloaded to a thumbdrive and then transferred to my ubuntu laptop won't install.
I tried running the Makefile from the terminal but got errors for missing files, I assumed that it probably was dependency files.
I also tried to install it from synaptic with no luck.
It isn't even listed in synaptic and I can't seem to get it in the packages list for Synaptic; if I could do that then I could run the script that would check it for dependencies and then download the files needed to my thumbdrive on my windows pc.

Can anyone help?

I also downloaded ndiswrapper but ran into the exact same install issues.

---

### Post by coolbrook on 2010-01-27
Please provide some detail about your hardware and the driver you're trying to use.

---

### Post by Noob2010 on 2010-01-27
Pentium 3, i386 architecture, the driver is for a netgear wn511b wireless notebook adapter.
The driver is written for linux and is made by the manufacturer of the device - Broadcom.

---

### Post by theozzlives on 2010-01-27
what's the output of lspci?

---

### Post by phillw on 2010-01-27
> **Noob2010 said:**
> Pentium 3, i386 architecture, the driver is for a netgear wn511b wireless notebook adapter.
The driver is written for linux and is made by the manufacturer of the device - Broadcom.

hi and welcome to the forums,

Broadcom wireless & ubuntu are not 'best of friends' because broadcom won't release the code.

It is solvable, but usually requires (from memory) a wrapper.

This is a solved thread --> [http://ubuntuforums.org/showthread.php?t=1288865](http://ubuntuforums.org/showthread.php?t=1288865)

Should point you in the general direction.

Regards,

Phill.

---

