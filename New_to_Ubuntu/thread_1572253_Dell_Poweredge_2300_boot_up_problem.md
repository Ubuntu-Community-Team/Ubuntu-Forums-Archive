---
title: "Dell Poweredge 2300 boot up problem"
date: 2010-09-10
forum: New to Ubuntu
---

### Post by LimeyTX on 2010-09-10
Hi,

I have a Dell Power Edge 2300 and installed Ubuntu Server 10.04 on it.

When it finished booting, it restarted and now comes up with the following.

```

Gave up waiting for root device. Common problems:
 - Boot args (cat /proc/cmdline)
  - Check rootdelay= (did the system wait long enough?)
  - Check root= (did the system wait for the right device?)
 - Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/mapper/homenet-root does not exist. Dropping to a shell!

BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)

```



I started learning Linux earlier this year, i know most of the basics, but this is stumping me.

Can anyone help??


Limey
TX

---

### Post by sandyd on 2010-09-10
> **LimeyTX said:**
> Hi,

I have a Dell Power Edge 2300 and installed Ubuntu Server 10.04 on it.

When it finished booting, it restarted and now comes up with the following.

```

Gave up waiting for root device. Common problems:
 - Boot args (cat /proc/cmdline)
  - Check rootdelay= (did the system wait long enough?)
  - Check root= (did the system wait for the right device?)
 - Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/mapper/homenet-root does not exist. Dropping to a shell!

BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)

```

I started learning Linux earlier this year, i know most of the basics, but this is stumping me.

Can anyone help??


Limey
TX
make sure the grub boot entry is pointing at the right disk.
press shift as soon as the computer starts.
press "e" and take a pic of the output

---

