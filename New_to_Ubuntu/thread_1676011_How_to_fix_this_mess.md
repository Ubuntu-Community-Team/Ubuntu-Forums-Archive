---
title: "How to fix this mess"
date: 2011-01-26
forum: New to Ubuntu
---

### Post by twinaxel on 2011-01-26
Would really appreciate your input on this mess.


etting up linux-image-2.6.32-28-generic-pae (2.6.32-28.55) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.32-28-generic-pae
Running postinst hook script /usr/sbin/update-grub.
/etc/default/grub: 18: Syntax error: newline unexpected
User postinst hook script [/usr/sbin/update-grub] exited with value 2
dpkg: error processing linux-image-2.6.32-28-generic-pae (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic-pae:
 linux-image-generic-pae depends on linux-image-2.6.32-28-generic-pae; however:
  Package linux-image-2.6.32-28-generic-pae is not configured yet.
dpkg: error processing linux-image-generic-pae (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic-pae:
 linux-generic-pae depends on linux-image-generic-pae (= 2.6.32.28.31); however:
  Package linux-image-generic-pae is not configured yet.
dpkg: error processing linux-generic-pae (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.32-28-generic-pae
 linux-image-generic-pae
 linux-generic-pae

---

### Post by wojox on 2011-01-26
Did you miss configure /etc/default/grub? Open it and post it up here to look at:

```
gksudo gedit /etc/default/grub
```

---

### Post by twinaxel on 2011-01-26
GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset video=uvesafb:mode_option=>>1024x768-24<<,mtrr=3,scroll=ywrap"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=>>1024x768-24<<

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

Also getting this in terminal Fontconfig error: "~/.fonts.conf", line 1: no element found

---

### Post by wojox on 2011-01-26
> **twinaxel said:**
> GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset video=uvesafb:mode_option=>>1024x768-24<<,mtrr=3,scroll=ywrap"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE

[COLOR="Blue"]Change this to[/COLOR]
# you can see them in real GRUB with the command `vbeinfo'
[COLOR="Red"]GRUB_GFXMODE=>>1024x768-24<<[/COLOR]
[COLOR="Blue"]GRUB_GFXMODE=1024x768x24[/COLOR]

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

Also getting this in terminal Fontconfig error: "~/.fonts.conf", line 1: no element found

Save and run:

```
sudo update-grub2
```

---

### Post by twinaxel on 2011-01-26
sudo update-grub2/ etc/default/grub: 18: Syntax error: newline unexpected

---

### Post by wojox on 2011-01-26
Did you try the usual:

```
sudo dpkg --configure -a
```

```
sudo apt-get -f install
```

---

### Post by twinaxel on 2011-01-27
Setting up linux-image-2.6.32-28-generic-pae (2.6.32-28.55) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.32-28-generic-pae
Running postinst hook script /usr/sbin/update-grub.
/etc/default/grub: 18: Syntax error: newline unexpected
User postinst hook script [/usr/sbin/update-grub] exited with value 2
dpkg: error processing linux-image-2.6.32-28-generic-pae (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic-pae:
 linux-image-generic-pae depends on linux-image-2.6.32-28-generic-pae; however:
  Package linux-image-2.6.32-28-generic-pae is not configured yet.
dpkg: error processing linux-image-generic-pae (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic-pae:
 linux-generic-pae depends on linux-image-generic-pae (= 2.6.32.28.31); however:
  Package linux-image-generic-pae is not configured yet.
dpkg: error processing linux-generic-pae (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.32-28-generic-pae
 linux-image-generic-pae
 linux-generic-pae
gizmo@gizmo-desktop:~$ .sudo apt-get -f install
No command '.sudo' found, did you mean:
 Command 'sudo' from package 'sudo' (main)
 Command 'sudo' from package 'sudo-ldap' (universe)
.sudo: command not found

---

### Post by adeee on 2011-01-27
> **twinaxel said:**
> 
gizmo@gizmo-desktop:~$ .sudo apt-get -f install
No command '.sudo' found, did you mean:
 Command 'sudo' from package 'sudo' (main)
 Command 'sudo' from package 'sudo-ldap' (universe)
.sudo: command not found

Please use this command 

sudo apt-get -f install.

see the first line i quote you just post fullstop before sudo.
correct it

---

