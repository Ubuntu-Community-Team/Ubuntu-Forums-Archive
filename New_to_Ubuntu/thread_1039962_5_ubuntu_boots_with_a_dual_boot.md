---
title: "5 ubuntu boots with a dual boot"
date: 2009-01-15
forum: New to Ubuntu
---

### Post by BurnChao on 2009-01-15
Hi. I'm new to Ubuntu. I installed Intrepid onto a partition, with a separate swap partition. (XP was installed first, Ubuntu added second (I don't know if any of this is relevant, but seems like I could be asked)

Anyways, at the GRUB loader, when choosing which OS to boot, I'm presented with 5 different booting options for Ubuntu, and one for XP. This seems off.

There's 2 different kernels, each with a safe mode, and the final one is a mem-test.

I did I mess up the installation, double installing or something? or is there really supposed to be 5 different ubuntu options? If not, how do I get rid of the extra kernel? (or should I just reformat the drive, and reinstall?)

Related: How can I add safe mode for XP into GRUB loader options?
Also related: Ideally, I'd like to be presented with just three options: Ubuntu, XP, and [MORE]. Under the [MORE] option I'd see the other safe modes and mem-tests options. I've found instructions on editing the GRUB loader to change default boot. Seems like I could be able to edit GRUB to this behaviour (though it also seems like I could make my drive unbootable if I don't do it right).

Thanks in advance for any help that can be provided.

---

### Post by king EZi on 2009-01-15
the 5 modes you see are different Kernels, normally (after fresh install) you'd have 2 plus memtest one in normal boot and another in safe mode but after updating a kernel it gets added to the /boot/grub/menu.lst file which is the displayed on the grub menu....by default Ubuntu will boot to the first Kernel (your latest version/ updated kernel).
Bottom line is you did nothing wrong so no need to blame yourself.:lolflag: 

Now for windoze safe mode...boot to windows and press F8.

Hope that explains it.

---

### Post by BurnChao on 2009-01-15
> **king EZi said:**
> the 5 modes you see are different Kernels, normally (after fresh install) you'd have 2 plus memtest one in normal boot and another in safe mode but after updating a kernel it gets added to the /boot/grub/menu.lst file which is the displayed on the grub menu

Well, this is a fresh install off of a CD I downloaded less than a week ago. I don't think anything newer has come out since then, and even if so, I don't know enough linux to have updated a kernel knowingly.  Does this happen automatically? and if so, it sounds like I'll soon have a boot list a mile long, with a hundred different ubuntu options. That sounds real sucky.

Can I have loader just present me with just Unbuntu, XP, and [MORE]? I really don't need all that clutter, and since that clutter grows (I have know idea how fast), and since I'll skim across all of it daily (the ubunutu kernel I'll want will always be at the top, and XP will be at the bottom).

---

### Post by mcduck on 2009-01-15
If you want to get rid of the extra kernels, just use the Synaptic package manager to uninstall the old versions and they will be automatically removed from the boot menu.

(Yes, every program and every part of the OS is updated automatically. When the kernel is updated it doesn't replace the old one, so you can test the new kernel to confirm it works correctly on your machine and if it doesn't, you still have the old kernel available to make sure you'll always be able to use your computer. When you are sure the new version works fine for you, just uninstall the old one.)

---

### Post by BurnChao on 2009-01-15
Right on. I did find that in the package manager. I didn't know if removing the older kernel version would kill everything.

Thanks all for the help. The information provided is useful and appreciated.

---

### Post by zvacet on 2009-01-15
> I didn't know if removing the older kernel version would kill everything

It will not,but make sure that latest kernel is working correct before you remove older one.I think it is good to have two kernels,just in case if something goes wrong.

---

### Post by king EZi on 2009-01-15
> **zvacet said:**
> It will not,but make sure that latest kernel is working correct before you remove older one.I think it is good to have two kernels,just in case if something goes wrong.

Yeah, make sure the "newer" kernel work ok with your machine THEN maybe you can remove it if you want...take your time though, maybe a week of testing. ):P 
Enjoy your Ubuntu.

---

