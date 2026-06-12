---
title: "Can't restart cups"
date: 2008-12-16
forum: New to Ubuntu
---

### Post by Swerve1000 on 2008-12-16
Hi, I am using 8.10 Desktop x86

I am trying to install my Lexmark 1100 printer following the instructions in this guide:

[https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkMultifuncPrinters](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkMultifuncPrinters)



Everything has gone fine and when I enter:
```

/usr/lib/cups/backend/z600

```
It does indeed say:

```
direct z600:/dev/usblp0 "Lexmark  Lexmark X1100 Series" "Lexmark Printer"
```

So according to the guide, the driver is now installed.

But when I enter:

```
sudo /etc/init.d/cupsys restart
```

It fails, saying:
```

sudo: /etc/init.d/cupsys: command not found
```

XXXXX@XXXXX-desktop:/etc/init.d$ ls

Shows these :

```

acpid                            mountoverflowtmp
acpi-support                     mtab.sh
alsa-utils                       networking
anacron                          NetworkManager
apmd                             pcmciautils
apparmor                         policykit
apport                           powernowd
atd                              powernowd.early
avahi-daemon                     pppd-dns
avgd                             procps
binfmt-support                   pulseaudio
bluetooth                        rc
bootlogd                         rc.local
bootmisc.sh                      rcS
brltty                           readahead
checkfs.sh                       readahead-desktop
checkroot.sh                     README
console-screen.kbd.sh            reboot
console-setup                    rmnologin
cron                             rsync
cups                             samba
dbus                             screen-cleanup
dns-clean                        sendsigs
firestarter                      single
gdm                              skeleton
glibc.sh                         stop-bootlogd
hal                              stop-bootlogd-single
halt                             stop-readahead
hostname.sh                      sysklogd
hotkey-setup                     system-tools-backends
hwclockfirst.sh                  udev
hwclock.sh                       udev-finish
keyboard-setup                   ufw
killprocs                        umountfs
klogd                            umountnfs.sh
laptop-mode                      umountroot
linux-restricted-modules-common  urandom
loopback                         usplash
module-init-tools                vbesave
mountall-bootclean.sh            vboxdrv
mountall.sh                      vboxnet
mountdevsubfs.sh                 wpa-ifupdown
mountkernfs.sh                   x11-common
mountnfs-bootclean.sh            xserver-xorg-input-wacom
mountnfs.sh

```

So I'm assuming the driver for the printer has installed, but I'm unable to restart cups.

How can I do that?

Many thanks for any help!

---

### Post by Nxion on 2008-12-16
> **Swerve1000 said:**
> Hi, I am using 8.10 Desktop x86

I am trying to install my Lexmark 1100 printer following the instructions in this guide:

[https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkMultifuncPrinters](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkMultifuncPrinters)



Everything has gone fine and when I enter:
```

/usr/lib/cups/backend/z600

```It does indeed say:

```
direct z600:/dev/usblp0 "Lexmark  Lexmark X1100 Series" "Lexmark Printer"
```So according to the guide, the driver is now installed.

But when I enter:

```
sudo /etc/init.d/cupsys restart
```It fails, saying:
```

sudo: /etc/init.d/cupsys: command not found
```XXXXX@XXXXX-desktop:/etc/init.d$ ls

Shows these :

```

acpid                            mountoverflowtmp
acpi-support                     mtab.sh
alsa-utils                       networking
anacron                          NetworkManager
apmd                             pcmciautils
apparmor                         policykit
apport                           powernowd
atd                              powernowd.early
avahi-daemon                     pppd-dns
avgd                             procps
binfmt-support                   pulseaudio
bluetooth                        rc
bootlogd                         rc.local
bootmisc.sh                      rcS
brltty                           readahead
checkfs.sh                       readahead-desktop
checkroot.sh                     README
console-screen.kbd.sh            reboot
console-setup                    rmnologin
cron                             rsync
cups                             samba
dbus                             screen-cleanup
dns-clean                        sendsigs
firestarter                      single
gdm                              skeleton
glibc.sh                         stop-bootlogd
hal                              stop-bootlogd-single
halt                             stop-readahead
hostname.sh                      sysklogd
hotkey-setup                     system-tools-backends
hwclockfirst.sh                  udev
hwclock.sh                       udev-finish
keyboard-setup                   ufw
killprocs                        umountfs
klogd                            umountnfs.sh
laptop-mode                      umountroot
linux-restricted-modules-common  urandom
loopback                         usplash
module-init-tools                vbesave
mountall-bootclean.sh            vboxdrv
mountall.sh                      vboxnet
mountdevsubfs.sh                 wpa-ifupdown
mountkernfs.sh                   x11-common
mountnfs-bootclean.sh            xserver-xorg-input-wacom
mountnfs.sh

```So I'm assuming the driver for the printer has installed, but I'm unable to restart cups.

How can I do that?

Many thanks for any help!

Try:

```
sudo service cups restart
```"sudo service cups restart" is the same as "sudo /etc/init.d/cups restart"

It is just easier to type :) This will work with every service you need to restart. This is a new feature in Intrepid. Hope it helps.

---

### Post by Swerve1000 on 2008-12-16
Worked!!

Thank you very much :)

---

### Post by Nxion on 2008-12-16
> **Swerve1000 said:**
> Worked!!

Thank you very much :)

Anytime :) 

Don't forget to make the thread as solved if all is well :)

---

