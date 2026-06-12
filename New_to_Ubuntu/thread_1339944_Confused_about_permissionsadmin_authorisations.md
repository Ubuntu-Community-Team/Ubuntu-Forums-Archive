---
title: "Confused about permissions/admin authorisations"
date: 2009-11-28
forum: New to Ubuntu
---

### Post by Leonasha on 2009-11-28
Hi folks,

I have been meaning to replace my old hard drive with a newer, bigger, faster one, and ideally I would like to just tar my entire OS and untar it on the new drive. Not sure if that's how it's done ... but the problem is that when I try to compress the content of my old hd (using the right-mouse menu) I get the message "Error adding that file to the archive - permission denied". I have fiddled around with the policykit doohickey to no avail, and now it is set back to default permissions. It just irks me that I don't have full permissions on my own computer! How can I make my computer do my bidding?

Thanks!

---

### Post by 3rdalbum on 2009-11-28
1. Your ordinary user account doesn't have full ownership over your operating system. This is part of the Linux security design. Only the "root" user has ownership and full permissions over the system, so you would need to temporarily switch to root by using "sudo" or "gksudo" before the command or program.

Not to sound harsh, but this is the way the entire Linux system is built to work, for various good reasons; you'll need to get used to this, because it's not going to change.

2. There are better ways to do what you want to do. I'd advise using Clonezilla to make the hard disk image, rather than just 'tar' up your hard disk. Clonezilla is designed for exactly what you want to do.

---

### Post by Leonasha on 2009-11-28
thanks - I'll try Clonezilla.

---

### Post by Leonasha on 2009-11-30
> **3rdalbum said:**
> 

2. There are better ways to do what you want to do. I'd advise using Clonezilla to make the hard disk image, rather than just 'tar' up your hard disk. Clonezilla is designed for exactly what you want to do.

I have downloaded Clonezilla and am trying to make a bootable live usb of it according to [these directions](http://clonezilla.org/clonezilla-live/liveusb.php) ... but when I get to the point of entering "bash makeboot.sh /dev/sdb1" (using the actual name of my usb, of course), the result is "no such file or directory". Am I doing something wrong?

---

### Post by nothingspecial on 2009-12-01
If it can`t find /dev/sdb1 then you are not using the correct device lable. Post the output of ```
sudo fdisk -l
```

---

### Post by Leonasha on 2009-12-01
ok here it is ... but as I said above, I do know the name of my disk, entered it and still got that result.

Anyway here is the code concerning my usb key.

```
Disk /dev/sdc: 1000 MB, 1000341504 bytes
16 heads, 32 sectors/track, 3816 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x5529bbd1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        3816      976880    e  W95 FAT16 (LBA)


```

I tried entering both "bash makeboot.sh /dev/sdc" and ".../sdc1" and got the result "no such file or directory".

---

### Post by Leonasha on 2009-12-02
anyhow, I am going to wipe the flash drive and try again ... I fear I may not have formatted it correctly.

---

