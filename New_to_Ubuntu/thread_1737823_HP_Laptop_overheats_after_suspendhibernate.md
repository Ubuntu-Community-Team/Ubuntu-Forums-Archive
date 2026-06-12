---
title: "HP Laptop overheats after suspend/hibernate"
date: 2011-04-23
forum: New to Ubuntu
---

### Post by ngubk on 2011-04-23
Since ubuntu 10.04, my laptop (hp 4410s) often got overheated after hibernate/suspend. CPU still runs low but the laptop's very hot( 90c). Do you have any idea?

---

### Post by josephmills on 2011-04-23
open the laptop up and clean it all of it especially the fan and the vents.  you could also put some new heat grease on the cpu or cpu's

---

### Post by Hedgehog1 on 2011-04-23
In addition to cleaning (cleaning is always a good idea):

To improve the function of the laptop fan using 'current' grub options:

```
gksudo gedit /etc/default/grub
```

```
GRUB_CMDLINE_LINUX_DEFAULT=**"**quiet splash **acpi_osi=\\\"Linux\\\""**
```

There are a total of **4 double quotes** in this line (2 side-by-side at the end)

Then do:

```
sudo update-grub
```

**And reboot. The operation of this will keep your computer running cooler.**

In case you are wondering WHY all these slashes, it is because this text string gets processed twice before it is used to boot the kernel:

In /etc/default/grub it looks like this:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=\\\"Linux\\\""
```

Which gets converted by the update-grub in /boot/grub/grub.cfg as:
```
linux /boot/vmlinuz-2.6.31-8-generic root=UUID=78b161e2-4d82-4df7-a423-8289fe6cc704
ro quiet splash acpi_osi=\"Linux\"
```

The command is then passed to the kernel when run by grub as:
```
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-8-generic root=UUID=78b161e2-4d82-4df7-a423-8289fe6cc704
ro quiet splash acpi_osi="Linux"
```

See how easy that (isn't) to follow?


***The Hedge***

:KS

---

### Post by ngubk on 2011-04-23
I just cleaned up my laptop a month ago. I dualboot Window XP (though i rarely use it) and it's never gotten overheated like that. 
I don't know why grub got involved with this but i'll try your idea. Thanks a lot.

---

### Post by jramshu on 2011-04-23
Hedgehog1, what does that code do? I'm curious. How does it change the fan settings?

I'm tempted to try it, my HP usually runs around 127F and up. Will it help it run cooler or help it stop varying so much? I have read around and can't seem to find a direct answer.

I know the fan pretty much runs wide open when running W*****s, especially if there is any graphics involved. In Ubuntu I monitor my temps with this code.
```
sensors -f
```
Thanks.

---

