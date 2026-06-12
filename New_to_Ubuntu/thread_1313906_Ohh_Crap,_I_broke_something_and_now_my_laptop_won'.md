---
title: "Ohh Crap, I broke something and now my laptop won't boot!!!! Help!"
date: 2009-11-04
forum: New to Ubuntu
---

### Post by humphreybc on 2009-11-04
Ahh so I tried downloading and installing a new kernel, 2.6.32 rc5 and on the first time I rebooted with it, it seemed to work okay.

Then I restarted again and now I have problems. On boot with the new kernel, OR my other one (2.6.31-14-generic) I get the following error messages:

```

EXT4-fs error (device sda1): ext4_lookup: deleted inode referenced: 134962

mount: cannot remount block device /dev/sda1 read-write, is write-protected
mountall: mount / [1016] terminated with status 32
mountall: Filesystem could not be mounted: /
init: mountall main process (578) terminated with status 4
Mount of root filesystem failed.
A maintenance shell will now be started.
CONTROL-D will terminate this shell and reboot the system.
* Starting init crypto disks...
root@benjamin-laptop:~# cryptswap1 (starting)
init: upstart-udev-bridge main process (592) terminated with status 1
init: upstart-udev-bridge main process ended, respawning

... and it just goes on like that till it halts on:

* cryptswap1 (started)...                           [ OK ]


```

So yeah, I'm kinda screwed. How do I uninstall the new kernel I installed? I would do a simple apt-get remove but I don't know the full name of the package, it's fairly long.

HELP!

---

### Post by kyuubi777 on 2009-11-04
i had a kernel issue when i ubdated my system once using 9.04.. booted in recovery and told the system to repair files.. reboooted and all was fine

---

### Post by philinux on 2009-11-04
> **humphreybc said:**
> Ahh so I tried downloading and installing a new kernel, 2.6.32 rc5 and on the first time I rebooted with it, it seemed to work okay.

Then I restarted again and now I have problems. On boot with the new kernel, OR my other one (2.6.31-14-generic) I get the following error messages:

```

EXT4-fs error (device sda1): ext4_lookup: deleted inode referenced: 134962

mount: cannot remount block device /dev/sda1 read-write, is write-protected
mountall: mount / [1016] terminated with status 32
mountall: Filesystem could not be mounted: /
init: mountall main process (578) terminated with status 4
Mount of root filesystem failed.
A maintenance shell will now be started.
CONTROL-D will terminate this shell and reboot the system.
* Starting init crypto disks...
root@benjamin-laptop:~# cryptswap1 (starting)
init: upstart-udev-bridge main process (592) terminated with status 1
init: upstart-udev-bridge main process ended, respawning

... and it just goes on like that till it halts on:

* cryptswap1 (started)...                           [ OK ]


```

So yeah, I'm kinda screwed. How do I uninstall the new kernel I installed? I would do a simple apt-get remove but I don't know the full name of the package, it's fairly long.

HELP!

In this situation I would boot into recovery mode and fsck -v /dev/sda1 because of this error. 
EXT4-fs error (device sda1): ext4_lookup: deleted inode referenced: 134962
You might have to unmount sda1.

---

### Post by humphreybc on 2009-11-04
> **kyuubi777 said:**
> i had a kernel issue when i ubdated my system once using 9.04.. booted in recovery and told the system to repair files.. reboooted and all was fine

Recovery Console doesn't work :(

I'm resorting to a LiveCD to do any changes, hopefully I can remove the linux image I installed via the LiveCD.... if not... i'm screwed :S

---

### Post by humphreybc on 2009-11-04
> **philinux said:**
> In this situation I would boot into recovery mode and fsck -v /dev/sda1 because of this error. 
EXT4-fs error (device sda1): ext4_lookup: deleted inode referenced: 134962
You might have to unmount sda1.

Okay i will try to do that from the LiveCD. Recovery console doesn't really want to work which is a shame!

---

### Post by humphreybc on 2009-11-04
Oh yay, that fixed it!! Thanks a bunch!

Do you think you could give me a brief explanation of inodes, and what could have caused this to happen? Just so I know for the future.

---

### Post by philinux on 2009-11-04
Can you not boot the previous kernel from grub or the previous kernel recovery mode?

---

