---
title: "Got suddendly logged out"
date: 2009-08-05
forum: New to Ubuntu
---

### Post by ubudog on 2009-08-05
Hi,  I just got suddendly logged out and when I logged back in, I looked at dmesg and this is what it had to say: Xorg[31082]: segfault at 1c ip b6538209 sp bfff2a00 error 4 in nvidia_drv.so[b64ea000+3b4000]



Help please!:confused:

---

### Post by ubudog on 2009-08-05
Update:I uninstalled ccsm and now it works fine.  My computer's kinda got an old graphics card anyway.  Gotta get a new one sometime. :)  The Cube was kinda nice though.....I guess I'll just live with only wobbly windows for now.  In extra effects mode. :)

---

### Post by 3rdalbum on 2009-08-05
CCSM just allows you to change the Compiz settings from the comfort of a GUI, rather than manually editing files. So removing CCSM itself doesn't solve any problems.

The error message basically says that the Nvidia driver crashed, causing the Xorg server to crash too. If you're not running the latest Nvidia driver, then updating may help to actually solve the problem, assuming that it wasn't a badly-behaved Compiz plugin that caused the original crash.

I recommend learning how to edit the Xorg.conf file from a command-line before manually installing any graphics card drivers. Usually if anything goes wrong Ubuntu will give you the option of starting an unaccelerated desktop, but some people have reported that this option doesn't always appear.

---

### Post by ubudog on 2009-08-05
> **3rdalbum said:**
> CCSM just allows you to change the Compiz settings from the comfort of a GUI, rather than manually editing files. So removing CCSM itself doesn't solve any problems.

The error message basically says that the Nvidia driver crashed, causing the Xorg server to crash too. If you're not running the latest Nvidia driver, then updating may help to actually solve the problem, assuming that it wasn't a badly-behaved Compiz plugin that caused the original crash.

I recommend learning how to edit the Xorg.conf file from a command-line before manually installing any graphics card drivers. Usually if anything goes wrong Ubuntu will give you the option of starting an unaccelerated desktop, but some people have reported that this option doesn't always appear.

Thanks for the response.  I found the nvidia driver on Restricted Drivers.  I chose the recommended one.  I'll take a look at Xorg.conf in a minute and learn how to use it.  Thanks!:)

---

