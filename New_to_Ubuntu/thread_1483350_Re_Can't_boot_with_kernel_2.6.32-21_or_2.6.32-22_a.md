---
title: "Re: Can't boot with kernel 2.6.32-21 or 2.6.32-22 after upgrade to Lucid"
date: 2010-05-14
forum: New to Ubuntu
---

### Post by SalahTr on 2010-05-14
Hi,
The output of 
```
lspci | grep VGA
```
is 
```
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
```
and the ouptput of 
```
ls /boot
```
is
```
abi-2.6.31-14-generic
abi-2.6.31-17-generic
abi-2.6.31-19-generic
abi-2.6.31-20-generic
abi-2.6.31-21-generic
abi-2.6.32-22-generic
config-2.6.31-14-generic
config-2.6.31-17-generic
config-2.6.31-19-generic
config-2.6.31-20-generic
config-2.6.31-21-generic
config-2.6.32-22-generic
grub
initrd.img-2.6.31-14-generic
initrd.img-2.6.31-17-generic
initrd.img-2.6.31-19-generic
initrd.img-2.6.31-20-generic
initrd.img-2.6.31-21-generic
initrd.img-2.6.32-22-generic
memtest86+.bin
System.map-2.6.31-14-generic
System.map-2.6.31-17-generic
System.map-2.6.31-19-generic
System.map-2.6.31-20-generic
System.map-2.6.31-21-generic
System.map-2.6.32-22-generic
vmcoreinfo-2.6.31-14-generic
vmcoreinfo-2.6.31-17-generic
vmcoreinfo-2.6.31-19-generic
vmcoreinfo-2.6.31-20-generic
vmcoreinfo-2.6.31-21-generic
vmcoreinfo-2.6.32-22-generic
vmlinuz-2.6.31-14-generic
vmlinuz-2.6.31-17-generic
vmlinuz-2.6.31-19-generic
vmlinuz-2.6.31-20-generic
vmlinuz-2.6.31-21-generic
vmlinuz-2.6.32-22-generic
```
Should I use instructions on [https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes]("https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes") :?:

---

