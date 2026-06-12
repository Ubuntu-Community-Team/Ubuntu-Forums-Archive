---
title: "No /proc/acpi/"
date: 2010-02-16
forum: New to Ubuntu
---

### Post by fslezak on 2010-02-16
I am trying to access the ACPI on a Kubuntu system. There is no /proc/acpi on my disk. Is there a way to make this or is my system doomed when it comes to ACPI?

---

### Post by kyenos on 2010-02-17
As in all dir's / files in /proc, this entry must be created by the current kernel in memory. /proc is a virtual file system, and is a "file system view" of the kernel that currently is running.

acpi generally is a BIOS thing, and is often not supported in older machines, even some new machines don't necessarily offer that much in the way of acpi information at runtime. 

That said, please provide details of the hardware and the kernel you are using.

---

### Post by fslezak on 2010-02-19
Ah... I am using a 2.6.24-23-generic kernel.

Funny, I have dual-boot and the ACPI on Ubuntu 8.04 worked fine (it was 2.6.24-24-generic)

---

### Post by Meneer Jansen on 2010-11-25
I have the same prob. on my laptop. Very irritating because now I do not know how much battery time I've left (because that needs acpi to work).

It's an oldie: Toshiba Tecra 8000.

---

### Post by marshmallow1304 on 2010-11-25
Several of the /proc directories will soon be deprecated anyway.  Try looking in /sys/class/power_supply/BAT0/ .

---

### Post by Meneer Jansen on 2010-11-26
Remark: **solved**! :popcorn:

Thanks for the reply and the info. However, I didn't have an */sys/class/power_supply* directoty either. I searched for BAT0 like this, so I thought for sure there was no BAT0 (and BAT and BAT1 etc.) on my system...:
```

sudo updatedb
locate BAT0
locate BAT

```

Then I had a look at *dmesg* and I saw a message that said "acpi not started" and the advice to set "force=acpi". I googled for that and te [solution]("http://ubuntuforums.org/showthread.php?t=1348427") appeared to be to add that option (as well as "pci=noacpi" for pcmcia) to */etc/defualt/grub*:
```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT="10"
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="**acpi=force pci=noacpi**"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console
...

```

(don't forget to run: "sudo update-grub" afterwards!). Now all the battery utilities work out of the box. But (strangely enough!) I still can't locate an "BAT1" after an 'updatedb'. The battery thingies appeared to be (after a reboot of course) in:
```

/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0A:00/power_supply/BAT1

```
which is a directory (doesn't locate look for dirs??).

Anyway: it all works again now (power off after shutdown etc.) :D

---

