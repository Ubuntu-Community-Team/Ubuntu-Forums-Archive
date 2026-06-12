---
title: "grub update problem"
date: 2011-03-25
forum: New to Ubuntu
---

### Post by msneo101 on 2011-03-25
i want to change Splash screen using grub....
i made some changes and when i try to update grub i found this  
  \problem..PLz help me!!!!!!

Generating grub.cfg ...
cat: /boot/grub/video.lst: No such file or directory
Found linux image: /boot/vmlinuz-2.6.35-28-generic
Found initrd image: /boot/initrd.img-2.6.35-28-generic
Found linux image: /boot/vmlinuz-2.6.32-29-generic
Found initrd image: /boot/initrd.img-2.6.32-29-generic
Found linux image: /boot/vmlinuz-2.6.32-28-generic
Found initrd image: /boot/initrd.img-2.6.32-28-generic
Found Windows 7 (loader) on /dev/sdb1
/etc/grub.d/40_custom: 1: BEGIN: not found
/etc/grub.d/40_custom: 2: menuentry: not found
insmod: can't read 'part_msdos': No such file or directory
insmod: can't read 'ntfs': No such file or directory
/etc/grub.d/40_custom: 6: search: not found
/etc/grub.d/40_custom: 7: loopback: not found
/etc/grub.d/40_custom: 8: Syntax error: "(" unexpected

---

### Post by Dutch70 on 2011-03-25
Hi & welcome to UF

Please run the following command in a terminal. Copy & paste the contents from Gedit into your next post. 
Be sure to put it between ```
 tags with the "#" symbol in the toolbar.

[CODE]sudo gedit /boot/grub/grub.cfg
```

Anyone that can help you will need that info, possibly even your boot info script. Can you still boot into Ubuntu?

On 2nd thought, you may just want to reinstall Grub2 from the live cd/usb and then use Grub Customizer.
[[COLOR="RoyalBlue"]Reinstalling Grub2 from Live CD[/COLOR]]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")

Here is a good program & tutorial if you want to customize your grub menu. Thanks to drs305 for the tutorial.
[[COLOR="RoyalBlue"]HOWTO Grub Customizer[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1664134")

---

