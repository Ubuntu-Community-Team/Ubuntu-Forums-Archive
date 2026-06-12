---
title: "Restore GDM as my desktop manager?"
date: 2009-02-28
forum: New to Ubuntu
---

### Post by nachos99 on 2009-02-28
how do i go about restoring GDM as my default/active/running desktop manager?

my deskmanager got switched to KD something after installing superkaramba, and after uninstalling it, GDM is still not running.

i did something in the terminal and was able to access GDM, but after restart, GDM is not running again.

thanks for any tips.

---

### Post by Xiong Chiamiov on 2009-02-28
```

sudo dpkg-reconfigure gdm

```
Tell it you want gdm as the default.

---

### Post by newbee70 on 2009-02-28
> **nachos99 said:**
> how do i go about restoring GDM as my default/active/running desktop manager?

my deskmanager got switched to KD something after installing superkaramba, and after uninstalling it, GDM is still not running.

i did something in the terminal and was able to access GDM, but after restart, GDM is not running again.

thanks for any tips.

Why have you opened a second thread on the same issue? 

you started one not 2 minutes prior to this one.

---

### Post by nachos99 on 2009-02-28
actually i started a thread hours ago asking about getting back into gnome desktop.

that specific problem is now solved i guess with me being able to access GUI.

and now im asking about a desktop management issue.  sorry for the related semi double post, but i thought it was a different question. i probably shouldnt have mentioned the the GDM issue in the later posts in the other thread.

---

### Post by kansasnoob on 2009-02-28
> **Xiong Chiamiov said:**
> ```

sudo dpkg-reconfigure gdm

```
Tell it you want gdm as the default.

That should do it!

---

### Post by nachos99 on 2009-02-28
im getting

~$ sudo dpkg-reconfigure gdm
 * Reloading GNOME Display Manager configuration...                              * Changes will take effect when all current X sessions have ended.
invoke-rc.d: initscript gdm, action "reload" failed.

---

### Post by taurus on 2009-02-28
Do you have gdm in /etc/init.d?

```
ls -la /etc/init.d
```

---

### Post by nachos99 on 2009-02-28
im getting

:~$ ls -la /etc/init.d
total 456
drwxr-xr-x   2 root root  4096 2009-02-28 04:31 .
drwxr-xr-x 130 root root 12288 2009-02-28 19:51 ..
-rwxr-xr-x   1 root root  2710 2008-04-18 21:19 acpid
-rwxr-xr-x   1 root root   762 2007-08-30 19:48 acpi-support
-rwxr-xr-x   1 root root  9708 2008-02-27 05:22 alsa-utils
-rwxr-xr-x   1 root root  1084 2008-08-01 06:43 anacron
-rwxr-xr-x   1 root root  1667 2007-05-23 05:59 apmd
-rwxr-xr-x   1 root root  2653 2008-05-02 13:41 apparmor
-rwxr-xr-x   1 root root  2181 2008-05-17 03:54 apport
-rwxr-xr-x   1 root root   969 2007-02-20 05:41 atd
-rwxr-xr-x   1 root root  2594 2008-12-18 10:33 avahi-daemon
-rwxr-xr-x   1 root root  1109 2005-10-27 05:15 binfmt-support
-rwxr-xr-x   1 root root  6609 2008-04-21 00:34 bluetooth
-rwxr-xr-x   1 root root  3597 2008-04-18 22:05 bootclean
-rwxr-xr-x   1 root root  2121 2008-04-18 22:05 bootlogd
-rwxr-xr-x   1 root root  1768 2008-04-18 22:05 bootmisc.sh
-rwxr-xr-x   1 root root  1795 2008-03-27 16:23 brltty
-rwxr-xr-x   1 root root  3304 2009-02-27 19:51 btnx
-rwxr-xr-x   1 root root  3454 2008-04-18 22:05 checkfs.sh
-rwxr-xr-x   1 root root 10602 2008-04-18 22:05 checkroot.sh
-rwxr-xr-x   1 root root  6355 2007-05-30 05:29 console-screen.sh
-rwxr-xr-x   1 root root  1634 2008-01-28 09:49 console-setup
-rwxr-xr-x   1 root root  1761 2008-04-08 11:02 cron
-rwxr-xr-x   1 root root  2287 2009-01-09 10:19 cupsys
-rwxr-xr-x   1 root root  4546 2008-10-14 11:30 dbus
-rwxr-xr-x   1 root root  1506 2007-10-23 07:34 dhcdbd
-rwxr-xr-x   1 root root  5647 2008-03-27 09:24 dkms_autoinstaller
-rwxr-xr-x   1 root root  1223 2007-06-21 21:55 dns-clean
-rwxr-xr-x   1 root root  3134 2008-07-17 12:12 gdm
-rwxr-xr-x   1 root root  7195 2008-04-04 16:38 glibc.sh
-rwxr-xr-x   1 root root  2301 2008-07-22 08:58 hal
-rwxr-xr-x   1 root root  1228 2008-04-18 22:05 halt
-rwxr-xr-x   1 root root   909 2008-04-18 22:05 hostname.sh
-rwxr-xr-x   1 root root  3576 2008-04-10 09:49 hotkey-setup
-rwxr-xr-x   1 root root  4528 2008-04-14 20:36 hwclockfirst.sh
-rwxr-xr-x   1 root root  4521 2008-04-14 20:36 hwclock.sh
-rwxr-xr-x   1 root root  1456 2007-03-21 15:59 inetutils-inetd
-rwxr-xr-x   1 root root  5968 2008-04-09 10:44 kdm-kde4
-rwxr-xr-x   1 root root  1376 2008-01-28 09:49 keyboard-setup
-rwxr-xr-x   1 root root   944 2008-04-18 22:05 killprocs
-rwxr-xr-x   1 root root  1729 2007-11-23 01:06 klogd
-rwxr-xr-x   1 root root  2308 2007-12-11 15:00 laptop-mode
-rwxr-xr-x   1 root root   349 2008-07-10 16:05 linux-restricted-modules-common
-rwxr-xr-x   1 root root   748 2006-01-23 10:47 loopback
-rwxr-xr-x   1 root root  1399 2008-02-25 13:20 module-init-tools
-rwxr-xr-x   1 root root   596 2008-04-18 22:05 mountall-bootclean.sh
-rwxr-xr-x   1 root root  2430 2008-04-18 22:05 mountall.sh
-rwxr-xr-x   1 root root  1465 2008-04-18 22:05 mountdevsubfs.sh
-rwxr-xr-x   1 root root  1544 2008-04-18 22:05 mountkernfs.sh
-rwxr-xr-x   1 root root   594 2008-04-18 22:05 mountnfs-bootclean.sh
-rwxr-xr-x   1 root root  1244 2008-04-18 22:05 mountoverflowtmp
-rwxr-xr-x   1 root root  3123 2008-04-18 22:05 mtab.sh
-rwxr-xr-x   1 root root  1772 2007-12-03 12:50 networking
-rwxr-xr-x   1 root root   860 2007-11-21 10:31 nvidia-kernel
-rwxr-xr-x   1 root root  2377 2007-10-23 10:03 pcmciautils
-rwxr-xr-x   1 root root   693 2008-04-18 21:42 policykit
-rwxr-xr-x   1 root root  4721 2008-03-08 16:24 powernowd
-rwxr-xr-x   1 root root   177 2008-03-08 16:24 powernowd.early
-rwxr-xr-x   1 root root   375 2007-10-04 12:56 pppd-dns
-rwxr-xr-x   1 root root  1261 2008-03-13 15:24 procps
-rwxr-xr-x   1 root root  1793 2008-04-06 18:18 pulseaudio
-rwxr-xr-x   1 root root  7891 2009-01-23 07:01 rc
-rwxr-xr-x   1 root root   522 2009-01-23 07:01 rc.local
-rwxr-xr-x   1 root root   117 2009-01-23 07:01 rcS
-rwxr-xr-x   1 root root  1492 2009-01-19 22:56 readahead
-rwxr-xr-x   1 root root  1957 2009-01-19 22:56 readahead-desktop
-rw-r--r--   1 root root  1335 2009-01-23 07:01 README
-rwxr-xr-x   1 root root   692 2008-04-18 22:05 reboot
-rwxr-xr-x   1 root root  1000 2008-04-18 22:05 rmnologin
-rwxr-xr-x   1 root root  4945 2008-04-10 17:12 rsync
-rwxr-xr-x   1 root root   955 2007-10-23 09:01 screen-cleanup
-rwxr-xr-x   1 root root  1199 2008-04-18 22:05 sendsigs
-rwxr-xr-x   1 root root   585 2008-04-18 22:05 single
-rwxr-xr-x   1 root root  4215 2009-01-23 07:01 skeleton
-rwxr-xr-x   1 root root   510 2008-04-18 22:05 stop-bootlogd
-rwxr-xr-x   1 root root   647 2008-04-18 22:05 stop-bootlogd-single
-rwxr-xr-x   1 root root   864 2009-01-19 22:56 stop-readahead
-rwxr-xr-x   1 root root  3343 2007-11-23 01:06 sysklogd
-rwxr-xr-x   1 root root  2488 2008-04-11 05:21 udev
-rwxr-xr-x   1 root root   706 2008-04-11 05:21 udev-finish
-rwxr-xr-x   1 root root  7239 2009-01-20 04:51 ufw
-rwxr-xr-x   1 root root  4030 2008-04-18 22:05 umountfs
-rwxr-xr-x   1 root root  1833 2008-04-18 22:05 umountnfs.sh
-rwxr-xr-x   1 root root  1863 2008-04-18 22:05 umountroot
-rwxr-xr-x   1 root root  1815 2008-04-18 22:05 urandom
-rwxr-xr-x   1 root root  2814 2007-10-15 02:20 usplash
-rwxr-xr-x   1 root root   820 2009-01-15 05:30 vbesave
-rwxr-xr-x   1 root root  9570 2009-02-16 13:56 vboxdrv
-rwxr-xr-x   1 root root  2445 2008-04-18 22:05 waitnfs.sh
-rwxr-xr-x   1 root root  1224 2008-10-10 09:45 winbind
-rwxr-xr-x   1 root root  1626 2008-03-12 14:27 wpa-ifupdown
-rwxr-xr-x   1 root root  1843 2008-05-13 17:10 x11-common
-rwxr-xr-x   1 root root   568 2008-03-29 22:41 xserver-xorg-input-wacom

---

### Post by taurus on 2009-02-28
What happens when you run

```
sudo /etc/init.d/gdm start
```

---

### Post by nachos99 on 2009-02-28
looks like problem is solved.  thank you everyone.

i ran $sudo apt-get purge kdelibs5 in terminal, removed everything that still remained anything kdelib... with package manager, retyped seemingly all the suggested terminal commands from you all and my GDM is running again as default.

i wish i had done it a little more methodically since im not exactly sure what the key was.  

hopefully the problem doesnt pop back up in a few hours.

---

