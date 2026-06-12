---
title: "Advice on compiling / Installing Realtek PCI-E NIC drivers in Feisty"
date: 2007-05-14
forum: Networking &amp; Wireless
---

### Post by galileux on 2007-05-14
Hi
I have a running setup of Feisty on a P5B Asus Motherboard featuring the onboard card mentioned in the title.

I discovered that I have a transfer problem and I found the threads below nailing the problem down to the absence of Realtek drivers.

[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/112794](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/112794)
[http://ubuntuforums.org/showthread.php?p=2618121](http://ubuntuforums.org/showthread.php?p=2618121)

I am scared of messing up my Feisty because I have no experience of compiling the kernel on-the fly.

Is anyone going to be so good to provide a safe procedure to get the Realtek driver installed without much pain?

Thanks for any help

---

### Post by nonlinear on 2007-05-16
sorry, didn't read the title carefully and thought you were talking about audio driverxs

cheers :)

---

### Post by chili555 on 2007-05-16
I'll be glad to help. Let's start with a link to the driver you want to install. I'll compile it, too, as we go along. In the meantime, please be sure you have *build-essential* and *linux-headers-`uname -r`* installed.

---

### Post by galileux on 2007-05-17
Hi Chili
Thanks for offering to help
I actually did both things. Compiled the module into the kernel, was quite painless.
The onboard card was bugged anyway (or feisty is), so I ended up shoving in an old Realtek contoller into an available PCI port and disabling the onboard NIC from the BIOS.
Thanks
Galileus

---

