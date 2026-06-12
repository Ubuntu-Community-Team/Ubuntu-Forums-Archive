---
title: "Grub2 issue with dual-boot"
date: 2010-12-27
forum: New to Ubuntu
---

### Post by HerzyWSU on 2010-12-27
Hi

I'm running a PC with Ubuntu 10.10 on one hard drive and Mint 9 LXDE on the other.  

Upon booting up, grub2 immediately boots up with the Mint splash in the background, even though the BIOS boots the Ubuntu drive first.  I'm planning on blowing away the Mint hard drive for a new hard drive, and I want to make sure that when I format the Mint hard drive that I'll be able to boot up the Ubuntu drive without a hitch.

P.S. I'm sure it's probably a redundant question, but I used the search feature and couldn't find the answer I was looking for

---

### Post by wilee-nilee on 2010-12-27
> **HerzyWSU said:**
> Hi

I'm running a PC with Ubuntu 10.10 on one hard drive and Mint 9 LXDE on the other.  

Upon booting up, grub2 immediately boots up with the Mint splash in the background, even though the BIOS boots the Ubuntu drive first.  I'm planning on blowing away the Mint hard drive for a new hard drive, and I want to make sure that when I format the Mint hard drive that I'll be able to boot up the Ubuntu drive without a hitch.

P.S. I'm sure it's probably a redundant question, but I used the search feature and couldn't find the answer I was looking for

If you installed the mint last it has the last grub bootloader added to the mbr.

If you want to insure the Ubuntu 10.10 is the controlling bootloader in 10.10 in a terminal run this
```
sudo grub-install /dev/sda
```

I have used sda that last 3 letters of the command must be pointed at the 10.10 hd run this command to confirm the hard drive letter.
```
sudo fdisk -lu
```

---

### Post by HerzyWSU on 2010-12-29
Thanks, exactly what I was looking for.

---

