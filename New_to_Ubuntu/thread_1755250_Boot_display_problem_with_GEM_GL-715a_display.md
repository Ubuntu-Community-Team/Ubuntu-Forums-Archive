---
title: "Boot display problem with GEM GL-715a display"
date: 2011-05-11
forum: New to Ubuntu
---

### Post by mla12 on 2011-05-11
Installed Ubuntu 11.04 64-bit. I can reach the grub2 prompt. After selecting a kernel, however, the display begins to flash and is completely unusable.

I have Win7 installed on the same machine and can boot into it fine.

The motherboard is a Gigabyte MA785GM-US2H with integrated video. I've tried disabling the on-board video and using an old PCI video card. Same problem.

I've tried booting with every kernel parameter I could find to bypass gdm and X. Tried the "rescue" kernel. No luck. It seems like something is switching/resetting the display very early in the boot process that is screwing it up.

Tried using the live CD to boot. Same problem.

Tried disabling every optional feature I could find in bios. No improvement.

I *can* use the monitor successfully on an old machine running CentOS 4.9.

I also tried Ubuntu 10.04 on the same machine with the same result.

Any ideas?

Thanks.

---

