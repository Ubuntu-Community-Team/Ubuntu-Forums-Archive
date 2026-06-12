---
title: "Just another Grub problem"
date: 2010-01-24
forum: New to Ubuntu
---

### Post by ozbolt on 2010-01-24
I had installed Windows firstly, after that Ubuntu 9.10 (in august i think - beta) and not long ago Windows7 again (it just stopped working properly for unknown reason) and now I restored grub menu. But when I click on Windows 7 in menu list, this shows up:
Can't boot: b0aeadb3aead7290 (or somethig like this). 
There is my grub file:
```
### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
        insmod ntfs
        set root=(hd0,1)
        search --no-floppy --fs-uuid --set b0aeadb3aead7290
        chainloader +1

```

I know what is the problem but I have no clue how to fix it. Please help.

---

### Post by weichimaster on 2010-01-24
Does the uuid in grub (b0aeadb3aead7290) agree with the drive's uuid?

You can find uuid with:

```
sudo blkid

```

It looks like you're after the identifier for sda1 .

---

### Post by ozbolt on 2010-01-24
With a little bit of playing with these UUIDs I got it to work. Thanks :)

---

### Post by weichimaster on 2010-01-24
Glad to help! :D

You shouldn't need to manually edit grub.cfg, by the way - sudo update-grub should build it automatically for you.

---

