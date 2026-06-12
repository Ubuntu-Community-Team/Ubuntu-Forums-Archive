---
title: "Making Grub parameters permanent"
date: 2010-08-08
forum: New to Ubuntu
---

### Post by Quixotic Hacker on 2010-08-08
Each time I boot I have to do two things:
1. Remove the 'quiet splash' parameter;
2. and replace it with pci=nomsi

Is there a way to make Grub boot like this automatically each time I reboot? If so, how?

---

### Post by bodhi.zazen on 2010-08-08
> **Quixotic Hacker said:**
> Each time I boot I have to do two things:
1. Remove the 'no splash' parameter;
2. and replace it with pci=nomsi

Is there a way to make Grub boot like this automatically each time I reboot? If so, how?

Add those options to the kernel line in /etc/default/grub

The default reads GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

See [https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2) for details

---

### Post by drs305 on 2010-08-08
You should be able to open /etc/default/grub and make those entries on the following line:
> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
Edit the file as root and make it look like this:
> GRUB_CMDLINE_LINUX_DEFAULT="pci=nomsi"

I'm not familiar with the specific setting you want to add, but if you make that change and then run "sudo update-grub" it should incorporate it into the grub menu parameters.

---

### Post by bodhi.zazen on 2010-08-08
> **drs305 said:**
> You should be able to open /etc/default/grub and make those entries on the following line:

Edit the file as root and make it look like this:


I'm not familiar with the specific setting you want to add, but if you make that change and then run "sudo update-grub" it should incorporate it into the grub menu parameters.

I would use ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pci=nomsi"
```

If you remove the quiet you will get more messages from the kernel as you boot (more messages flashing on the screen) and if you remove splash you will not get a boot splash (I think, although I am not positive with plymouth).

As far as kernel boot options:

[http://www.kernel.org/doc/Documentation/kernel-parameters.txt](http://www.kernel.org/doc/Documentation/kernel-parameters.txt)

> nomsi		[MSI] If the PCI_MSI kernel config parameter is
				enabled, this kernel boot option can be used to
				disable the use of MSI interrupts system-wide.

although that is probably Greek to most :twisted:

[http://www.linuxtopia.org/online_books/linux_kernel/kernel_configuration/ch10.html](http://www.linuxtopia.org/online_books/linux_kernel/kernel_configuration/ch10.html)

---

### Post by Quixotic Hacker on 2010-08-08
Thanks for the suggestions, all. I will let you know if I get it to work.

---

### Post by Quixotic Hacker on 2010-08-08
Reboot went smooth. Thanks for the help.

---

### Post by scott8035 on 2011-04-27
We're using 10.10-server. We had the same desire to make grub boot changes permanent. We updated /etc/default/grub, and update-grub propagates those changes into /boot/grub/grub.cfg, but not into menu.lst. It appears to use menu.lst as the source, so our change doesn't show up as a linux parm when booting. Any ideas?

---

### Post by drs305 on 2011-04-27
> **scott8035 said:**
> ...but not into menu.lst. It appears to use menu.lst as the source, so our change doesn't show up as a linux parm when booting. Any ideas?

You can edit /boot/grub/menu.lst in the same manner. Add the options to the end of the kernel line in the menu item you wish to change and save the file. 

IIRC you can also add it to the "# kopt" in the upper part of menu.lst so it is added if updates actually update grub legacy and grub 2. Do not remove the # at the start of the "# kopt", it's not a comment symbol.

---

