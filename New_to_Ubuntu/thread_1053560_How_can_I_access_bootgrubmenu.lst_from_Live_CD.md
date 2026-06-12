---
title: "How can I access boot/grub/menu.lst from Live CD?"
date: 2009-01-28
forum: New to Ubuntu
---

### Post by kansasnoob on 2009-01-28
No urgency here, I found a way to "fix it", but there has to be a better and easier way!

I made a stupid mistake last night!

I deleted some partitions to reinstall Vista on a friends dual-boot machine and I thought I'd pre-planned properly as far as editing the  /boot/grub/menu.lst.

Well, I was close, but I'd messed up the "kopt" and "groot" parts of the menu list. I simply goofed! I was working with Ubuntu on sda6 and I made the right entries "hd05" in the boot sequence, but in the "kopt" and "groot" parts of the menu list I had a brain fart and made them (hd0,6).

Just a pure goof up! Of course I could mount the partition using a live CD and mount that partition and then go to File System > Boot > Grub > Menu.lst, and of course I could immediately see the problem but I couldn't fix and "save" it.

Since I'd been using a minimal ubuntu CD trying some lightweight alternatives I just shrunk one of the new Vista partitions and installed Ubuntu minimal with a new GRUB and mounted the Ubuntu OS from there to make the edits I needed to make.

But, sheesh, there must be an easier way!

I tried (e) and (c) from Grub but couldn't get there.

Does this make sense to anyone?

As I said, I got it fixed, but I just think there should be an easier and much faster way!

I want to know because I'm sure this won't be my last "brain fart"!

---

### Post by rmockler on 2009-01-28
Before you go to boot/grub/menu.lst, open a terminal session and key gksu nautilus
Then navigate to boot/grub/menu.lst, fix your error and save the file.

---

### Post by Boomhauer on 2009-01-28
you couldnt save because you didnt have permission?
with booting a live cd did you ```
sudo mount /dev/sda6 /mnt

sudo nano /mnt/boot/grub/menu.lst
```

---

### Post by Sorivenul on 2009-01-28
1.) Boot your Ubuntu LiveCD
2.) Open a terminal
3.) sudo mkdir /mnt/ubuntu
4.) sudo mount -t ext3 /dev/sdaX /mnt/ubuntu (where sdaX is your partition, assuming it is ext3 formatted)
5.) gksudo gedit /mnt/ubuntu/boot/grub/menu.lst (edit and save - really you can use any editor you like, just make sure to save)
6.) Reboot

---

### Post by kansasnoob on 2009-01-29
> **Sorivenul said:**
> 1.) Boot your Ubuntu LiveCD
2.) Open a terminal
3.) sudo mkdir /mnt/ubuntu
4.) sudo mount -t ext3 /dev/sdaX /mnt/ubuntu (where sdaX is your partition, assuming it is ext3 formatted)
5.) gksudo gedit /mnt/ubuntu/boot/grub/menu.lst (edit and save - really you can use any editor you like, just make sure to save)
6.) Reboot

Darn excellent instructions! I'm curious what "mount -t" means?

I'm learning and I like to know what I'm doing.

---

### Post by kansasnoob on 2009-01-29
> **Boomhauer said:**
> you couldnt save because you didnt have permission?
with booting a live cd did you ```
sudo mount /dev/sda6 /mnt

sudo nano /mnt/boot/grub/menu.lst
```

I'd swear I tried that other than using gedit in place of nano and it was a "no-go"!

That's why I finally just used my Ubuntu Minimal CD to shrink the new Vista 2GB and then I used that GRUB to mount my Ubuntu partition and properly edit the menu list.

Then I deleted the new partition and put everything right! (And luckily did not hose the fresh Vista install)!

---

### Post by Sorivenul on 2009-01-29
> **kansasnoob said:**
> Darn excellent instructions! I'm curious what "mount -t" means?

I'm learning and I like to know what I'm doing.

The "mount -t ext3" specifies the type of the filesystem to be mounted. Mounting an NTFS filesystem (Windows) would be something like "mount -t ntfs-3g /dev/sda1 /mnt/win32". 

For more information:
```
man mount
```

---

### Post by kansasnoob on 2009-01-29
> **Sorivenul said:**
> The "mount -t ext3" specifies the type of the filesystem to be mounted. Mounting an NTFS filesystem (Windows) would be something like "mount -t ntfs-3g /dev/sda1 /mnt/win32". 

For more information:
```
man mount
```

Thank you!

I like to know, it helps later on!

---

