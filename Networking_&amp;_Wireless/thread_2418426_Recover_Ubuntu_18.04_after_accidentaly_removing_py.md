---
title: "Recover Ubuntu 18.04 after accidentaly removing python3"
date: 2019-05-06
forum: Networking &amp; Wireless
---

### Post by larryskywalker on 2019-05-06
Ok so I am an old geezer and thought Ubuntu (18.04.2 LTS) didn't need  python, at least not python3. Big mistake, after I removed python3,  nothing works anymore. I could recover it by reinstalling everything  again, especially, in /var/log/apt/history.log I can find everything that was removed.


  However, my network does not work anymore (why would need python3 for having a working network...). 

  
So my question is, how do I recover my network without python3 and without the ability to install anything?

  I have tried to reconfigure /etc/network/interfaces with a static IP address, but this does not seem to get picked up. Rebooting and my interface is still not configured.

  
Any idea?

---

### Post by oldfred on 2019-05-06
You may be able to chroot into your install and then update it.
Or you can do a "dirty" install where you do not reformat the partition. Any system files you edited will be reset to defaults, but all your other data should not get changed.

 chroot with UEFI, LVM, encryption on NVMe drive
[https://ubuntuforums.org/showthread.php?t=2349833&p=13602088#post13602088](https://ubuntuforums.org/showthread.php?t=2349833&p=13602088#post13602088)
UEFI chroot
[http://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380](http://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380)
To chroot, you need the same 32bit or 64 bit kernel. Best to use same version.

this is older and for BIOS, you have to add efi partition if UEFI.
kansasnoob- full chroot one line version with &&---- change sda3 to your install
[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)
[http://ubuntuforums.org/showthread.php?t=1470597](http://ubuntuforums.org/showthread.php?t=1470597)

Over install without formatting to reuse same home data. "Dirty Install"
System settings or anything in / may be overwritten with defaults. Good backups still important
[https://help.ubuntu.com/community/UbuntuReinstallation](https://help.ubuntu.com/community/UbuntuReinstallation)
[http://ubuntuforums.org/showthread.php?t=1941872](http://ubuntuforums.org/showthread.php?t=1941872)

---

