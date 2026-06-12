---
title: "vga=789 is deprecated?"
date: 2010-09-26
forum: New to Ubuntu
---

### Post by hcs7dap on 2010-09-26
Hi people,

I am running Karmic and consider myself a bit of a noob.

When I boot, there is a strange message that starts "vga=789 is deprecated..." it only appears on screen for a second before the rest of the boot sequence continues.

I haven't noticed any problems with the display (assuming the vga refers to that) or indeed any other problems.

Should I get over it and stop worrying over nothing? or does anyone have any suggestions as to what this means and if there is a fix?

Thanks for reading, Dave

---

### Post by kerry_s on 2010-09-26
did you add that to your boot line?
is this a clean install?

---

### Post by hcs7dap on 2010-09-26
Yes, I downloaded the iso file and installed from a CD. I have accepted all the recommended updates.

I haven't (to my knowledge) added anything to the boot line

---

### Post by hcs7dap on 2010-09-27
bump

---

### Post by andrewthomas on 2010-09-27
post the output of 

```
cat /etc/default/grub
```

---

### Post by hcs7dap on 2010-09-27
hcs7dap@SamandDaveslaptop:~$ cat /etc/default/grub
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=1
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=\\\"Linux\\\""
GRUB_CMDLINE_LINUX=" splash vga=769"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entrys
#GRUB_DISABLE_LINUX_RECOVERY="true"

---

### Post by andrewthomas on 2010-09-27
> **hcs7dap said:**
> 

GRUB_CMDLINE_LINUX=" splash vga=769"

change the above line to 
```

GRUB_CMDLINE_LINUX=""
```

---

### Post by hcs7dap on 2010-09-27
Thanks for your reply.

Sorry to be a pain... please can you give me explicit instructions on how to edit the grub file.

Cheers, Dave

---

### Post by andrewthomas on 2010-09-27
enter 
```
gksu gedit /etc/default/grub
```in the terminal

---

### Post by hcs7dap on 2010-09-27
many thanks for your help

---

### Post by andrewthomas on 2010-09-27
You're welcome.

---

