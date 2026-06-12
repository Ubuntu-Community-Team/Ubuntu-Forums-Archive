---
title: "Linux-2.6.25.4 , memory violation at while executing &quot;run_init_process(/sbin/init)&quot;"
date: 2009-07-17
forum: New to Ubuntu
---

### Post by saikiran.veluri on 2009-07-17
We have built the Linux-2.6.25.4 version linux with tool chain scratchbox-toolchain-cs2005q3.2-glibc2.5-arm-1.0.7.2-i386,

Situation:
when we are trying to bring up on our hardware, we are observing that its crashing at the file(fs/binfmt_elf.c) at function(load_elf_binary) while calling the statement padzero(elf_bss)

Other things to know:
we are trying to bring up the file system from the SD card, formated the sd card with ext2 format and copied the file system files into the partition 1.
we also observed that the "elf_bss" should have the proper address for application executables like busybox, but its having some value (0xCA908) which is not a valid address, we are not sure whether the address is a valid address or an offset.

---

