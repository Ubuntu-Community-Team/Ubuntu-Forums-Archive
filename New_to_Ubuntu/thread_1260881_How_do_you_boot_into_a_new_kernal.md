---
title: "How do you boot into a new kernal?"
date: 2009-09-08
forum: New to Ubuntu
---

### Post by boxxy27 on 2009-09-08
I heard that the new RC release of the linux kernel 2.6.31-rc9 has a fix for the intel pro 100 cards and because iv been having multiple problems with it i downloaded it and installed it. 

Thing is, i dont know what to do next because when i re-booted i was still in the 2.26.1 kernal instead of the RC.

So how do you configure grub or whatever to boot into the newly installed kernel?

---

### Post by nothingspecial on 2009-09-08
Reboot and when you see  the grub loading dialogue press escape then choose your new kernel.

Do it this way for a few days to check everything works then if your happy back up your /boot/grub/menu.lst

```
sudo cp /boot/grub/menu.lst ~/boot_backup
```

Then ```
sudo nano /boot/grub/menu.lst
```

and put a # infront of the kernel you don`t want to boot.

---

### Post by boxxy27 on 2009-09-08
The only problem is that it is not located under grub for some reason...
i downloaded the .debs here btw 

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.31-rc9/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.31-rc9/)

so what did i do wrong?

---

### Post by egalvan on 2009-09-08
I experimented with these a couple months ago...
I followed this HowTo...


[https://wiki.ubuntu.com/KernelTeam/MainlineBuilds](https://wiki.ubuntu.com/KernelTeam/MainlineBuilds)

It worked for me.

GRUB was updated automatically.

---

### Post by philinux on 2009-09-08
Have you ran update-grub?

---

### Post by nothingspecial on 2009-09-08
If it`s been installed correctly and exists within /boot it should just be a matter of copying one of the other kernel entries and changing the kernel entry.

---

