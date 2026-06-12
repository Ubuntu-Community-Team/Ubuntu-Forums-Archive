---
title: "Many Ubuntus???"
date: 2010-10-17
forum: New to Ubuntu
---

### Post by mahmoodkamal on 2010-10-17
I have recently upgraded from 10.04 to 10.10. My question is when I boot my computer the Grub boot loader shows me several options, such as:

Ubuntu 10.10 X-X-X-X
Ubuntu 10.10 X-X-X-X (recovery mode)


Ubuntu 10.10 Y-Y-Y-Y
Ubuntu 10.10 Y-Y-Y-Y (recovery mode)

Which one to choose to boot up?

Kindly explain.

Thanks

---

### Post by Elfy on 2010-10-17
Kernel's get upgraded. The one at the top is the most recent. Once I have more than 2 kernels installed I start removing the oldest one.

I would always keep the most recent 2.

---

### Post by madmax75 on 2010-10-17
When Ubuntu updates the kernel, it usually keeps a few old kernels around just in case. If the new kernel causes trouble, you can boot the computer with the old kernels.

10.10 must have updated the kernel after you installed it, so this is why you see both the new and the old kernel in your Grub boot loader.

---

### Post by Hippytaff on 2010-10-17
> **forestpiskie said:**
> Kernel's get upgraded. The one at the top is the most recent. Once I have more than 2 kernels installed I start removing the oldest one.

I would always keep the most recent 2.

Does the kernel get upgraded with the standard apt-get update/upgrade...or is there a different command for this?

(Sorry to hijack the thread)

---

### Post by krishnandu.sarkar on 2010-10-17
Yes kernel updates comes with normal updates. BTW you can remove the previous kernels from ubuntu-tweak. Though it's not recommended.

Take a look at these

[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)
[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

---

### Post by Elfy on 2010-10-17
I am old fashioned and remove with synaptic :)

---

### Post by Paqman on 2010-10-17
> **forestpiskie said:**
> I am old fashioned and remove with synaptic :)

This. Hit the filter for installed packages and search for "linux-image", you'll see them all. You can uninstall everything except the latest one. It's worth doing, especially on machines with small drives, as you'll gain back 100MB per kernel. Uninstalling them will clean up the Grub list.

You can also use startupmanager to limit the number of kernels shown in Grub.

---

### Post by amjjawad on 2010-10-17
> **mahmoodkamal said:**
> I have recently upgraded from 10.04 to 10.10. My question is when I boot my computer the Grub boot loader shows me several options, such as:

Ubuntu 10.10 X-X-X-X
Ubuntu 10.10 X-X-X-X (recovery mode)


Ubuntu 10.10 Y-Y-Y-Y
Ubuntu 10.10 Y-Y-Y-Y (recovery mode)

Which one to choose to boot up?

Kindly explain.

Thanks


[http://ubuntuforums.org/showthread.php?t=1586923](http://ubuntuforums.org/showthread.php?t=1586923)

---

### Post by da burger on 2010-10-17
> **Paqman said:**
> This. Hit the filter for installed packages and search for "linux-image", you'll see them all. You can uninstall everything except the latest one. It's worth doing, especially on machines with small drives, as you'll gain back 100MB per kernel. Uninstalling them will clean up the Grub list.

You can also use startupmanager to limit the number of kernels shown in Grub.

I would recommend that you leave at least two. Things can go wrong :)
Angus

---

### Post by Paqman on 2010-10-18
> **da burger said:**
> I would recommend that you leave at least two. Things can go wrong :)
Angus

If you're on the development branch, definitely. If you're running a stable release, there's no real need. Has a major kernel regression ever made it into a stable Ubuntu release? I've certainly never had one.

---

### Post by Elfy on 2010-10-18
I have a couple of years ago - or at least my memory of whether it was in a dev version or not is hazy enough to make me keep two :D

Edit - I do remember the fix appearing in hours but ...

---

