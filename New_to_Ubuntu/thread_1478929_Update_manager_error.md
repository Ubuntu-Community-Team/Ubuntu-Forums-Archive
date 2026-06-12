---
title: "Update manager error"
date: 2010-05-10
forum: New to Ubuntu
---

### Post by betterthanjordan79 on 2010-05-10
I keep getting an error every time I install a program or a program updates. I think its something to do with the Kernal updating.

Heres the error i get from update manager.

> E: linux-image-2.6.32-22-generic: subprocess installed post-installation script returned error exit status 127
E: grub-pc: subprocess installed post-installation script returned error exit status 127
E: linux-image-generic: dependency problems - leaving unconfigured
E: linux-generic: dependency problems - leaving unconfigured


heres a picture of the terminal also

[IMG]http://i40.tinypic.com/2hz06qv.png[/IMG]

thanks in advanced for all help!!

Daniel

---

### Post by Sealbhach on 2010-05-10
Looks like you have broken packages. If I were you I would boot into recovery mode and select the option to repair broken packages.

.

---

### Post by betterthanjordan79 on 2010-05-10
ok i will try that but how do i access the recovery mode. I remember in older versions u pressed esc when it asked you to when its booting but i cant see that menu anymore...thanks for your input Sealbhach

---

### Post by Sealbhach on 2010-05-11
> **betterthanjordan79 said:**
> ok i will try that but how do i access the recovery mode. I remember in older versions u pressed esc when it asked you to when its booting but i cant see that menu anymore...thanks for your input Sealbhach

That option will be in your Grub boot menu.

.

---

### Post by Silent Warrior on 2010-05-11
Hold down the right Shift-button as you start the computer - the menu is hidden by default, probably to save boot-up time. Well, hidden if you have only one OS, anyway.

---

### Post by betterthanjordan79 on 2010-05-13
ok i tried this but it didnt fix anythin...anyone else have any ideas...

---

### Post by mhgsys on 2010-05-13
can you open up a terminal and type; 

```
sudo dpkg --configure -a
```

---

### Post by betterthanjordan79 on 2010-05-13
i got this error
> daniel@daniel-laptop:~$ sudo dpkg --configure -a
Setting up grub-pc (1.98-1ubuntu6) ...
/etc/default/grub: 1: x#: not found
dpkg: error processing grub-pc (--configure):
 subprocess installed post-installation script returned error exit status 127
Setting up linux-image-2.6.32-22-generic (2.6.32-22.33) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.32-22-generic
Running postinst hook script /usr/sbin/update-grub.
/etc/default/grub: 1: x#: not found
User postinst hook script [/usr/sbin/update-grub] exited with value 127
dpkg: error processing linux-image-2.6.32-22-generic (--configure):
 subprocess installed post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.32-22-generic; however:
  Package linux-image-2.6.32-22-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.32.22.23); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 grub-pc
 linux-image-2.6.32-22-generic
 linux-image-generic
 linux-generic
daniel@daniel-laptop:~$ 

---

### Post by mhgsys on 2010-05-13
open up a terminal type
```
gedit /etc/default/grub
```

post output

---

### Post by betterthanjordan79 on 2010-05-13
this opens
> x# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset video=uvesafb:mode_option=1280x1024-24,mtrr=3,scroll=ywrap"
GRUB_CMDLINE_LINUX=" splash vga=769"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=1280x1024

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"


---

### Post by mhgsys on 2010-05-13
Nice; 
Close it again. 

open up the terminal again
type;
```
gksudo gedit /etc/default/grub
```
(now you can edit the file.

remove the x from line one ; 

so 
x# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

becomes 

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

Save the file.
Done.
This should fix your error

EDIT: After doing that; run 
```
sudo dpkg --configure -a
```
in terminal again.

Updating in update manager or terminal should work again.

---

### Post by betterthanjordan79 on 2010-05-13
thanks a million mhgsys!!!that worked perfect!!!

---

### Post by mhgsys on 2010-05-13
You're  Welcome; I wonder how that x came in there in the first place; :-)
Anyway;

Please mark you thread as solved.
(Go to thread tools > Mark this thread as solved)

---

### Post by dreamsR4living on 2010-07-16
I have the exact same problem as betterthanjordan79, but in my etc/default/grub there is no x showing up. Everyting is looking entirely normal:

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT=”quiet splash nomodeset video=uvesafb:mode_option=1280×1024-24,mtrr=3,scroll=ywrap”
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=1280×1024

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```

Does anyone have an idea to fix this?

---

