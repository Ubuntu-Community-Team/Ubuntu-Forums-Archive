---
title: "No bootable devices, dual boot"
date: 2010-04-09
forum: New to Ubuntu
---

### Post by Saraslife on 2010-04-09
I have dual boot ubuntu 9.10 and windows 7. recently after windows updated something, once I shut down windows and then start my computer I get no bootable devices. So I looked around the forums and found that when I booted from ubuntu cd and ran terminal and entered:

sudo mkdir /media/sda5
sudo mount /dev/sda5 media/sda5
sudo grub-install --root-directory=media/sda5 /dev/sda

and restart my computer, everything works fine. but when i load windows 7 and turn it off then on again i get no bootable devices again. Is there a permanent fix? please tell me there is.

thanks.

---

### Post by byStanderone on 2010-04-09
...would assume that you have your karmic installed in sda5 partition, boot from your live cd and try:

boot from your karmic live cd...

mount your karmic: mount /dev/sda5 /mnt

then: grub-install --root-directory=/mnt /dev/sda 
                  (note: sda without 5)

then unmount the partition: umount /mnt

-REBOOT

---

### Post by Saraslife on 2010-04-09
ubuntu@ubuntu:~$ sudo mount /dev/sda5 /mnt
ubuntu@ubuntu:~$ grub-install --root-directory=/mnt /dev/sda 
rm: cannot remove `/mnt/boot/grub/915resolution.mod': Permission denied

---

### Post by byStanderone on 2010-04-09
> **Saraslife said:**
> ubuntu@ubuntu:~$ sudo mount /dev/sda5 /mnt
ubuntu@ubuntu:~$ grub-install --root-directory=/mnt /dev/sda 
rm: cannot remove `/mnt/boot/grub/915resolution.mod': Permission denied


sorry, am at a lost here, would do a search on the last two lines...

---

### Post by yetiman64 on 2010-04-09
@Standerone, Maybe if the second command (grub-install) was preceded by "sudo", grubs attempt at removing the file "915resolution.mod" would succeed, as it was originally mounted by root (with the first command being run with sudo.) 

eg. instead of;

> ubuntu@ubuntu:~$ sudo mount /dev/sda5 /mnt
ubuntu@ubuntu:~$ grub-install --root-directory=/mnt /dev/sda 
rm: cannot remove `/mnt/boot/grub/915resolution.mod': Permission deniedtry

```
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda 
```also the last of the original instructions you gave

> then unmount the partition: umount /mnt

-REBOOT           should also be run with "sudo"
eg.
```
sudo umount /mnt
sudo reboot
```edit: rather than rebooting from the terminal maybe Saraslife may want to use the "normal" means - if so ignore the "sudo reboot" command above.

Note the "user" is ubuntu@ubuntu. It is possible to get a terminal on a live cd to show as root@ubuntu with "sudo su root" (maybe even with "sudo su", though I haven't tried that one.)

@Saraslife, Although I haven't tried out Standerone's instructions myself before, they appear to make sense. Though to use them would require you to preface all commands with sudo (which is missing in your original error quoted).

Hope this works for you.

---

### Post by oldfred on 2010-04-09
This may be windows software writing into the MBR.

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR)
[http://www.supergrubdisk.org/wiki/WindowsErasesGrub](http://www.supergrubdisk.org/wiki/WindowsErasesGrub)
HP ProtectTools, Dell Recovery, and a few others write into MBR 
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941)
[https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/441941?comments=all](https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/441941?comments=all)
Dell Media direct issues with MBR
[http://ubuntuforums.org/showthread.php?t=923576](http://ubuntuforums.org/showthread.php?t=923576)

---

### Post by byStanderone on 2010-04-09
...yes oldfred it really seems so, suspected that from the start, tho clearing our own backyard comes first in line. got one from you again, thanks.

---

