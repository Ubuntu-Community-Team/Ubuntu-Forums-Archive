---
title: "acpi=force in grub2 how to?"
date: 2009-12-07
forum: New to Ubuntu
---

### Post by SSzretter on 2009-12-07
I want to add acpi=force, but every reference I can find is modifying /boot/grub/grub.cfg

however, at the top of the file it says do not modify this file!

where would I add the acpi=force and what do I do next to re-generate the grub.cfg?

---

### Post by sisco311 on 2009-12-07
Edit the /etc/default/grub file:
```
 # If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT="10"
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="**acpi=force**"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console
...

```

then run:
```
sudo update-grub
```

[uhelp]community/Grub2[/uhelp]
[thread=1302743]Grub 2 - 5 Common Tasks[/thread]
[thread=1287602]Grub 2 Title Tweaks[/thread]
[thread=1195275]The Grub 2 Guide[/thread]

---

### Post by diesch on 2009-12-07
Add it to* GRUB_CMDLINE_LINUX* in */etc/default/grub*

See [https://help.ubuntu.com/community/Grub2]("https://help.ubuntu.com/community/Grub2#Configuring%20GRUB%202") for more about how to configure Grub2

---

### Post by SSzretter on 2009-12-07
it looks like according to the grub2 docs, you are supposed to add the acpi=force to "GRUB_CMDLINE_LINUX_DEFAULT", and in fact there might be a bug with GRUB_CMDLINE_LINUX.

If I want multiple parameters, is it space or command delimited?

acpi=force,apparmor=0
or
acpi=force apparmor=0

?

---

### Post by sisco311 on 2009-12-07
Just like in Grub Legacy, kernel parameters are space separeted.

i.e.
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=force apparmor=0"
```

---

### Post by Marvin Stodolsky on 2010-01-31
Fine!!
though only for global application to all bootups.

How can different bootup options be set for alternate bootups??
In particular, a choice between the default runlevel=2 and an alternate 
runlevel=3
is desirable.

---

