---
title: "PXE configuration"
date: 2016-07-09
forum: Networking &amp; Wireless
---

### Post by timonoj on 2016-07-09
Hi guys,

I'd like to setup a PXE boot of the Ubuntu full installer. This is mainly for learning, as I intend a more extended menu later on with different possibilities. I configured successfully on my NAS DHCP-boot and TFTP, and PXE seems to even show the grub menu of Ubuntu I set, but seems I made some mistakes and nothing happens when I choose to start. Could you guide me through so I understand which file should I point from the default file to start linux? Thanks!

My default file:
> 
DEFAULT vesamenu.c32
TIMEOUT 100
PROMPT 0
MENU INCLUDE pxelinux.cfg/PXE.conf
NOESCAPE 1
LABEL Try Kubuntu 16.04 Desktop
MENU LABEL Try Kubuntu 16.04 Desktop
kernel Ubuntu/vmlinuz
append boot=casper netboot=nfs nfsroot=192.168.0.10:/tftpboot/kubuntu/
initrd=Ubuntu/initrd.lz quiet splash
ENDTEXT
LABEL Install Ubuntu 14.04 Desktop

---

### Post by him610 on 2016-07-09
Personally, I have never had a reason to PXE boot, so that means I can not offer any advice except a link that may help you...
[https://help.ubuntu.com/community/DisklessUbuntuHowto]("https://help.ubuntu.com/community/DisklessUbuntuHowto")

---

