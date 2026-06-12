---
title: "Experience on grub4dos"
date: 2009-11-16
forum: New to Ubuntu
---

### Post by Albert Net on 2009-11-16
[SIZE=3]Just used grub4dos because of ubuntu for a while. I feel like it, tiny but powerful. Unfortunately, a lot documentations about it didn't mention one point, which confused beginner a lot. I am not the exception.

In grub4dos, the "root" really means root, that everything derives from, while in ubuntu we use the meaning that root is administrator in most cases, which is a big difference.

For example
root  (hd0,0)      // All your operations begin from the first sector of your first hard disk. Here by first hard disk, we mean the one where grub4dos is, which confused me for a long time, for it does not must coincide with the order that is recognized by your BIOS. Grub4dos always think the hard disk where it is is the first one, while BIOS is a little clever, that BIOS recognizes several hard disks in the ordinary order.

kernel /kerne(tab)  root=/dev/sda0        //Indicates where the kernel is. Because I can't remember the exactly name of my kernel, I just use "tab", which is extremely useful. Here we tell ubuntu where the root (the partition of root)is.

initrd /ini(tab)     //I am a lazy typer, use "tab" again, initiallizing kernel

boot       //Succeed.
 
Form is dead. The correct way to do it on your computer is probably not what I showed above, but you should understand how to do it right, since I have told you what all the stuff mean.

The example above is mundane, and possibly useful when you edit the menu.lst, which doesn't happen a lot. The next example is much more practical.

root (hd1,2)
kernel /vm(tab) boot=casper iso-scan/filename=ubun(tab) 
initrd /in(tab)
boot

Using this method, we can install ubuntu from iso file without burning it on a CD. The only thing we need is to extract vmlinuz and initrd.lz from casper, which is a directory in iso file.
[/SIZE]

---

