---
title: "GRUB2: chainload to other MBR"
date: 2015-12-01
forum: Networking &amp; Wireless
---

### Post by ultradj83 on 2015-12-01
Dears,    I have grub2 installed in the MBR record on sdb.
  I need to add a entry to chainload to an other bootloader in MBR on sda.
  Is this possible?
  Thanks and best regards.

---

### Post by oldfred on 2015-12-01
I have not done it for ages, I also like seperator line & reboot:
Note boot drive is always hd0, so if booting sdb, then sda will be hd1. But if booting sda, then that is hd0. Depending on default drive order can be confusing. And my order changed when I plug in a flash drive which became sdb, as I then booted from sdc, so most of my drives changed.

```
 menuentry "Lucid Lynx on sda (When from sdc) Chainboot" {
set root=(hd1)
chainloader +1
}
      
 # spacer line
menuentry " " {
set root= 
}

menuentry "System restart" {
  echo "System rebooting..."
  insmod reboot
  reboot
  }    
  
menuentry "System shutdown" {
  echo "System shutting down..."
  insmod halt
  halt
  }
    

```

But with grub2 you normally directly boot another install. And to avoid the issue of other install kernel updates you boot the kernel link in / not the kernel directly.

      ```
 menuentry "Daily on sda13" {
    set root=(hd0,13)
        linux /vmlinuz root=/dev/sda13 ro quiet splash
        initrd /initrd.img
}


```

More info:
       How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)

---

### Post by ultradj83 on 2015-12-02
Perfect.

Thank you so much.

---

