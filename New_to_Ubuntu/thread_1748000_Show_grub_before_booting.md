---
title: "Show grub before booting"
date: 2011-05-03
forum: New to Ubuntu
---

### Post by RobikShrestha on 2011-05-03
My grub does not show up before booting. (Ubuntu 11.04)
How do I display the grub menu??

/etc/default/grub is:

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

---

### Post by matt_symes on 2011-05-03
Hi

Try pressing the shift key at PC start up just after the POST test. That should display your grub menu.

How many kernels do you have installed ? Grub will not be displayed by default if you only have one kernel or if there is no other operating systems on your PC.

Kind regards

---

### Post by RobikShrestha on 2011-05-03
I have ubutnu only

---

### Post by matt_symes on 2011-05-03
Hi

Did you try pressing the shift key at start up ?

Boot into your installation, open a terminal and type

```
ls /boot
```

Post the results back here.

Kind regards

---

### Post by RobikShrestha on 2011-05-03
Yes shift worked
I do not have windows but will install it i.e. I have already got ubuntu then I am going to install windows. I think I will use supergrub to recover back the grub. Or, is there a way to prevent windows from replacing MBR with its own "boot loader??" (I do not know what it is called).


ls /boot 
Results:

abi-2.6.38-8-generic         memtest86+_multiboot.bin
config-2.6.38-8-generic      System.map-2.6.38-8-generic
grub                         vmcoreinfo-2.6.38-8-generic
initrd.img-2.6.38-8-generic  vmlinuz-2.6.38-8-generic
memtest86+.bin

---

### Post by matt_symes on 2011-05-03
Hi

> **RobikShrestha said:**
> Yes shift worked

Good :D

> 
```
ls /boot 
Results:

abi-2.6.38-8-generic         memtest86+_multiboot.bin
config-2.6.38-8-generic      System.map-2.6.38-8-generic
grub                         vmcoreinfo-2.6.38-8-generic
initrd.img-2.6.38-8-generic  **vmlinuz-2.6.38-8-generic**
memtest86+.bin
```

Grub is defaulted not to display the menu if you only have one kernel installed. You only have one kernel installed at the moment.

> I do not have windows but will install it i.e. I have already got ubuntu then I am going to install windows. I think I will use supergrub to recover back the grub. Or, is there a way to prevent windows from replacing MBR with its own "boot loader??" (I do not know what it is called).

Windows will override the bootloader with its own bootloader. There is no way around this as far as i am aware. It is best to install windows first.

You could just reinstall grub from the liveCD.

[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

Kind regards

---

### Post by RobikShrestha on 2011-05-03
Thank you

---

