---
title: "my nvidia settings??"
date: 2009-12-27
forum: New to Ubuntu
---

### Post by soryu on 2009-12-27
linux@linux-desktop:~$ nvidia-xconfig

Using X configuration file: "/etc/X11/xorg.conf".

WARNING: No Layout specified, constructing implicit layout section using screen
         "Default Screen".


WARNING: Unable to find CorePointer in X configuration; attempting to add new
         CorePointer section.


WARNING: The CorePointer device was not specified explicitly in the layout;
         using the first mouse device.


WARNING: Unable to find CoreKeyboard in X configuration; attempting to add new
         CoreKeyboard section.


WARNING: The CoreKeyboard device was not specified explicitly in the layout;
         using the first keyboard device.


ERROR: Unable to write to directory '/etc/X11'.

linux@linux-desktop:~$ 


how can i fix this?

---

### Post by Mrandersonjr on 2009-12-27
Try: 
sudo eselect opengl set nvidia

If it is unable to run because of a readonly file system or some sort of file system error,then in a terminal:
sudo su (to become root)

THEN ONCE YOU ARE ROOT
fsck -f -c -y /
once it is done,then run:
eselect opengl set nvidia

---

### Post by soryu on 2009-12-27
linux@linux-desktop:~$ sudo eselect opengl set nvidia
sudo: eselect: command not found
linux@linux-desktop:~$ sudo eselect opengl set nvidia
sudo: eselect: command not found
linux@linux-desktop:~$ sudo su
root@linux-desktop:/home/linux# fsck /
fsck from util-linux-ng 2.16
e2fsck 1.41.9 (22-Aug-2009)
/dev/sda1 is mounted.  

WARNING!!!  Running e2fsck on a mounted filesystem may cause
SEVERE filesystem damage.

Do you really want to continue (y/n)? no

check aborted.
root@linux-desktop:/home/linux# 
root@linux-desktop:/home/linux# eselect opengl set nvidia
No command 'eselect' found, did you mean:
 Command 'dselect' from package 'dselect' (main)
 Command 'qselect' from package 'gridengine-client' (universe)
 Command 'qselect' from package 'torque-client' (multiverse)
 Command 'iselect' from package 'iselect' (universe)
eselect: command not found
root@linux-desktop:/home/linux#

don't want to damage system.

---

### Post by marshmallow1304 on 2009-12-27
To be able to write to xorg.conf, nvidia-xconfig must be run as root, so
```
sudo nvidia-xconfig
```

---

### Post by soryu on 2009-12-28
linux@linux-desktop:~$ sudo nvidia-xconfig
[sudo] password for linux: 

Using X configuration file: "/etc/X11/xorg.conf".

WARNING: No Layout specified, constructing implicit layout section using screen
         "Default Screen".


WARNING: Unable to find CorePointer in X configuration; attempting to add new
         CorePointer section.


WARNING: The CorePointer device was not specified explicitly in the layout;
         using the first mouse device.


WARNING: Unable to find CoreKeyboard in X configuration; attempting to add new
         CoreKeyboard section.


WARNING: The CoreKeyboard device was not specified explicitly in the layout;
         using the first keyboard device.

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

linux@linux-desktop:~$ 


how do i write to xorg.conf? what do i need to change?

---

### Post by marshmallow1304 on 2009-12-28
> **soryu said:**
> ```
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'
```

how do i write to xorg.conf? what do i need to change?

It worked.  You'll notice you didn't receive

```
ERROR: Unable to write to directory '/etc/X11'.
```

A reboot will start you up with the new xorg.conf

---

### Post by ibuclaw on 2009-12-28
Hmm... was the question to **see** the nvidia settings, or **change** the nvidia settings?

That is not quite clear in the question.

---

### Post by soryu on 2009-12-31
linux@linux-desktop:~$ nvidia-xconfig

Using X configuration file: "/etc/X11/xorg.conf".

ERROR: Unable to write to directory '/etc/X11'.

linux@linux-desktop:~$ sudo nvidia-xconfig
[sudo] password for linux: 

Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

linux@linux-desktop:~$ 




to see and change if wrong.    
i dont know wrong or right??

---

### Post by themusicalduck on 2009-12-31
try ```
sudo nvidia-settings
```

You can change settings from there.

---

### Post by SuperSonic4 on 2009-12-31
> **soryu said:**
> 
linux@linux-desktop:~$ sudo nvidia-xconfig
[sudo] password for linux: 
[B]
Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'[/B]

linux@linux-desktop:~$ 




to see and change if wrong.    
i dont know wrong or right??

Bold bit indicates success

If there is an error after rebooting/restarting gdm then you'll need to tell us what you want

---

### Post by soryu on 2009-12-31
i tried the command and configured the X server settings.
i restarted my pc ,looked at the display conf. in the X serv.settings and they now show auto configuration,it didn't save the settings.

oddly enough my PC is now hibernating like it should:popcorn: bout time.:guitar:

---

