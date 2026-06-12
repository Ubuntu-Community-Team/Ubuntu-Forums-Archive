---
title: "[SOLVED] TrueCrypt System Drive Encryption"
date: 2008-12-29
forum: New to Ubuntu
---

### Post by Goll on 2008-12-29
Am I missing something?

Oh yes, I googled it, but no one's talking about it.
I don't understand. Why is it so *Awesomely *impossible to encrypt the partitions your installation is on with TrueCrypt? 
(Yes. **The whole thing.** The whole drive. Pow.)
Is it because this would require the replacement of GRUB?
Please don't say the word LVM, because I've tried ...

about 6 times to get it to work (in varying ways) and it never has worked. (Besides with Debian.) *Which doesn't support my printer, or have access to proprietary drivers...*

Would it be so hard to implement this?
I don't quite understand what's going on here.

Kind of funny.
Here's one for you: I can't install LVM. I need drive encryption. Only Windows supports TrueCrypts drive encryption. = I need windows to be secure.

Get a laugh out of that..

---

### Post by BDNiner on 2008-12-29
I think that complete system encryption is only supported under Windows Vista.

---

### Post by aurelieng on 2008-12-29
An alternative to TrueCrypt is to encrypt your filesystems with LUKS (except the /boot partition, of course). You can follow the guide @ [http://howtoforge.com/set-up-a-fully-encrypted-raid1-lvm-system](http://howtoforge.com/set-up-a-fully-encrypted-raid1-lvm-system) . Also, note that you don't have to use LVM stuff.

---

### Post by Moop on 2008-12-29
Use the alternate install cd and choose full disk encryption. I've never had a problem with the install or use. It works great.

---

### Post by Goll on 2008-12-29
> **aurelieng said:**
> An alternative to TrueCrypt is to encrypt your filesystems with LUKS (except the /boot partition, of course). You can follow the guide @ [http://howtoforge.com/set-up-a-fully-encrypted-raid1-lvm-system](http://howtoforge.com/set-up-a-fully-encrypted-raid1-lvm-system) . Also, note that you don't have to use LVM stuff.

This is for RAID. I do not own a RAID drive.
Also, this installation procedure is for Debian. I am not installing through Debian.
Thank you though.

> **Moop said:**
> Use the alternate install cd and choose full disk encryption. I've never had a problem with the install or use. It works great.

Thank you, I have already done that. (Even the Guided one.)
Every time I reboot, GRUB errors with #15.

> **BDNiner said:**
> I think that complete system encryption is only supported under Windows Vista.

Yes, that is what I'm gathering.

---

### Post by aurelieng on 2008-12-29
Whoups... seems that I posted the wrong link, sorry.

The guide for ubuntu 8.10 with LUKS is @ [http://learninginlinux.wordpress.com/2008/04/23/installing-ubuntu-804-with-full-disk-encryption/](http://learninginlinux.wordpress.com/2008/04/23/installing-ubuntu-804-with-full-disk-encryption/)

You tried sth similar and got a grub error 15 ? Weird... I did it several time, without any problems.

---

### Post by Goll on 2008-12-29
I am doing this on another hard drive other than the first one.
I believe this may be the source of my problems.

---

### Post by igknighted on 2008-12-29
You cannot boot to an encrypted partition.  Something needs to load first to decrypt it.  If you want to have your primary filesystem encrypted, make sure you have an unencrypted /boot partition.

---

### Post by jerome1232 on 2008-12-29
> **Moop said:**
> Use the alternate install cd and choose full disk encryption. I've never had a problem with the install or use. It works great.

+1. It's very painless, lvm and luks are included by default on the alternate install cd. You have to create a seperate /boot partition when working with encryption. Usually I do something like this:

```

/dev/sda1 200 Mb /boot
/dev/sda5 The rest of my Drive. Physical Volume for Encryption.
/dev/sda5crypt Entire partion, Physical Volume for LVM
-------   Create a volume group that takes up the entire drive, I give
          it the same name as the computers hostname.
          ----- I create 2 volume groups, on is for swap the other my root 
                partition. I leave enough space so that I can create a snapshot for the purpose of backups. (~10% of the partition)
```

---

### Post by Goll on 2008-12-30
Turns out the problem was the **External HD **I had hooked up.
The device showed up 1st in the list of hd's to partition.
I removed the usb before install, did the same procedure and it worked fine.

-good day.

---

### Post by levelup3 on 2008-12-30
Thanks for all your post

---

