---
title: "Uninstall from WinXP Dual-Boot"
date: 2010-08-13
forum: New to Ubuntu
---

### Post by guitargler on 2010-08-13
I installed Lucid Lynx onto my WinXP eMachine as a dual-boot a while ago, and while I loved it, I sorta did it wrong. I didn't make enough system space, so I can no longer install any applications, and since my webcam doesn't *seem to* work in Ubuntu, I do most of my computing in Windows anyway. I'm finding now, though, that I'm running shy of disk space on my two NTFS hard drives, and a lot of those files are 1) too big for FAT32 and/or 2) not about to be deleted by me. I don't know where my Windows XP disc is, but I've read that it is used to replace the Windows bootloader. How else can I do a complete removal of Ubuntu and get back that HDD space? I appreciate the help, cheers :)

---

### Post by Dustin2128 on 2010-08-13
> **guitargler said:**
> I installed Lucid Lynx onto my WinXP eMachine as a dual-boot a while ago, and while I loved it, I sorta did it wrong. I didn't make enough system space, so I can no longer install any applications, and since my webcam doesn't *seem to* work in Ubuntu, I do most of my computing in Windows anyway. I'm finding now, though, that I'm running shy of disk space on my two NTFS hard drives, and a lot of those files are 1) too big for FAT32 and/or 2) not about to be deleted by me. I don't know where my Windows XP disc is, but I've read that it is used to replace the Windows bootloader. How else can I do a complete removal of Ubuntu and get back that HDD space? I appreciate the help, cheers :)

hm, well if you're short on disk space, you could always shrink your 'buntu partition with.. say.. a knoppix or gparted livecd. As for total removal, do you have it installed on wubi or a full dual boot?

---

### Post by I8NY on 2010-08-13
Well it is a bummer you are going back to windows but i'll still help even though i like ubuntu better.  Well get your Ubuntu live disc, boot onto it, then in the non-installation desktop go to System>Admin>GParted.  This will enable you to edit the partitions, delete the ubuntu parition but _**NOT THE SWAP**_ (this is the boot loader). Shrink the extended partition and then expand the Windows partition.

---

### Post by guitargler on 2010-08-13
It's a full dual-boot install.
Thanks I8NY. I agree, Ubuntu is much better, and I plan to get a netbook which I'll hhave Ubuntu on full-time, hopefully soon. I'll go hunting for that liveCD now, my disc burner's gone to crap.. And again, thanks for the help. Hopefully I'll be back soonish, but with ubuntu and the ability to help other people in the full spirit of open-source goodness. (Still using Linux BTW, I have an Android phone. The original Android phone.)

---

### Post by a2020vision on 2010-08-13
A couple options. You could do like the others said, and shrink your Ubuntu partitions (incidentally, idk about I8NY's settings, but *my* bootloader's on my actual Ubuntu partitions, *not* the swap partition).

Or, you could borrow/"acquire" another XP disc for the purpose of reinstalling the bootloader (if you need help with that, ask; it's easy, but only if you already know how to do it).

---

### Post by I8NY on 2010-08-13
well the boot loader might be on the ubuntu partition so maybe don't delete it for the safety, just shrink it. Reinstalling the windows boot loader it the best option for a long term solution. You can use Unetbootin to burn a ISO to a thumb drive.

---

### Post by guitargler on 2010-08-13
> **a2020vision said:**
> A couple options. You could do like the others said, and shrink your Ubuntu partitions (incidentally, idk about I8NY's settings, but *my* bootloader's on my actual Ubuntu partitions, *not* the swap partition).

Or, you could borrow/"acquire" another XP disc for the purpose of reinstalling the bootloader (if you need help with that, ask; it's easy, but only if you already know how to do it).

I have seen several tutorials that include instructions on how to restore the XP bootloader, I might look into that. And yeah, "acquisition" of an XP disc shouldn't be too hard, hehehe *cough*.

And I really wish my computer was not t3h suck, but my BIOS doesn't support thumb-drive booting (my flash drive is already bootable with Lucid on it).

---

