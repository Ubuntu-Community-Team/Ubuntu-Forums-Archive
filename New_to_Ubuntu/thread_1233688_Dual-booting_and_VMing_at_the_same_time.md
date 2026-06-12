---
title: "Dual-booting and VMing at the same time?"
date: 2009-08-07
forum: New to Ubuntu
---

### Post by InfectedWithDrew on 2009-08-07
I'm looking to set up a dual-boot with Windows 7 and Ubuntu.  I'd like to be able to boot either system and use all 6GB of my RAM (yes, be jealous ;)), or, if I want to have both at the same time, boot one and then put the other in a VM.

However, at the same time, I kind of want to be able to use the same partition for my various /home folders (using symlinks) as I have my remapped My Documents and such folders.  See, I put My Documents etc. (Windows) on a 500GB drive, and I want Documents etc. (Ubuntu) to draw from the same source, so I have a more seamless dual-boot.

This presents a problem.  Can I actually do this (I mean, doesn't it cause problems when a VM touches the same disk as the host OS)?  And if I can't, what should I do?  I've thought about using 64-bit Windows booting a VM of 32-bit Ubuntu (since I'd rather not deal with 64-bit if I'm only going to use it as a VM), but then, even in the VM, I wouldn't get a very seamless integration.

So, can I VM when I have a system that's set up like that, where I'm touching the same partition with both the host and the VM?  And, if not, what should I do?  Dual-boot or VM?

---

### Post by 123456789123456789123456 on 2009-08-07
To run both systems from the same physical disk, at the same time, It is not done, because the processing power, and the hardware technology does not exist for regular home based computers.  You can set up Ubuntu to access the windows My Documents folder, and use the data from it.  Since windows 7 and vista use NTFS file systems, and Ubuntu can read/write to NTFS now without data limitations, it should be possible.  The bad thing about using VM programs to run the other OS, it slows down the system
you are using the same ram, true, but it also requires more processing power, does not make a difference rather the host OS is 64 or 32 bit, the problem is with the processor, for instance, if you have a dual core processor, the VM machine is using both cores, and the main host OS is using both cores,
causing a system slow down.  Another problem is that when using a virtual machine, you will not be able to set Ubuntu to use the windows My documents folder as the location for Documents.  It can not access that disk space, since any folders you have it use, will be basically treated as seperate hard drives.  + your intergration is now controled, and limited by the virtual machine software being used.  Your best bet is Dual boot, even if you can't boot both at the same time.  You will run into the following problems, where Ubuntu will be able to read and access the windows files, and folders, Windows will be unable to read the files and folders of Ubuntu.  It may not therefore be wise to have Ubuntu have the documents folder set to the same path as My Documents.  However if you wanted to you can save ubuntu files in that location if you like, and you can even tell windows to move My Documets to antoher disk, or disk partition.
hope this helps.

---

### Post by InfectedWithDrew on 2009-08-07
> **123456789123456789123456 said:**
> To run both systems from the same physical disk, at the same time, It is not done, because the processing power, and the hardware technology does not exist for regular home based computers.  You can set up Ubuntu to access the windows My Documents folder, and use the data from it.  Since windows 7 and vista use NTFS file systems, and Ubuntu can read/write to NTFS now without data limitations, it should be possible.  The bad thing about using VM programs to run the other OS, it slows down the system
you are using the same ram, true, but it also requires more processing power, does not make a difference rather the host OS is 64 or 32 bit, the problem is with the processor, for instance, if you have a dual core processor, the VM machine is using both cores, and the main host OS is using both cores,
causing a system slow down.  Another problem is that when using a virtual machine, you will not be able to set Ubuntu to use the windows My documents folder as the location for Documents.  It can not access that disk space, since any folders you have it use, will be basically treated as seperate hard drives.  + your intergration is now controled, and limited by the virtual machine software being used.  Your best bet is Dual boot, even if you can't boot both at the same time.  You will run into the following problems, where Ubuntu will be able to read and access the windows files, and folders, Windows will be unable to read the files and folders of Ubuntu.  It may not therefore be wise to have Ubuntu have the documents folder set to the same path as My Documents.  However if you wanted to you can save ubuntu files in that location if you like, and you can even tell windows to move My Documets to antoher disk, or disk partition.
hope this helps.
I have a quad-core (AMD Phenom II X4, it's a beast) so processing power is NOT a problem for me.

But I really didn't understand what you said about the VM and the host touching the same disk.  Can you word it differently?  I'm just not catching on.

---

