---
title: "How to add ubuntu (install inside windows) in fedora grub?"
date: 2011-09-06
forum: New to Ubuntu
---

### Post by kiranmatrixlee on 2011-09-06
i have 3 os(windows7,ubuntu 11.04,fedora).ubuntu install inside windows.fedora's boot loader is currently working.i need to add ubuntu in ferodra's grub menu.


fedora grub file


```


    default=0
    timeout=15
    splashimage=(hd0,8)/boot/grub/splash.xpm.gz
    hiddenmenu
    title Fedora (2.6.38.6-26.rc1.fc15.i686.PAE)
    root (hd0,8)
    kernel /boot/vmlinuz-2.6.38.6-26.rc1.fc15.i686.PAE ro root=UUID=1f745484-544a-4249-8d9f-dcd103ccf545 rd_NO_LUKS rd_NO_LVM rd_NO_MD rd_NO_DM LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYTABLE=us rhgb quiet
    initrd /boot/initramfs-2.6.38.6-26.rc1.fc15.i686.PAE.img
    title Other
    rootnoverify (hd0,0)
    chainloader +1
```

ubuntu grub file(only ubuntu's entry specified below)


```


     menuentry "Ubuntu, Linux 2.6.38-8-generic" {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root 6E8283B482837F79
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=6E8283B482837F79 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.38-8-generic
    }
```I need ubuntu in fedora grub menu.The problem is difference in grub version.

---

### Post by oldfred on 2011-09-06
There is no loop command in grub legacy unless someone added it. So I do not think you can easily convert the grub2 boot stanza.

You can boot with grub2 and even without Windows.
Posts by meierfra. to use grub2 to directly boot wubi
[http://ubuntuforums.org/showthread.php?p=8903013](http://ubuntuforums.org/showthread.php?p=8903013)

Fedora's new Alpha supposedly uses grub2. Have they offered a grub2 update for the current version?

---

