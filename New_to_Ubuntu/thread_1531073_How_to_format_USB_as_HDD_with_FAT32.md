---
title: "How to format USB as HDD with FAT32"
date: 2010-07-14
forum: New to Ubuntu
---

### Post by boki15 on 2010-07-14
Hello to all,

i wrote a script for myself which creates MultiBootUSB with grub2 in mbr and syslinux in pbr. 

I format with following command:
```
sudo mkfs.vfat -n ${VOLUME} ${DEVICE}1
```and in my *.cfg I boot win with following entry (grub2):
```
# (0) Windows 7 x86/64. Chainloading Win 7 second stage bootloader (PBRMETHOD)
menuentry "00. Windows 7 Installation x86/64" {
insmod fat
set root=(hd0)
chainloader (hd0,1)/bootmgr.pbr +1
boot
}
```Syslinux is also not booting with following command:
```
# (3) Syslinux boot with second stage bootloader. Syslinux must be installed to pbr.
menuentry "03. Syslinux via chainloading" {
 insmod fat
 set root="(hd0,1)"
 chainloader +1
}
```Grub1 also not:
```
# (1) Grub PBR. Chainloading Grub second stage bootloader (PBRMETHOD)
menuentry "01. Grub via PBR (second stage bootloader)" {
 insmod fat
 set root=(hd0)
 chainloader (hd0,1)/grldr.pbr +1
}
```But if I just format it with BOOTICE or other format tool from Win, everything woks!

I couldnt find out how to format it right. I tried install with dd NT6 mbr and pbr but it didnt work too.

How can I format from terminal to get it work like if I format it from win. I just dont want to use win for that, the script works also from LiveCD (just needs "sudo apt-get install -f")

Please help someone :)

---

