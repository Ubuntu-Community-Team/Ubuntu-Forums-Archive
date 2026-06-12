---
title: "Fixing GRUB Bootloader"
date: 2010-05-28
forum: New to Ubuntu
---

### Post by xRedx22 on 2010-05-28
I'm sure a lot of people have already asked how to fix a Ubuntu install, but I somehow seem to have messed it up really bad.

I was trying to dual-boot Ubuntu 9.04 with Windows XP SP3 on my computer, and since I 
did not have a disk, I used UNetBootin to install the Ubuntu .iso onto my hard drive.
After trying to install multiple times, and then finally getting it to install, I rebooted my system. Now whenever I boot up I get the following on GRUB:

Ubuntu 9.04, memtest86+
Other operating systems:
Windows Vista (loader)

I then ran the Windows Vista loader, and wiped all my system files on the XP partition.

I tried reinstalling Ubuntu from a live USB drive, but that didn't seem to help.
All I really would like to do now is to access my Ubuntu install. Any ideas?

---

### Post by cariboo on 2010-05-28
Have you run update-grub in a terminal?

```
sudo update-grub
```

---

### Post by kansasnoob on 2010-05-28
If you have the ability to run either a Live CD or Live USB please post the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by xRedx22 on 2010-05-28
I attached the file that boot_info_script gave me.
And when updating GRUB I get:

```

Searching for GRUB installation directory ... 
No GRUB directory found. To create a template run 'mkdir /boot/grub' first. To install grub, install it manually or try the 'grub-install' command. ### Warning, grub-install is used to change your MBR. ###

```

---

### Post by xRedx22 on 2010-05-28
Does anyone else have any ideas on how to fix this?

---

### Post by kansasnoob on 2010-05-28
Just looking now, be patient :)

---

### Post by kansasnoob on 2010-05-28
For reference you can look here:

[http://ubuntuforums.org/showpost.php?p=9338226&postcount=41](http://ubuntuforums.org/showpost.php?p=9338226&postcount=41)

But, if you can run a Live USB or CD go to terminal and copy-n-paste the following commands:

```
sudo mount /dev/sda5 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo chroot /mnt
```

```
grub
```

```
root (hd0,4)
```

```
setup (hd0)
```

```
quit
```

```
exit
```

```
sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt
```

Hopefully that's it.

---

### Post by xRedx22 on 2010-05-28
Thank you! I'll try that.

Oh, and sorry about being kind of impatient, I sometimes do that. :oops:
I will tell you if it worked later.

---

### Post by kansasnoob on 2010-05-28
> sorry about being kind of impatient

No sweat, I can be a grouchy old man sometimes, we're all human :)

---

### Post by xRedx22 on 2010-05-28
It worked!

Again, thank you, because I was starting to get really annoyed after re-booting trying so many different things.

---

