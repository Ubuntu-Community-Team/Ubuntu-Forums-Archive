---
title: "How can I update kernels in Grub 2 (9.10) ?"
date: 2010-05-03
forum: New to Ubuntu
---

### Post by Mongoose088 on 2010-05-03
Hi all,

I've just upgraded my Ubuntu 9.04 system to 9.10 (not a clean install, I used the update manager). During the installation it asked me what I wanted to do with "menu.lst", and I picked the default option (to leave it as it is, I believe). Now I'm having some issues which I believe can be fixed with a kernel update.


I am running Grub 2, but when I use the "update- grub" commmand, the output suggests it found the 2.6.3.xx kernel:
```

sudo update-grub
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.31-21-generic
Found kernel: /boot/vmlinuz-2.6.28-18-generic
Found kernel: /boot/vmlinuz-2.6.28-11-generic
Found GRUB 2: /boot/grub/core.img
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

```

But as I understand it, menu.lst is not used for Grub2.

So, if we look at /boot/grub/grub.cfg (relavant portion)
```

### BEGIN /etc/grub.d/10_linux ###
set root=(hd0,1)
search --fs-uuid --set f47b3f0b-a70c-4945-8fab-002a7faa27e8
menuentry "Ubuntu, linux 2.6.28-18-generic" {
        linux   /boot/vmlinuz-2.6.28-18-generic root=UUID=f47b3f0b-a70c-4945-8fab-002a7faa27e8 ro  quiet splash i8042.reset
        initrd  /boot/initrd.img-2.6.28-18-generic
}
menuentry "Ubuntu, linux 2.6.28-18-generic (single-user mode)" {
        linux   /boot/vmlinuz-2.6.28-18-generic root=UUID=f47b3f0b-a70c-4945-8fab-002a7faa27e8 ro single
        initrd  /boot/initrd.img-2.6.28-18-generic
}
menuentry "Ubuntu, linux 2.6.28-11-generic" {
        linux   /boot/vmlinuz-2.6.28-11-generic root=UUID=f47b3f0b-a70c-4945-8fab-002a7faa27e8 ro  quiet splash i8042.reset
        initrd  /boot/initrd.img-2.6.28-11-generic
}
menuentry "Ubuntu, linux 2.6.28-11-generic (single-user mode)" {
        linux   /boot/vmlinuz-2.6.28-11-generic root=UUID=f47b3f0b-a70c-4945-8fab-002a7faa27e8 ro single
        initrd  /boot/initrd.img-2.6.28-11-generic
}
### END /etc/grub.d/10_linux ###

```

How exactly do I confirm that a new kernel is installed, and how do I tell ubuntu's grub 2 to start booting from it?

Thanks for your help. If you need more information, just ask

---

### Post by clhsharky on 2010-05-03
HI Mongoose088

Install ' StartUp-Manager ' from software center or synaptic package manager.
 Startup manager will show you what kernels you have installed and let choose the kernel to use.

Sharky

---

### Post by Mongoose088 on 2010-05-04
> 
HI Mongoose088

Install ' StartUp-Manager ' from software center or synaptic package manager.
Startup manager will show you what kernels you have installed and let choose the kernel to use.

Sharky 


I installed start up manager, but it only lists 2.6.2.x kernels. So it seems that my new kernel isn't installed. How exactly can I install the new kernel, or make the manager see where my kernel is installed?

Thanks for such a quick reply.

---

### Post by xumuk37 on 2010-05-04
in Synaptic reload, look for "generic" "kernel" and "headers" and mark for upgrade with RMB then apply. That's it.

---

### Post by xumuk37 on 2010-05-04
bump

---

### Post by Elfy on 2010-05-04
Find out what grub you are using 

```
grub-install -v
```

It would appear that menu.lst was updated - > Updating /boot/grub/menu.lst ... done

Edit to use grub2 you would need to upgrade grub - from 9.04 to 9.10 this would not be done automatically. [https://help.ubuntu.com/community/Grub2#Upgrading%20to%20GRUB%202](https://help.ubuntu.com/community/Grub2#Upgrading%20to%20GRUB%202)

---

### Post by Mongoose088 on 2010-05-04
> 
in Synaptic reload, look for "generic" "kernel" and "headers" and mark for upgrade with RMB then apply. That's it. 


> 
Find out what grub you are using

Code:

grub-install -v

It would appear that menu.lst was updated -
Quote:
Updating /boot/grub/menu.lst ... done
Edit to use grub2 you would need to upgrade grub - from 9.04 to 9.10 this would not be done automatically. [https://help.ubuntu.com/community/Gr...0to%20GRUB%202](https://help.ubuntu.com/community/Gr...0to%20GRUB%202)


Thank you both for your replies. It turns out that upon updating to 9.10, GRUB rolled back to legacy. I was able to solve this problem after reinstalling GRUB 2.

Problem solved!

Thanks to everyone who helped.

---

