---
title: "dual booted, with Ubuntu and Windows XP doesn't show"
date: 2010-03-26
forum: New to Ubuntu
---

### Post by EEVIAC on 2010-03-26
I just installed Ubuntu and grub seems to have not detected my other operating system, Windows XP.  Windows XP was on the hard drive first and I just added Ubuntu 9.10.  During setup, it gave me an option to use grub as the boot loader and I opted to use it, but Windows XP is not showing up in the boot loader, so I can't boot into XP.

How can I add XP to the boot loader?

---

### Post by Gixxy on 2010-03-26
Well hopefully when you setup ubuntu you didn't tell it to use the entire disk in the partitioner!

It should have just shown up but maybe something happened... 

I would try these two commands first as an easy way to get Windoze as a boot option.

```
sudo update-grub
```
or...
```
sudo update-grub2
```

Depending on your version of grub. If you just installed the lastest version of ubuntu "9.10 Karmic" then it will be grub2 all earlier versions of ubuntu would be grub.

You should get something like this after you run that.

> :~$ sudo update-grub2
[sudo] password for username: 
Generating grub.cfg ...
Found Debian background: Debian_Infinity.jpg
Found linux image: /boot/vmlinuz-2.6.31-20-generic
Found initrd image: /boot/initrd.img-2.6.31-20-generic
Found linux image: /boot/vmlinuz-2.6.31-19-generic
Found initrd image: /boot/initrd.img-2.6.31-19-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done


Hope that helps!

---

### Post by EEVIAC on 2010-03-26
the first command worked like a charm..


thx

---

