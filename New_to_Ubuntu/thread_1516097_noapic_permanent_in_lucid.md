---
title: "noapic permanent in lucid"
date: 2010-06-23
forum: New to Ubuntu
---

### Post by DarinB on 2010-06-23
how to make noapic permanent in lucid lynx.
Grub2.

---

### Post by Elfy on 2010-06-23
Try adding it to this line GRUB_CMDLINE_LINUX in grub

```
gksudo gedit /etc/default/grub
```

[https://help.ubuntu.com/community/Grub2#Configuring%20GRUB%202](https://help.ubuntu.com/community/Grub2#Configuring%20GRUB%202)

eg.

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash noapic"

After editing the file 

```
sudo update-grub
```

---

### Post by DarinB on 2010-06-23
will i need to do this every kernel upgrade or will it stay?

---

### Post by Elfy on 2010-06-23
As far as I know it will get picked up on kernel updates.

From what I read - that grub file is where the 00_header picks up it's initial settings.

---

### Post by DarinB on 2010-06-23
when i add the code the grub.cfg is empty?

---

### Post by plucky on 2010-06-23
> **DarinB said:**
> when i add the code the grub.cfg is empty?

Use ```
gksudo gedit /etc/default/grub
```


Good Luck

---

### Post by DarinB on 2010-06-23
do i add the line or add it to [I]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
[/I]

> # If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
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

---

### Post by plucky on 2010-06-23
Add it to GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"


so it looks like ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash noapic"
```

and then run ```
sudo update-grub
```

Good luck

---

### Post by DarinB on 2010-06-23
off the charts it works! i hope it stays that way.
thanks a lot.

---

