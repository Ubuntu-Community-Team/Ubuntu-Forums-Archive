---
title: "How to hide GRUB2 Menu"
date: 2010-10-24
forum: New to Ubuntu
---

### Post by karthick87 on 2010-10-24
I want to hide the GRUB2 Menu,like when i press the ESC Key the menu should be visible...I have done it in the previous version of ubuntu,but in ubuntu 10.04 i dont find the way..Can anyone help..?

---

### Post by Quackers on 2010-10-24
If you only have one operating system installed open up a terminal and type

```
sudo gedit /etc/default/grub
```

It will ask for your password, then a screen will open up with your file for editing.
Look for the line

```
GRUB_HIDDEN_TIMEOUT=0
```

Does it have a # in front of it?

This is from drs305's guide

```
GRUB_HIDDEN_TIMEOUT=0 [ Note: This setting only applies to computers with only a single operating system. ]

    * The hidden timeout option allows a screen to be displayed without the Grub 2 menu, awaiting input from the user for a given number of seconds. It is available to single-OS computers - if multiple OS's are known to Grub 2, this option is bypassed.
      On single-OS computers:
          o The menu will be hidden unless the user adds a # symbol to the beginning of this line ( # GRUB_HIDDEN_TIMEOUT=0 ) and the GRUB_TIMEOUT value is greater than 0.
```

---

### Post by karthick87 on 2010-10-24
Still its not working,this is my file


```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
#GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="ipv6.disable=1"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```

---

### Post by Rubi1200 on 2010-10-24
Did you run ```
sudo update-grub
``` after editing the file?

---

### Post by Quackers on 2010-10-24
If you took the # away you need to run sudo update-grub afterwards.

Edit, oops I was slow there :-)

---

### Post by karthick87 on 2010-10-24
Yes but still the menu is visible,

```
karthick@Ubuntu-desktop:~$ sudo update-grub 
Generating grub.cfg ...
Found background image: Linux-Mint-SysLinux-Splash.png
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found Microsoft Windows XP Professional on /dev/sda1
done
```

---

### Post by Rubi1200 on 2010-10-25
The menu is visible because you have more than 1 operating system:
> **GRUB_HIDDEN_TIMEOUT=0**   [ [COLOR=DarkRed]Note: This setting only applies to computers with only a single operating system.[/COLOR] ]The  hidden timeout option allows a screen to be displayed without the Grub 2  menu, awaiting input from the user for a given number of seconds. It is  available to single-OS computers - if multiple OS's are known to Grub  2, this option is bypassed. 
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

