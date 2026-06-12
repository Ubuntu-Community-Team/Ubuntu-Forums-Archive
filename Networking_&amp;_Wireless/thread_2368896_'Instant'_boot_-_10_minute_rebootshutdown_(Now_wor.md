---
title: "'Instant' boot - 10 minute reboot/shutdown (Now working ok but no resolv.conf error)"
date: 2017-08-16
forum: Networking &amp; Wireless
---

### Post by makem2 on 2017-08-16
Just started yesterday for no apparent reason other than I was attempting to make a symlink for Chromium to a previously setup and working ramdisk. (Still not succeeded!)

Started grub recovery mode and checked all filesystems - no errors

Enable Networking - error:

grep: /etc/resolve.conf: No such file or directory
Trying to start NetworkManager.........
grep: /etc/resolve.conf: No such file or directory

After several attempts the system hangs.

Reboot is fine, networking operates normally.

Next went to check on resolv.conf:

```

makem@ssdTOSH:~$ cd /etc
makem@ssdTOSH:/etc$ ls -la
total 1440
drwxr-xr-x 157 root root     12288 Aug 16 10:16 .
drwxr-xr-x  27 root root      4096 Aug  4 11:33 ..
drwxr-xr-x   3 root root      4096 Sep 14  2016 acpi
-rw-r--r--   1 root root      2981 Feb 17  2016 adduser.conf
-rw-r--r--   1 root root        18 Sep 14  2016 adjtime
drwxr-xr-x   2 root root      4096 Jun  8  2016 akonadi
drwxr-xr-x   2 root root     16384 Aug 16 10:16 alternatives
-rw-r--r--   1 root root       401 Feb 20  2014 anacrontab
drwxr-xr-x   3 root root      4096 Sep 24  2016 apache2
drwxr-xr-x   6 root root      4096 Feb 17  2016 apm
drwxr-xr-x   3 root root      4096 Apr  2 17:16 apparmor
drwxr-xr-x   8 root root      4096 Aug  7 22:53 apparmor.d
drwxr-xr-x   5 root root      4096 Jul 21 22:02 apport
-rw-r--r--   1 root root       389 Apr 18  2016 appstream.conf
drwxr-xr-x   6 root root      4096 May 30 19:26 apt
-rw-r-----   1 root daemon     144 Oct 21  2013 at.deny
drwxr-xr-x   2 root root      4096 Sep 14  2016 at-spi2
drwxr-xr-x   3 root root      4096 Sep 14  2016 avahi
-rw-r--r--   1 root root      2188 Jun 24  2016 bash.bashrc
-rw-r--r--   1 root root        45 Mar 22  2014 bash_completion
drwxr-xr-x   2 root root      4096 Aug  2 00:48 bash_completion.d
-rw-r--r--   1 root root       367 Jan 27  2016 bindresvport.blacklist
drwxr-xr-x   2 root root      4096 Jul 12  2016 binfmt.d
drwxr-xr-x   2 root root      4096 Jul 18 20:01 bluetooth
drwxr-xr-x   2 root root      4096 Sep 14  2016 bonobo-activation
-rw-r--r--   1 root root        33 Feb 17  2016 brlapi.key
drwxr-xr-x   7 root root     12288 Sep 14  2016 brltty
-rw-r--r--   1 root root     23444 Apr 28  2016 brltty.conf
drwxr-xr-x   3 root root      4096 Feb 17  2016 ca-certificates
-rw-r--r--   1 root root      8669 Jun  8  2016 ca-certificates.conf
-rw-r--r--   1 root root      7773 Feb 17  2016 ca-certificates.conf.dpkg-old
drwxr-xr-x   2 root root      4096 Sep 14  2016 calendar
drwxr-s---   2 root dip       4096 Sep 14  2016 chatscripts
drwxr-xr-x   4 root root      4096 Aug 16 10:16 chromium-browser
drwxr-xr-x   5 root root      4096 Jun  8  2016 ConsoleKit
drwxr-xr-x   2 root root      4096 Feb 12  2017 console-setup
drwxr-xr-x   2 root root      4096 Jan 11  2017 cracklib
drwxr-xr-x   2 root root      4096 Sep 14  2016 cron.d
drwxr-xr-x   2 root root      4096 Aug  4 12:37 cron.daily
drwxr-xr-x   2 root root      4096 Sep 14  2016 cron.hourly
drwxr-xr-x   2 root root      4096 Sep 14  2016 cron.monthly
-rw-r--r--   1 root root       722 Feb  9  2013 crontab
drwxr-xr-x   2 root root      4096 Aug  7 22:53 cron.weekly
drwxr-xr-x   5 root lp        4096 Aug 16 17:21 cups
drwxr-xr-x   2 root root      4096 Sep 14  2016 cupshelpers
drwxr-xr-x   4 root root      4096 Jan 18  2017 dbus-1
-rw-r--r--   1 root root      2969 Feb 23  2014 debconf.conf
-rw-r--r--   1 root root        12 Apr 30  2015 debian_version
drwxr-xr-x   3 root root      4096 Aug 16 10:16 default
-rw-r--r--   1 root root       604 Nov  7  2013 deluser.conf
drwxr-xr-x   2 root root      4096 Aug  2 00:48 depmod.d
drwxr-xr-x   4 root root      4096 Jun  2 14:10 dhcp
drwxr-xr-x   2 root root      4096 Sep 14  2016 dictionaries-common
drwxr-xr-x   3 root root      4096 Nov  1  2016 dkms
drwxr-xr-x   2 root root      4096 Mar 11 19:00 dnsmasq.d
drwxr-xr-x   3 root root      4096 Feb 17  2016 doc-base
drwxr-xr-x   4 root root      4096 May  8 08:45 dpkg
-rw-r--r--   1 root root      4676 Jul  6 06:25 drirc
drwxr-xr-x   3 root root      4096 Sep 14  2016 emacs
-rw-r--r--   1 root root        96 Feb 17  2016 environment
drwxr-xr-x   2 root root      4096 Dec 11  2016 esound
drwxr-xr-x   2 root root      4096 Jun 18 23:12 firefox
drwxr-xr-x   4 root root      4096 Sep 14  2016 fonts
-rw-r--r--   1 root root      1237 Jul 17 23:21 fstab
-rw-r--r--   1 root root      1164 Jul 17 22:26 fstab.save
-rw-r--r--   1 root root      1024 Aug 16 01:28 .fstab.swp
-rw-r--r--   1 root fuse       280 May 24  2013 fuse.conf
-rw-r--r--   1 root root       331 Aug 17  2016 fwupd.conf
-rw-r--r--   1 root root      2584 Oct 10  2012 gai.conf
drwxr-xr-x   5 root root      4096 Feb 17  2016 gconf
drwxr-xr-x   2 root root      4096 Jul 27 13:59 gdb
drwxr-xr-x   4 root root      4096 Feb 17  2016 ghostscript
drwxr-xr-x   3 root root      4096 Feb 17  2016 gimp
drwxr-xr-x   2 root root      4096 Mar 11 19:00 gnome
drwxr-xr-x   2 root root      4096 Sep 14  2016 gnome-app-install
drwxr-xr-x   2 root root      4096 Sep 14  2016 gnome-system-tools
drwxr-xr-x   3 root root      4096 Jun  8  2016 gnome-vfs-2.0
drwxr-xr-x   2 root root      4096 Sep 14  2016 groff
-rw-r--r--   1 root root      1159 Aug  7 22:47 group
-rw-------   1 root root      1141 Jun  2 19:21 group-
drwxr-xr-x   2 root root      4096 Aug  2 00:48 grub.d
-rw-r-----   1 root shadow     969 Aug  7 22:47 gshadow
-rw-------   1 root root       954 Jun  2 19:21 gshadow-
drwxr-xr-x   3 root root      4096 Sep 14  2016 gss
drwxr-xr-x   2 root root      4096 Jul 12 12:14 gtk-2.0
drwxr-xr-x   2 root root      4096 Apr 27 05:59 gtk-3.0
drwxr-xr-x   2 root root      4096 Sep 14  2016 gtkmathview
drwxr-xr-x   2 root root      4096 Jul 29  2016 guest-session
drwxr-xr-x   3 root root      4096 Jun 27  2016 gufw
-rw-r--r--   1 root root      6748 Oct 29  2012 hddtemp.db
-rw-r--r--   1 root root      4781 Nov 15  2013 hdparm.conf
-rw-r--r--   1 root root        92 Feb 20  2014 host.conf
-rw-r--r--   1 root root         8 Jun  8  2016 hostname
-rw-r--r--   1 root root       222 Jun  8  2016 hosts
-rw-r--r--   1 root root       411 Feb 17  2016 hosts.allow
-rw-r--r--   1 root root       711 Feb 17  2016 hosts.deny
drwxr-xr-x   2 root root      4096 Sep 14  2016 hp
drwxr-xr-x   3 root root      4096 Feb 17  2016 ifplugd
drwxr-xr-x   2 root root      4096 Aug  2 00:48 ImageMagick-6
drwxr-xr-x   2 root root     12288 Aug  2 00:48 init
drwxr-xr-x   2 root root      4096 Aug  7 22:53 init.d
drwxr-xr-x   5 root root      4096 Jan 18  2017 initramfs-tools
-rw-r--r--   1 root root      1721 Mar 28  2014 inputrc
drwxr-xr-x   3 root root      4096 May 19  2013 insserv
-rw-r--r--   1 root root       771 May 19  2013 insserv.conf
drwxr-xr-x   2 root root      4096 May 19  2013 insserv.conf.d
-rw-r--r--   1 root root        71 Sep 30  2014 inxi.conf
drwxr-xr-x   2 root root      4096 May 26 14:52 iproute2
-rw-r--r--   1 root root        26 Jul 31 14:36 issue
-rw-r--r--   1 root root        19 Jul 31 14:36 issue.net
drwxr-xr-x   3 root root      4096 Jun  9  2016 .java
drwxr-xr-x   5 root root      4096 Sep 14  2016 java-7-openjdk
drwxr-xr-x   5 root root      4096 Aug  2 00:48 java-8-openjdk
drwxr-xr-x   2 root root      4096 Oct 14  2016 kbd
drwxr-xr-x   6 root root      4096 Sep 14  2016 kernel
-rw-r--r--   1 root root       110 Jun  8  2016 kernel-img.conf
-rw-r--r--   1 root root      1308 Mar 10  2016 kerneloops.conf
drwxr-xr-x   2 root root      4096 Jun  1 18:09 ldap
-rw-r--r--   1 root root    152672 Aug 16 10:16 ld.so.cache
-rw-r--r--   1 root root        34 Feb 17  2016 ld.so.conf
drwxr-xr-x   2 root root      4096 Jul  1 14:05 ld.so.conf.d
-rw-r--r--   1 root root        20 Sep 24  2016 ld.so.preload
-rw-r--r--   1 root root       267 Feb 20  2014 legal
-rw-r--r--   1 root root        27 Jan  8  2015 libao.conf
-rw-r--r--   1 root root       191 Dec  4  2013 libaudit.conf
drwxr-xr-x   2 root root      4096 Jun 11 21:55 libnl-3
drwxr-xr-x   2 root root      4096 Dec 11  2013 libpaper.d
drwxr-xr-x   2 root root      4096 May  8 08:47 libreoffice
-rw-r--r--   1 root root      2290 Feb 29  2012 libuser.conf
drwxr-xr-x   3 root root      4096 Apr  7 10:40 lightdm
drwxr-xr-x   4 root root      4096 Sep 24  2016 lighttpd
-rw-r--r--   1 root root      1151 Apr  8  2016 lintianrc
-rw-r--r--   1 root root      2995 Apr 14  2016 locale.alias
-rw-r--r--   1 root root      9149 Jul  1 14:05 locale.gen
lrwxrwxrwx   1 root root        33 Dec  8  2016 localtime -> /usr/share/zoneinfo/Europe/London
drwxr-xr-x   5 root root      4096 Sep 27  2016 logcheck
-rw-r--r--   1 root root     10551 Feb 17  2014 login.defs
-rw-r--r--   1 root root       703 Jan 22  2014 logrotate.conf
drwxr-xr-x   2 root root      4096 Aug  7 22:53 logrotate.d
-rw-r--r--   1 root root       105 Jul 31 14:36 lsb-release
-rw-r--r--   1 root root     14867 May 10  2014 ltrace.conf
-r--r--r--   1 root root        33 Sep 14  2016 machine-id
-rw-r--r--   1 root root       111 Apr  3  2014 magic
-rw-r--r--   1 root root       111 Apr  3  2014 magic.mime
-rw-r--r--   1 root root     53836 Aug 16 10:16 mailcap
-rw-r--r--   1 root root       449 May 13  2013 mailcap.order
-rw-r--r--   1 root root      5170 Nov  6  2015 manpath.config
drwxr-xr-x   2 root root      4096 Sep 14  2016 menu
drwxr-xr-x   2 root root      4096 Sep 14  2016 menu-methods
-rw-r--r--   1 root root     24241 Oct 30  2015 mime.types
-rw-r--r--   1 root root      4562 Feb 16 23:39 minidlna.conf
-rw-r--r--   1 root root       967 Oct 30  2015 mke2fs.conf
drwxr-xr-x   2 root root      4096 Aug  2 00:48 modprobe.d
-rw-r--r--   1 root root       198 Sep 14  2016 modules
drwxr-xr-x   2 root root      4096 Jul 25 12:37 modules-load.d
lrwxrwxrwx   1 root root        19 Sep 14  2016 mtab -> ../proc/self/mounts
-rw-------   1 root lightdm      0 Jun  8  2016 mtab.fuselock
-rw-r--r--   1 root root       624 Aug  8  2007 mtools.conf
drwxr-xr-x   4 root root      4096 Jul 21 22:02 mysql
-rw-r--r--   1 root root      1911 May 12  2015 nail.rc
-rw-r--r--   1 root root      8338 Mar 29  2016 nanorc
drwxr-xr-x   7 root root      4096 Sep 15  2016 network
drwxr-xr-x   8 root root      4096 Mar 11 19:00 NetworkManager
-rw-r--r--   1 root root        91 Feb 20  2014 networks
drwxr-xr-x   2 root root      4096 Sep 14  2016 newt
-rw-r--r--   1 root root       507 Feb 17  2016 nsswitch.conf
drwxr-xr-x   2 root root      4096 Sep 14  2016 obex-data-server
-rw-r--r--   1 root root         0 Dec 11  2013 odbc.ini
-rw-r--r--   1 root root         0 Jun  8  2016 odbcinst.ini
drwxr-xr-x   2 root root      4096 Sep 14  2016 openal
drwxr-xr-x   3 root root      4096 Sep 14  2016 OpenCL
drwxr-xr-x   2 root root      4096 Feb 17  2016 opt
lrwxrwxrwx   1 root root        21 Jul 31 14:36 os-release -> ../usr/lib/os-release
-rw-r--r--   1 root root       552 Jan 31  2014 pam.conf
drwxr-xr-x   2 root root      4096 Jul 27 13:59 pam.d
-rw-r--r--   1 root root         3 Jun  8  2016 papersize
-rw-r--r--   1 root root      2658 Aug  7 22:47 passwd
-rw-------   1 root root      2658 Aug  7 22:47 passwd-
drwxr-xr-x   2 root root      4096 Feb 17  2016 pcmcia
drwxr-xr-x   4 root root      4096 Sep 14  2016 perl
drwxr-xr-x   4 root root      4096 Sep 14  2016 pki
drwxr-xr-x   5 root root      4096 Feb 17  2016 pm
-rw-r--r--   1 root root      7649 Sep 14  2016 pnm2ppa.conf
drwxr-xr-x   5 root root      4096 Feb 17  2016 polkit-1
-rw-r--r--   1 root root       350 Jun  8  2016 popularity-contest.conf
drwxr-xr-x   8 root root      4096 Sep 14  2016 ppp
-rw-r--r--   1 root root         3 Sep 14  2016 prime-discrete
lrwxrwxrwx   1 root root        22 Sep 14  2016 printcap -> /var/run/cups/printcap
-rw-r--r--   1 root root       575 Oct 22  2015 profile
drwxr-xr-x   2 root root      4096 May 17 11:44 profile.d
-rw-r--r--   1 root root      2932 Dec 30  2013 protocols
drwxr-xr-x   2 root root      4096 Jul  1 14:05 pulse
drwxr-xr-x   2 root root      4096 Mar 16 14:45 purple
-rw-------   1 root root         0 Feb 17  2016 .pwd.lock
drwxr-xr-x   2 root root      4096 Feb 17  2016 python
drwxr-xr-x   2 root root      4096 Nov 29  2016 python2.7
drwxr-xr-x   2 root root      4096 Feb 17  2016 python3
drwxr-xr-x   2 root root      4096 Feb 17  2016 python3.4
drwxr-xr-x   2 root root      4096 Nov 29  2016 python3.5
-rw-r--r--   1 root root      1154 Aug 11  2015 rarfiles.lst
drwxr-xr-x   2 root root      4096 Aug  7 22:47 rc0.d
drwxr-xr-x   2 root root      4096 Aug  7 22:47 rc1.d
drwxr-xr-x   2 root root      4096 Aug  7 22:47 rc2.d
drwxr-xr-x   2 root root      4096 Aug  7 22:47 rc3.d
drwxr-xr-x   2 root root      4096 Aug  7 22:47 rc4.d
drwxr-xr-x   2 root root      4096 Aug  7 22:47 rc5.d
drwxr-xr-x   2 root root      4096 Aug  7 22:47 rc6.d
-rwxr-xr-x   1 root root       306 Feb 17  2016 rc.local
drwxr-xr-x   2 root root      4096 Jul  1 14:04 rcS.d
[COLOR=#000000]drwxr-xr-x   5 root root      4096 Mar  4 10:54 resolvconf[/COLOR]
[COLOR=#ff0000]lrwxrwxrwx   1 root root        29 Jun  8  2016 resolv.conf -> ../run/resolvconf/resolv.conf[/COLOR]
-rwxr-xr-x   1 root root       268 Feb  4  2014 rmt
-rw-r--r--   1 root root       887 Dec 30  2013 rpc
-rw-r--r--   1 root root      1371 Jan 27  2016 rsyslog.conf
drwxr-xr-x   2 root root      4096 Sep 14  2016 rsyslog.d
-rw-r--r--   1 root root      5189 Apr  4  2016 rygel.conf
drwxr-xr-x   3 root root      4096 Jul 16 17:46 samba
drwxr-xr-x   3 root root      4096 May  8 08:47 sane.d
-rw-r--r--   1 root root      4038 Feb 17  2014 securetty
drwxr-xr-x   4 root root      4096 Jan 11  2017 security
drwxr-xr-x   2 root root      4096 Sep 14  2016 selinux
-rw-r--r--   1 root root     10368 Oct  2  2015 sensors3.conf
drwxr-xr-x   2 root root      4096 Sep 14  2016 sensors.d
-rw-r--r--   1 root root     19605 Oct 25  2014 services
drwxr-xr-x   3 root root      4096 Sep 14  2016 sgml
-rw-r-----   1 root shadow    1560 Aug  7 22:47 shadow
-rw-------   1 root root      1560 Aug  7 22:47 shadow-
-rw-r--r--   1 root root        73 Feb 17  2016 shells
drwxr-xr-x   3 root root      4096 May 26 14:51 skel
-rw-r--r--   1 root root      6299 Jan  2  2016 s-nail.rc
drwxr-xr-x   3 root root      4096 Jun  8  2016 sound
drwxr-xr-x   4 root root      4096 Sep 14  2016 speech-dispatcher
drwxr-xr-x   2 root root      4096 May 11 15:23 ssh
drwxr-xr-x   4 root root      4096 Jun 11 21:55 ssl
drwxr-xr-x   2 root root      4096 Jun  9  2016 stunnel
-rw-r--r--   1 root root        19 Jun  9  2016 subgid
-rw-------   1 root root         0 Feb 17  2016 subgid-
-rw-r--r--   1 root root        19 Jun  9  2016 subuid
-rw-------   1 root root         0 Feb 17  2016 subuid-
-r--r-----   1 root root       755 Aug 17  2016 sudoers
drwxr-xr-x   2 root root      4096 Jul 27 13:59 sudoers.d
-rw-r--r--   1 root root        19 May  1  2011 su-to-rootrc
-rw-r--r--   1 root root      2102 Jun 14  2016 sysctl.conf
drwxr-xr-x   2 root root      4096 Aug  8 14:06 sysctl.d
drwxr-xr-x   5 root root      4096 Jul 25 12:37 systemd
drwxr-xr-x   2 root root      4096 Sep 14  2016 terminfo
drwxr-xr-x   2 root root      4096 Apr 27 05:59 thermald
drwxr-xr-x   2 root root      4096 Jul  6 10:46 thunderbird
-rw-r--r--   1 root root        14 Dec  8  2016 timezone
drwxr-xr-x   2 root root      4096 Jun  8  2016 timidity
drwxr-xr-x   2 root root      4096 Jul 12  2016 tmpfiles.d
drwxr-xr-x   2 root root      4096 Aug  7 22:53 tor
-rw-r--r--   1 root root       645 Jan 21  2014 ts.conf
-rw-r--r--   1 root root      1260 Jul  1  2013 ucf.conf
drwxr-xr-x   4 root root      4096 Jul 25 12:38 udev
drwxr-xr-x   2 root root      4096 Jun 10  2015 udisks2
drwxr-xr-x   3 root root      4096 Sep 14  2016 ufw
-rw-r--r--   1 root root       338 Nov 18  2014 updatedb.conf
drwxr-xr-x   3 root root      4096 Jul 27 14:00 update-manager
drwxr-xr-x   2 root root      4096 Aug  4 11:32 update-motd.d
drwxr-xr-x   2 root root      4096 Oct  7  2014 update-notifier
drwxr-xr-x   2 root root      4096 Sep 14  2016 UPower
-rw-r--r--   1 root root       270 May 19  2016 upstart-xsessions
-rw-r--r--   1 root root      1018 Oct  5  2015 usb_modeswitch.conf
drwxr-xr-x   2 root root      4096 Apr  9  2014 usb_modeswitch.d
-rw-r--r--   1 root root        51 Feb 19  2016 vdpau_wrapper.cfg
drwxr-xr-x   2 root root      4096 Nov 29  2016 vim
lrwxrwxrwx   1 root root        23 Jun  8  2016 vtrgb -> /etc/alternatives/vtrgb
-rw-r--r--   1 root root      4942 Jun 14  2016 wgetrc
drwxr-xr-x   2 root root      4096 Sep 14  2016 wildmidi
drwxr-xr-x   2 root root      4096 Sep 14  2016 wpa_supplicant
drwxr-xr-x  11 root root      4096 Sep 14  2016 X11
drwxr-xr-x  12 root root      4096 Sep 14  2016 xdg
drwxr-xr-x   2 root root      4096 Sep 14  2016 xfce4
drwxr-xr-x   2 root root      4096 Sep 14  2016 xml
-rw-r--r--   1 root root       477 Jul 19  2015 zsh_command_not_found
makem@ssdTOSH:/etc$ 



```


[COLOR=#FF0000]lrwxrwxrwx   1 root root        29 Jun  8  2016 resolv.conf -> ../run/resolvconf/resolv.conf

[/COLOR][COLOR=#000000]Is present but its properties for [/COLOR][COLOR=#000000][FONT=&amp]/etc/resolvconf/resolv.conf.d/tail contained in the directory [/FONT][/COLOR][COLOR=#000000]in FileManager say 'broken link'[/COLOR]
[COLOR=#000000]
[/COLOR]```
makem@ssdTOSH:/etc$ stat /etc/resolvconf/resolv.conf.d/tail
  File: '/etc/resolvconf/resolv.conf.d/tail' -> 'original'
  Size: 8             Blocks: 0          IO Block: 4096   symbolic link
Device: 802h/2050d    Inode: 654561      Links: 1
Access: (0777/lrwxrwxrwx)  Uid: (    0/    root)   Gid: (    0/    root)
Access: 2017-03-04 10:54:52.980475452 +0000
Modify: 2017-03-04 10:54:52.980475452 +0000
Change: 2017-03-04 10:54:52.980475452 +0000
 Birth: -
makem@ssdTOSH:/etc$


```

No mention of 'broken'

[COLOR=#000000]Actually I thought symlinks were shown in blue coloured text in listing but this on is not (because broken?). However, there are many also not in blue too.[/COLOR]

[COLOR=#000000]Anyway, the system appears to have started shutting down very quickly after the first attempt with grub recovery options. So, should I leave well alone or be concerned about this broken link?[/COLOR]

---

### Post by praseodym on 2017-08-16
The file is called "/etc/resolv.conf", without the second "e". Maybe setting its symlink again:

```
sudo rm /etc/resolv.conf
sudo ln -s /var/run/resolvconf/resolv.conf /etc/resolv.conf
sudo service network-manager restart
```

---

### Post by makem2 on 2017-08-16
> **praseodym said:**
> The file is called "/etc/resolv.conf", without the second "e". Maybe setting its symlink again:

```
sudo rm /etc/resolv.conf
sudo ln -s /var/run/resolvconf/resolv.conf /etc/resolv.conf
sudo service network-manager restart
```

Thank you, but I would like to understand what I am doing before doing that.

```

makem@ssdTOSH:~$ cd /etc/resolvconf
makem@ssdTOSH:/etc/resolvconf$ ls -la
total 32
drwxr-xr-x   5 root root  4096 Mar  4 10:54 .
drwxr-xr-x 157 root root 12288 Aug 16 10:16 ..
-rw-r--r--   1 root root   511 Jun  3  2015 interface-order
drwxr-xr-x   2 root root  4096 Mar  4 10:54 resolv.conf.d
drwxr-xr-x   2 root root  4096 Mar  4 10:54 update.d
drwxr-xr-x   2 root root  4096 Sep 14  2016 update-libc.d
makem@ssdTOSH:/etc/resolvconf$ cd resolv.conf.d
makem@ssdTOSH:/etc/resolvconf/resolv.conf.d$ ls -la
total 12
drwxr-xr-x 2 root root 4096 Mar  4 10:54 .
drwxr-xr-x 5 root root 4096 Mar  4 10:54 ..
-rw-r--r-- 1 root root    0 Dec 13  2012 base
-rw-r--r-- 1 root root  151 Dec 13  2012 head
lrwxrwxrwx 1 root root    8 Mar  4 10:54 tail -> original
makem@ssdTOSH:/etc/resolvconf/resolv.conf.d$

```

Now you tell me to remove /etc/resolv.conf directory (no extra 'e' in there or its contents). This will remove all contents of that directory.

Then I make a symlink from /var/run/resolvconf/resolv.conf to /etc/resolv.conf

This will remake the directory cd /etc/resolvconf and its contents? (Including repairing the broken symlink)

/var/run is itself a symlink to /run in which is NetworkManager inside which is another resolv.conf.

Sorry if I am being pedantic but I am also trying to get my head around symlinks which I've already had a problem. Is it possible to explain what the end result of those link is? Does it set the 'flow' to the final resolv.conf?

---

### Post by praseodym on 2017-08-16
Not the directory, only the conf file in /etc/. You can also backup it instead:

```
sudo mv /etc/resolv.conf /etc/resolv.backup
```

---

### Post by makem2 on 2017-08-16
> **praseodym said:**
> Not the directory, only the conf file in /etc/. You can also backup it instead:

```
sudo mv /etc/resolv.conf /etc/resolv.backup
```

Sorry, of course, file not directory.

Ok, I will backup and try remaking the link.

```

makem@ssdTOSH:/$ sudo mv /etc/resolv.conf /etc/resolv.backup
[sudo] password for makem: 
makem@ssdTOSH:/$ sudo ln -s /var/run/resolvconf/resolv.conf /etc/resolv.conf
makem@ssdTOSH:/$ sudo service network-manager restart
makem@ssdTOSH:/$

```

Now to reboot and start grub in recovery mode.


EDIT: It has just dawned on me - there was never a /etc/resolv.conf file!

Anyhow, I made the symlink change before seeing that and when I check the directory again, nothing has changed. The symlink is still broken.

I will however, reboot and see what I get.

---

### Post by makem2 on 2017-08-16
Rebooted, started grub in recovery mode, still get the same error in networking:
[COLOR=#000000]Enable Networking - error:[/COLOR]

[COLOR=#000000]grep: /etc/resolve.conf: No such file or directory[/COLOR]
[COLOR=#000000]Trying to start NetworkManager.........[/COLOR]
[COLOR=#000000]grep: /etc/resolve.conf: No such file or directory[/COLOR]

[COLOR=#000000]After several attempts the system hangs.[/COLOR]

[COLOR=#000000]Reboot is fine, networking operates normally.

[/COLOR]Shutdown is quick.

We need an /etc/resolv.conf!

---

### Post by makem2 on 2017-08-16
> **praseodym said:**
> The file is called "/etc/resolv.conf", without the second "e". Maybe setting its symlink again:

```
sudo rm /etc/resolv.conf
sudo ln -s /var/run/resolvconf/resolv.conf /etc/resolv.conf
sudo service network-manager restart
```

did you mean /etc/resolvconf not /etc/resolv.conf

Therefore: [COLOR=#000000][FONT=&quot]sudo ln -s /var/run/resolvconf/resolv.conf /etc/resolvconf ?[/FONT][/COLOR]

---

### Post by makem2 on 2017-08-16
Would this solve my broken link?

[https://askubuntu.com/questions/812714/run-resolvconf-resolv-conf-gets-erased-each-time-i-restart-and-i-cant-use-int](https://askubuntu.com/questions/812714/run-resolvconf-resolv-conf-gets-erased-each-time-i-restart-and-i-cant-use-int)

---

