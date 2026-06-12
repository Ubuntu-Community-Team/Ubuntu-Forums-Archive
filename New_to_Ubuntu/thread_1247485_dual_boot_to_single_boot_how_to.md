---
title: "dual boot to single boot how to"
date: 2009-08-23
forum: New to Ubuntu
---

### Post by azlinuxnb on 2009-08-23
LinuxNB would like to know how to go from a dual boot to single boot system. I have been dual booting XP and Ubuntu for about a year. I love linux and would now like to boot linux, install vmware and have xp in that. Is this possible without loosing all my xp and linux configurations, setting, documents, ect.?  Id like to try out some other linux distributions hence the VM. Any help would be greatly appreciated.:)

---

### Post by nhasian on 2009-08-23
i recommend backing up your data from the windowsxp system and then doing a fresh install inside the vm host in linux.  you wont be able to simply move the xp install from one computer to another.  heck you cant even replace your motherboard in windows without it crashing on you.

---

### Post by Codix121 on 2009-08-23
Open your grub,

```
sudo gedit /boot/grub/menu.lst
```
In terminal

Go up to the very top

and set:

Default: 0

Timeout: 0

Here is an example of mine:

```

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		0

```

Basically, Default sets 0 (your first option) as the default selection,
and timeout 0, means the seconds the grub menu is open, setting it to 0,
will let you automatically select your default without wait time.

I think this is what you were asking. :confused:

---

### Post by PFN on 2009-08-23
You can convert your current Windows installation to a virtual machine using VMware Converter with all your current configuration.([http://www.vmware.com/products/converter](http://www.vmware.com/products/converter))

This VM can be open with VMware Player or VMware Server installed on any Linux distro.
You can find a nice how-to here-
[http://www.howtoforge.com/vmware_converter_windows_linux](http://www.howtoforge.com/vmware_converter_windows_linux)

---

### Post by azlinuxnb on 2009-08-26
Thank you all for the information. I think I will go for the vm converter route. :)

---

### Post by Windows Nerd on 2009-08-26
Back up everything you need from your windows XP partition: documents, programs, ect. Then delete your Windows partition so that Linux is the only OS on the drive. Then install VMware for Xp, then move all of your programs and documents back.

Scott

---

