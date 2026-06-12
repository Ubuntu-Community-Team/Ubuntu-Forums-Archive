---
title: "Running vista from hard drive using KVM"
date: 2008-12-26
forum: New to Ubuntu
---

### Post by slymi2005 on 2008-12-26
I have vista 64bit installed on hard drive and I want to run it using KVM

```
sudo fdisk -l
Disk /dev/sda: 360.0 GB, 360080695296 bytes
255 heads, 63 sectors/track, 43777 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       42508   341445478+   7  HPFS/NTFS
/dev/sda2           42509       43777    10193242+   7  HPFS/NTFS

Disk /dev/sdb: 360.0 GB, 360080695296 bytes
255 heads, 63 sectors/track, 43777 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x501c6aaf

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       24069   193334211    7  HPFS/NTFS
/dev/sdb2           24070       43169   153420750   83  Linux
/dev/sdb3           43170       43777     4883760   82  Linux swap / Solaris

```

I am trying to run /dev/sda1 so i put in
```
kvm -hda /dev/sda1
```

and I get
```
qemu: could not open disk image /dev/sda1

```

I try adding sudo and I get
```
exception 13 (33)
rax 0000000000000000 rbx 000000000000f001 rcx 00000000000079a0 rdx 0000000000006edc
rsi 00000000ffff0001 rdi 000000000008fdc4 rsp 0000000000007bea rbp 0000000000009000
r8  0000000000000000 r9  0000000000000000 r10 0000000000000000 r11 0000000000000000
r12 0000000000000000 r13 0000000000000000 r14 0000000000000000 r15 0000000000000000
rip 0000000000006340 rflags 00033682
cs 09a0 (00009a00/0000ffff p 1 dpl 3 db 0 s 1 type 3 l 0 g 0 avl 0)
ds 52b7 (00052b70/0000ffff p 1 dpl 3 db 0 s 1 type 3 l 0 g 0 avl 0)
es 09a0 (00009a00/0000ffff p 1 dpl 3 db 0 s 1 type 3 l 0 g 0 avl 0)
ss 0000 (00000000/0000ffff p 1 dpl 3 db 0 s 1 type 3 l 0 g 0 avl 0)
fs 0000 (00000000/0000ffff p 1 dpl 3 db 0 s 1 type 3 l 0 g 0 avl 0)
gs 0000 (00000000/0000ffff p 1 dpl 3 db 0 s 1 type 3 l 0 g 0 avl 0)
tr 0000 (fffbd000/00002088 p 1 dpl 0 db 0 s 0 type b l 0 g 0 avl 0)
ldt 0000 (00000000/0000ffff p 1 dpl 0 db 0 s 0 type 2 l 0 g 0 avl 0)
gdt fb1f2/30
idt 0/3ff
cr0 10 cr2 0 cr3 0 cr4 0 cr8 0 efer 0
code: d5 03 42 fd 23 43 d5 03 b0 00 d4 03 b0 04 19 00 50 00 00 00 --> 0f 00 5a fd cf 60 00 00 00 0f 07 06 00 0f 1e 09 19 00 50 00 00 03 03 0f 00 fd 66 fd f2 37
Aborted

```

I am obviously doing something wrong so if anyone could help that would be great.	](*,)

---

### Post by pp. on 2008-12-27
I don't know KVM or qemu. However, from the error message:

> **slymi2005 said:**
> 
```
qemu: could not open disk image /dev/sda1

```

I'd assume:
- qemu expects a file
- you are calling qemu with a disk partition, which is not the same at all.

Further, I'd think you should look into:
- how to invoke KVM or qemu with a partition instead of a file --OR--
- how to prepare a file of the kind expected by qemu (i.e. how to create a virtual machine)

Also, I'd think that your query would fetch more useful responses faster if posted in the Virtualisation forum.

---

