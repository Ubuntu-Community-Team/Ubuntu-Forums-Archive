---
title: "grub-reboot doesn't work - GRUB 2"
date: 2010-07-13
forum: New to Ubuntu
---

### Post by MiniMe on 2010-07-13
Hello,

I'm using a clean Ubuntu 10.04 64-bit install so therefore I assume I'm using GRUB 2.

The command 'sudo grub-reboot x' (where x is the menu entry position) doesn't seem to work. The first grub entry is always selected upon reboot.

I've edited /etc/default/grub to have "GRUB_DEFAULT=saved" as per the documentation to have grub-reboot command enabled.

This command was working for me before so perhaps it has something to do with a recent update? My current kernel version is "2.6.32-23-generic"

Any help would be appreciated. Thank you in advance.

In case it helps, my /etc/default/grub file contains the following:

```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=saved
#GRUB_DEFAULT=0
#GRUB_SAVEDEFAULT=false
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=" splash"

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

```

---

### Post by wojox on 2010-07-13
Did you update grub after all your changes?

```
sudo update-grub
```

---

### Post by MiniMe on 2010-07-13
Thank you! This has done the trick.

---

### Post by Fabioamd87 on 2010-12-18
I've the same problem and update-grub doesn't work...

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=saved
#GRUB_HIDDEN_TIMEOUT=5
#GRUB_HIDDEN_TIMEOUT_QUIET=false
#GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
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
```

```
fabio@hp:~$ sudo update-grub

Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-23-generic
Found initrd image: /boot/initrd.img-2.6.35-23-generic
Found Windows 7 (loader) on /dev/sda1
done
fabio@hp:~$ 

```

```
fabio@hp:~$ sudo grub-reboot 3
fabio@hp:~$ 

```

nothing happen...

---

### Post by Cue2 on 2011-08-17
I know this is an old thread but for anybody who stumbles upon this thread facing the same problem as Fabio. grub-reboot does not actually reboot the system. It only sets what to boot if you were to actually reboot the system. So I think what you are looking for is 
```

sudo grub-reboot x
sudo reboot
```

---

