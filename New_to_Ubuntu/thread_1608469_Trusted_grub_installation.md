---
title: "Trusted grub installation"
date: 2010-10-29
forum: New to Ubuntu
---

### Post by sajnanazeer on 2010-10-29
Hi,Where can I find Trusted grub source for Ubuntu? How can I install it?

---

### Post by Hippytaff on 2010-10-29
Grub2 is already installed with ubuntu. Do you want to uninstall and reinstall it?

---

### Post by sajnanazeer on 2010-11-01
Hi,I have to install TrustedGrub1.1.5. I have downloaded the source from [http://sourceforge.net/projects/trustedgrub/files/TrustedGRUB-1.1.5/TrustedGRUB-1.1.5.tar.gz/download](http://sourceforge.net/projects/trustedgrub/files/TrustedGRUB-1.1.5/TrustedGRUB-1.1.5.tar.gz/download) . I have installed it. But the booting stops at stage2(leaves in the grub prompt). It could not find the kernel image. I think it looks for menu.lst file in /boot/grub. But it is not present there. I have created my own menu.lst and then it worked. How can I automate the creation of menu.lst? In ubuntu menu.lst is not there. Which file it takes instead of menu.lst?

---

### Post by Elfy on 2010-11-01
You would have to remove grub2 and install grub legacy to get a menu.lst automated. Grub2 has been default in new installs for a couple of versions now.

Not completely sure what trusted grub is - never heard of it myself.

---

### Post by sajnanazeer on 2010-11-01
Hi,
You can find information about trusted grub at [http://www.sirrix.com/content/pages/trustedgrub.htmI]("http://www.sirrix.com/content/pages/trustedgrub.htm"). I was using ubuntu 10.04. Since it has grub2, it uses grub.cfg instead of menu.lst. But trusted grub searches for the menu.lst and it does not find. So it stops at stage2 of booting since it could not find information about kernel. I have tried with grub.cfg instead of menu.lst, but trusted grub doesnot understands the format of grub.cfg. Then I manually created a menu.lst file and then it booted correctly. Now, I wanted to know that is there any way to make kernel to generate menu.lst? Is there any trusted grub versions that is compatible with the os that supports grub2?

---

### Post by Elfy on 2010-11-01
As I said as far as I am aware you'd need to remove grub2 and use grub legacy.

Maybe contact them about trusted grub and grub2.

---

### Post by kiraven on 2011-06-14
I am using trustedgrub with Maveric. forestpiskie is right: At first, you have to remove Grub2 and install Grub Legacy via the Package Management (e.g. Synaptic). Afterwards, you can simply follow Trusted Grub’s Readme.

---

### Post by FormatSeize on 2011-06-14
Out of curiosity, what are the reasons behind using Trusted Grub?

---

### Post by rsteele on 2011-06-23
> **FormatSeize said:**
> Out of curiosity, what are the reasons behind using Trusted Grub?

Trusted Grub is needed if you want to use your computer's TPM (Trusted Platform Module, google it). It's all security stuff.  Trusted Grub will store check sums of various pieces of the kernel into the TPM module.  These checksums can be recalculated as the system is running to verify that things like key loggers haven't been installed.  Or, if you are doing remote attestation the sums are stored on a remote server and verified as being unchanged when access to that server is required.

I've been working all day trying to get TG to boot, so far with zero luck.  It's based on a Grub version that's a couple of years old and Ubuntu really doesn't seem to like it. I'll give the suggestions above a try...

---

### Post by Varsel on 2012-05-20
> **Elfy said:**
> You would have to remove grub2 and install grub legacy to get a menu.lst automated. Grub2 has been default in new installs for a couple of versions now.

Not completely sure what trusted grub is - never heard of it myself.

Not sure if sajnanazeer would be interested in this or not, but could you give a brief rundown on how to "remove grub2 and install grub legacy" in its place?

---

