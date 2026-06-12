---
title: "Grub settings messed up after update"
date: 2011-07-23
forum: New to Ubuntu
---

### Post by OkosBokos on 2011-07-23
A few days ago, after an update I was required to reboot the computer and after that the Grub settings have been messed up. Before that, the default boot option was Windows XP. Now it boots Ubuntu, even though Windows XP is still shown as the default option in both Start Up Manager and Grub Customizer. I'm using Ubuntu 11.04.

---

### Post by lmarmisa on 2011-07-23
Open a terminal and type this command:

```

grep GRUB_DEFAULT /etc/default/grub 

```

If you get a result similar to this, Ubuntu will be your default option:

```

luis@UB1104ENG:~$ grep GRUB_DEFAULT /etc/default/grub 
GRUB_DEFAULT=0
luis@UB1104ENG:~$ 

```

---

### Post by OkosBokos on 2011-07-23
Grub_default=6, so that's probably Windows. But I don't understand why it keeps on booting Ubuntu as default.

---

### Post by thefasterblueone on 2011-07-23
Try:

```
sudo update-grub
```

---

### Post by lmarmisa on 2011-07-23
If a new version of the kernel was added, you will have to increase the number 6 ( probably to 8 ) and finally to run the command

```

sudo update-grub

```

---

### Post by OkosBokos on 2011-07-23
> **lmarmisa said:**
> If a new version of the kernel was added, you will have to increase the number 6 ( probably to 8 ) and finally to run the command

```

sudo update-grub

```

Nope, didn't work.

---

### Post by lmarmisa on 2011-07-23
Do you have more than one Linux operating system installed on your computer?.

---

### Post by OkosBokos on 2011-07-23
Just this one.

---

### Post by lmarmisa on 2011-07-23
I like to use the "saved" configuration for GRUB. This configuration maintains the last selected option of the GRUB menu as default until this option is changed by the user to a new one.

If you wish to use it, edit the file **/etc/default/grub**

```

gksudo gedit /etc/defalut/grub

```

and change the lines marked in blue:

```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

[COLOR="Blue"]GRUB_DEFAULT=saved
GRUB_SAVEDEFAULT=true[/COLOR]
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=5
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
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

```

Save & Quit.

Finally, type the command update-grub:

```

sudo update-grub

```

---

