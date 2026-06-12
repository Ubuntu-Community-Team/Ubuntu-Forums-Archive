---
title: "Kernel Update Grub Not Found"
date: 2010-11-26
forum: New to Ubuntu
---

### Post by armoftheland on 2010-11-26
Hi everyone,

For the past few months I have been going crazy because my updates wont complete. It looks like an issue moving over to a new kernel, but the issue seems to be with finding my grub file. I've looked over my grub file and as far as I can tell everything looks fine. But the same happens when I try to update grub:


> armoftheland@armoftheland-laptop:~$ sudo update-grub
/etc/default/grub: 1: dy6#: not found

Here's my grub file (which I have not altered in any way) 

> dy6# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi.power_nocheck"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"


Is this indeed the issue with updating?

HELP!!!!

---

### Post by Rubi1200 on 2010-11-26
We need to know which version you are running and which kernel you compiled (assuming that is what you did).

There seems to be an issue with GRUB, evidenced by the error message.

It would also really help us if you could run the boot info script linked at the bottom of my post (instructions included).

Copy/paste the results from the text that is generated and post it back here so we can see what is where.

Thanks.

---

### Post by sikander3786 on 2010-11-26
The issue lies here.

> dy6# If you change this file, run 'update-grub' afterwards to update

I don't know from where that **dy6#** came in but it is not supposed to be here.

Edit /etc/default/grub by,

```
gksudo gedit /etc/default/grub
```

Edit this line and remove dy6, don't remove #,

```
dy6# If you change this file, run 'update-grub' afterwards to update
```

So that it looks like,

```
# If you change this file, run 'update-grub' afterwards to update
```

And now update-grub,

```
sudo update-grub
```

If the errors persist, you definitely need to post the output of bootinfoscript as **Rubi** mentioned above.

Good Luck!

---

### Post by armoftheland on 2010-11-27
Sikander is the hero. I have no idea why that's in there but I removed it and I can update again!

THANK YOU! Something so simple really made my computer so much better :)

---

