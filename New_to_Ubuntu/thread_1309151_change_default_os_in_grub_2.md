---
title: "change default os in grub 2"
date: 2009-11-01
forum: New to Ubuntu
---

### Post by Falc7 on 2009-11-01
I want to change the default OS in grub2, but i am having some trouble. I've been looking at this thread
[http://ubuntuforums.org/showthread.php?t=1308665](http://ubuntuforums.org/showthread.php?t=1308665)

But startup-manager dosen't work, and i get strange errors when i enter this code ```
sudo kate /etc/default/grub
```

Here are the errors 
```
Error: "/var/tmp/kdecache-jamie" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-jamie" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-jamie" is owned by uid 1000 instead of uid 0.
Error: "/tmp/ksocket-jamie" is owned by uid 1000 instead of uid 0.
kdeinit4: preparing to launch /usr/lib/libkdeinit4_klauncher.so
Error: "/tmp/ksocket-jamie" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-jamie" is owned by uid 1000 instead of uid 0.
kdeinit4: preparing to launch /usr/lib/libkdeinit4_kded4.so
Error: "/var/tmp/kdecache-jamie" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-jamie" is owned by uid 1000 instead of uid 0.
kdeinit4: preparing to launch /usr/lib/libkdeinit4_kbuildsycoca4.so
kbuildsycoca4 running...
Error: "/var/tmp/kdecache-jamie" is owned by uid 1000 instead of uid 0.
kdeinit4: preparing to launch /usr/lib/libkdeinit4_kbuildsycoca4.so
kbuildsycoca4 running...
Error: "/var/tmp/kdecache-jamie" is owned by uid 1000 instead of uid 0.
Error: "/var/tmp/kdecache-jamie" is owned by uid 1000 instead of uid 0.
kdeinit4: preparing to launch /usr/lib/libkdeinit4_kconf_update.so
Error: "/tmp/ksocket-jamie" is owned by uid 1000 instead of uid 0.
kdeinit4: preparing to launch /usr/lib/kde4/kio_file.so

```

Here is the file anyway
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

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
```

Can someone help me change the default OS?

Edit: Here is the output for ```
grep menuentry /boot/grub/grub.cfg
```

```
jamie@jamie-kubuntu:~$ grep menuentry /boot/grub/grub.cfg
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
menuentry "Ubuntu, Linux 2.6.31-13-generic" {
menuentry "Ubuntu, Linux 2.6.31-13-generic (recovery mode)" {
menuentry "Ubuntu, Linux 2.6.31-12-generic" {
menuentry "Ubuntu, Linux 2.6.31-12-generic (recovery mode)" {
menuentry "Memory test (memtest86+)" {
menuentry "Memory test (memtest86+, serial console 115200)" {
menuentry "Ubuntu, Linux 2.6.31-14-generic-pae (on /dev/sda1)" {
menuentry "Ubuntu, Linux 2.6.31-14-generic-pae (recovery mode) (on /dev/sda1)" {
menuentry "Windows 7 (loader) (on /dev/sda2)" {

```

I want to make ```
menuentry "Ubuntu, Linux 2.6.31-14-generic"
``` the default, but atm ```
menuentry "Ubuntu, Linux 2.6.31-14-generic-pae (on /dev/sda1)" {
``` is the default

---

### Post by 0cton on 2009-11-01
nvm that sorry I'll look into it.

---

