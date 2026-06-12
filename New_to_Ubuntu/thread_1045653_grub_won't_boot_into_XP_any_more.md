---
title: "grub won't boot into XP any more"
date: 2009-01-20
forum: New to Ubuntu
---

### Post by talguy on 2009-01-20
Ok so I just upgraded from ubuntu 8.04 to 8.10 since the upgrade grub no longer can boot into my windows xp partition.  When I try to boot into the partition it gives me an error saying that this format is not executable.

here is my menu.lst
> 
title		Ubuntu 8.10, kernel 2.6.27-9-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=0546ed2b-6773-4b55-8b27-2b53f66f4cf0 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=0546ed2b-6773-4b55-8b27-2b53f66f4cf0 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.24-22-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=0546ed2b-6773-4b55-8b27-2b53f66f4cf0 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-22-generic
quiet

title		Ubuntu 8.10, kernel 2.6.24-22-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=0546ed2b-6773-4b55-8b27-2b53f66f4cf0 ro  single
initrd		/boot/initrd.img-2.6.24-22-generic

title		Ubuntu 8.10, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title Microsoft Windows XP
root (hd0,1)
savedefault
makeactive
chainloader +1


---

### Post by Ub1476 on 2009-01-20
I'm pretty sure your problem lies in the root section, which as you can see, is exactly the same in both Ubuntu and XP. I think it's supposed to be like this:


### END DEBIAN AUTOMAGIC KERNELS LIST

title Microsoft Windows XP
**root (hd0,0)**
savedefault
makeactive
chainloader +1

---

### Post by 73ckn797 on 2009-01-20
The "root (hd0,1)" info should not be the same for Ubuntu and Win XP.

Provide the output from Applications/Accessories/Terminal for:
```
sudo fdisk -l
```Post results back in reply.

Above root info suggested by [Ub1476]("http://ubuntuforums.org/member.php?u=296405") may also fix the issue.

---

### Post by talguy on 2009-01-20
thanks you guys for helping me out.  I am current writing this in windows xp.  I guess when I upgraded ubuntu it deleted my window's information out of menu.lst so a placed it back in and I didn't take notice of that mistake i made

Thanks again

---

