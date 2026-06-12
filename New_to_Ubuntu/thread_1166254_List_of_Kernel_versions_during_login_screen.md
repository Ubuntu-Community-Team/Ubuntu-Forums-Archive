---
title: "List of Kernel versions during login screen"
date: 2009-05-21
forum: New to Ubuntu
---

### Post by babloo75 on 2009-05-21
I upgraded Ubuntu 8.10 to 9.04, i think it has been updated fully but during boot the black screen gives the same list of kernel versions (two are with recovery mode and two without recovery). is it normal to have two kernel versions even after upgrading. 
I thought the older obsolete will be deleted on its own. am i right to think so. 
How can i determine whether the kernel version is upgraded correctly and the older one (if not required now) can be removed? Is it ok to remove the older version?
Please guide.

---

### Post by snowpine on 2009-05-21
It is good to keep at least two kernel versions. That way, you have a spare if one breaks. :) Unless you are very short on hard drive space, there is no disadvantage to keeping the old one.

The correct kernel for 9.04 contains the numbers 2.6.28. If that appears in your Grub, then the upgrade was successful. (8.10 was 2.6.27.)

---

### Post by durand on 2009-05-21
> **snowpine said:**
> It is good to keep at least two kernel versions. That way, you have a spare if one breaks. :) Unless you are very short on hard drive space, there is no disadvantage to keeping the old one.

The correct kernel for 9.04 contains the numbers 2.6.28. If that appears in your Grub, then the upgrade was successful. (8.10 was 2.6.27.)

Grub looks pretty ugly with all those kernel lines.

babloo75, you can just edit /boot/grub/menu.lst and delete the paragraphs at the bottom of the file which you don't need anymore.

```
sudo gedit /boot/grub/menu.lst
```

The better solution here would be to just uninstall the kernel versions with System > Administration > Synaptic Package Manager. Just use the search tool (Not quick search) and find linux-image. In a terminal, type uname -r. Uninstall any packages that are not linux-image-whatever_your_version_is.

---

### Post by snowpine on 2009-05-21
If the only concern is cosmetic, the more elegant solution is to add the hiddenmenu option to grub with a short timeout. Then you don't have to look at all those kernel options, but you can hit Esc if you need them. :)

---

### Post by durand on 2009-05-21
That's true. You can also add two lines between the option you want and the others.
```
title
root
``` which will "hide" the options below that line but if you move over them, they will become visible again.

This is what mine looks like:
> 
title           Crunchbang
root            (hd0,9)
kernel          /vmlinuz root=/dev/sda10 ro quiet splash i8042.reset usbcore.au$
initrd          /initrd.img
quiet

title
root

title           Fedora
root            (hd0,10)
kernel          /boot/vmlinuz-2.6.29.1-102.fc11.x86_64 root=/dev/sda11 ro vga=3$
initrd          /boot/initrd-2.6.29.1-102.fc11.x86_64.img
quiet


---

### Post by celticbhoy on 2009-05-21
You could just install startup manager & set the number of kernels there.

---

### Post by babloo75 on 2009-05-21
I am unaware of these things........ let it be like this only..... don't want a mess with my ubuntu, if something goes wrong.
Thanks anyway.

---

### Post by mprince on 2009-05-21
If you'd like to see which kernel version you are currently using, type this in a terminal:

```
uname -r
```

This won't hurt anything.

---

### Post by babloo75 on 2009-05-22
thanks.

---

### Post by rcayea on 2009-09-01
> **celticbhoy said:**
> You could just install startup manager & set the number of kernels there.

I never heard of this and WOW!!!!!!I love it!

Thanks for posting.

---

### Post by drs305 on 2009-09-01
Here's a guide on how to use StartUp-Manager, if you should have any questions on the settings or want to know how to physically remove extra kernels:
[http://ubuntuforums.org/showthread.php?t=818177]("http://ubuntuforums.org/showthread.php?t=818177")

---

