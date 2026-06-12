---
title: "Root suddenly expanded to fill partition"
date: 2010-08-02
forum: New to Ubuntu
---

### Post by TXpaniolo on 2010-08-02
I was in Firefox and got a popup system msg that my partition was full.  Quit and rebooted and get strange msgs about configuration defaults for GNOME power mgmt.  Booted up in LiveCD and see that my root has totally filled the 11gb partition, which seems to totally choke the Ubuntu boot.

Background:  Yesterday I moved my /home to a separate partition following the [community guide]("https://help.ubuntu.com/community/HowtoPartition/EditorsAndBackup") .  That all seemed well and I rebooted several times and everything worked OK through the day.  Then I decided to shrink the root partition (sda1)  and increase the space in the extended partition for /home (sda7).  I used Gparted Live from CD with the last action moving the freed unallocated space to sda7.  This was projected to take 40min so I turned off screen and went to bed.  This am all actions were shown as completed OK in GParted.  I quit and rebooted  and started browsing in Firefox and in that time the files in root doubled in size from under 5gb to over 10gb and the above errors and problems started.

I checked Fstab from the LiveCD boot and everything looks fine with the proper UUID's and mount points.

Suggestions?  Should I just go back into Gparted and increase the size of the root partition and debug from there?

Just when I thought I was at the last major activity I wanted to get done on the installation ... which just seems like a metaphor for my life :D

---

### Post by dream_coder on 2010-08-02
I had a similar problem mine was log files that were getting far too big, check /var/log and see if the space is being taken up by log files, weird problem I know but on mine I filled a 20gb root partition in 4 hours it was that bad!

if you find that it is then you either need to work out what is causing the massive increase in log files or just remove the logs at fault for now until you find the problem if i is killing your space.

P.S hint go to terminal type in baobab will bring up disk usage analyser help you find where the problem lies.

---

### Post by TXpaniolo on 2010-08-02
Thanks for the response.

I checked my /var and it was not the problem.  So I ran baobab (Disk Usage Analyzer) from terminal.  I'm on CD, so when I mounted sda1 which is partitioned at 11gb it shows usage at 100%, but with only 4.3 gb of files?  Does the usage show the % of the total available in the partition?  It seems like it is saying there are 4,3gb of files but the whole 11gb partition is used?

More confusing when I go to Disk Utility and highlight the sda1 partition it shows 11gb capacity, but with 0 available.  I try to run the check filesystem, and get an error "Device is mounted and no online capability in fsck tool for file system"

---

### Post by blur xc on 2010-08-02
yup- 1st thing I'd check is the log files.  Also - du -sx might help you find out what directory is hogging up your space.

I had a program crash and was stuck in some endless loop in the background writing error messages to the system log fiels, filled up my whole 20gb / partition, made my computer unbootable.  It'd start to the initramfs prompt.  I had to delete the offending files, and then fix my partition to be bootable again (for some reason it got unmarked- dunno, but it fixed it).

BM

---

### Post by linux18 on 2010-08-02
post the output of:

```
 du / -hs 
``` 
```
 df 
```
```
 du /var -h 
```
```
 du /boot -h 
```
```
 du /usr -h 
```

---

### Post by blur xc on 2010-08-02
> **blur xc said:**
> yup- 1st thing I'd check is the log files.  Also - du -sx might help you find out what directory is hogging up your space.

I had a program crash and was stuck in some endless loop in the background writing error messages to the system log fiels, filled up my whole 20gb / partition, made my computer unbootable.  It'd start to the initramfs prompt.  I had to delete the offending files, and then fix my partition to be bootable again (for some reason it got unmarked- dunno, but it fixed it).

BM

I checked the du man page and here's a revised command which will throw out some more relevant information- 

```
du -hx --max-depth 1 / 2> /dev/null
```

After that you can find which directory has all the data, then re-run that command for that directoiry (if it's /var then replace the / with /var, etc...)

good luck

BM

---

### Post by TXpaniolo on 2010-08-02
> **linux18 said:**
> post the output of:


```
 du / -hs

I get several pages of permission denied msgs like, does this have to do with me running in LiveCD since I can't boot from HD?  It actually scrolls off the top of Terminal and I can't get to it all.

du: cannot read directory `/proc/5846/fd': Permission denied
du: cannot read directory `/proc/5846/fdinfo': Permission denied
du: cannot access `/proc/5858/task/5858/fd/3': No such file or directory
du: cannot access `/proc/5858/task/5858/fdinfo/3': No such file or directory
du: cannot access `/proc/5858/fd/3': No such file or directory
du: cannot access `/proc/5858/fdinfo/3': No such file or directory
8.7G    /
ubuntu@ubuntu:/home$  
``````
 df 
ubuntu@ubuntu:/home$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
aufs                    996140     93000    903140  10% /
none                    990896       288    990608   1% /dev
/dev/sr0                714310    714310         0 100% /cdrom
/dev/loop0              682368    682368         0 100% /rofs
none                    996140       276    995864   1% /dev/shm
tmpfs                   996140      1532    994608   1% /tmp
none                    996140        88    996052   1% /var/run
none                    996140         4    996136   1% /var/lock
none                    996140         0    996140   0% /lib/init/rw
/dev/sda1             10118080  10095460         0 100% /media/1198ecf0-2399-41bb-bfc5-8de670143c46

``````
 du /var -h 

ubuntu@ubuntu:/home$ du /var -h 
1.3M    /var/crash
du: cannot read directory `/var/spool/cups': Permission denied
0    /var/spool/cups
0    /var/spool/anacron
du: cannot read directory `/var/spool/cron/atjobs': Permission denied
0    /var/spool/cron/atjobs
du: cannot read directory `/var/spool/cron/atspool': Permission denied
0    /var/spool/cron/atspool
du: cannot read directory `/var/spool/cron/crontabs': Permission denied
0    /var/spool/cron/crontabs
0    /var/spool/cron
11K    /var/spool/openoffice/uno_packages/cache/registry/com.sun.star.comp.deployment.component.PackageRegistryBackend
0    /var/spool/openoffice/uno_packages/cache/registry/com.sun.star.comp.deployment.configuration.PackageRegistryBackend/registry
12K    /var/spool/openoffice/uno_packages/cache/registry/com.sun.star.comp.deployment.configuration.PackageRegistryBackend
0    /var/spool/openoffice/uno_packages/cache/registry/com.sun.star.comp.deployment.executable.PackageRegistryBackend
0    /var/spool/openoffice/uno_packages/cache/registry/com.sun.star.comp.deployment.help.PackageRegistryBackend
0    /var/spool/openoffice/uno_packages/cache/registry/com.sun.star.comp.deployment.script.PackageRegistryBackend
0    /var/spool/openoffice/uno_packages/cache/registry/com.sun.star.comp.deployment.sfwk.PackageRegistryBackend
23K    /var/spool/openoffice/uno_packages/cache/registry
12K    /var/spool/openoffice/uno_packages/cache/uno_packages/PNKYek_
12K    /var/spool/openoffice/uno_packages/cache/uno_packages
47K    /var/spool/openoffice/uno_packages/cache
47K    /var/spool/openoffice/uno_packages
47K    /var/spool/openoffice
0    /var/spool/plymouth
47K    /var/spool
4.0K    /var/cache/jockey
0    /var/cache/apt/archives/partial
0    /var/cache/apt/archives
7.0M    /var/cache/apt
1.5M    /var/cache/hald
0    /var/cache/gdm/ubuntu
0    /var/cache/gdm
268K    /var/cache/fontconfig
0    /var/cache/cups/rss
0    /var/cache/cups
19M    /var/cache/debconf
1.0K    /var/cache/binfmts
6.0K    /var/cache/dictionaries-common
du: cannot read directory `/var/cache/ldconfig': Permission denied
0    /var/cache/ldconfig
0    /var/cache/man/cat1
0    /var/cache/man/cat2
0    /var/cache/man/cat3
0    /var/cache/man/cat4
0    /var/cache/man/cat5
0    /var/cache/man/cat6
0    /var/cache/man/cat7
0    /var/cache/man/cat8
0    /var/cache/man/cs/cat1
0    /var/cache/man/cs/cat5
0    /var/cache/man/cs/cat7
0    /var/cache/man/cs/cat8
14K    /var/cache/man/cs
0    /var/cache/man/de/cat1
0    /var/cache/man/de/cat3
0    /var/cache/man/de/cat5
0    /var/cache/man/de/cat7
0    /var/cache/man/de/cat8
22K    /var/cache/man/de
0    /var/cache/man/es/cat1
0    /var/cache/man/es/cat5
0    /var/cache/man/es/cat8
14K    /var/cache/man/es
0    /var/cache/man/fi/cat1
0    /var/cache/man/fi/cat8
13K    /var/cache/man/fi
0    /var/cache/man/fr/cat1
0    /var/cache/man/fr/cat3
0    /var/cache/man/fr/cat5
0    /var/cache/man/fr/cat7
0    /var/cache/man/fr/cat8
36K    /var/cache/man/fr
0    /var/cache/man/fr.ISO8859-1/cat7
0    /var/cache/man/fr.ISO8859-1/cat8
13K    /var/cache/man/fr.ISO8859-1
0    /var/cache/man/fr.UTF-8/cat7
0    /var/cache/man/fr.UTF-8/cat8
13K    /var/cache/man/fr.UTF-8
0    /var/cache/man/gl/cat8
13K    /var/cache/man/gl
0    /var/cache/man/hu/cat1
0    /var/cache/man/hu/cat5
0    /var/cache/man/hu/cat8
13K    /var/cache/man/hu
0    /var/cache/man/id/cat1
0    /var/cache/man/id/cat5
0    /var/cache/man/id/cat8
14K    /var/cache/man/id
0    /var/cache/man/it/cat1
0    /var/cache/man/it/cat5
0    /var/cache/man/it/cat8
17K    /var/cache/man/it
0    /var/cache/man/ja/cat1
0    /var/cache/man/ja/cat5
0    /var/cache/man/ja/cat8
18K    /var/cache/man/ja
0    /var/cache/man/ko/cat1
0    /var/cache/man/ko/cat5
0    /var/cache/man/ko/cat8
13K    /var/cache/man/ko
0    /var/cache/man/pl/cat1
0    /var/cache/man/pl/cat5
0    /var/cache/man/pl/cat8
18K    /var/cache/man/pl
0    /var/cache/man/pt_BR/cat1
0    /var/cache/man/pt_BR/cat5
0    /var/cache/man/pt_BR/cat8
14K    /var/cache/man/pt_BR
0    /var/cache/man/ru/cat1
0    /var/cache/man/ru/cat5
0    /var/cache/man/ru/cat8
22K    /var/cache/man/ru
0    /var/cache/man/sv/cat1
0    /var/cache/man/sv/cat5
0    /var/cache/man/sv/cat8
16K    /var/cache/man/sv
0    /var/cache/man/tr/cat1
0    /var/cache/man/tr/cat5
0    /var/cache/man/tr/cat8
14K    /var/cache/man/tr
0    /var/cache/man/zh_CN/cat1
0    /var/cache/man/zh_CN/cat5
0    /var/cache/man/zh_CN/cat8
13K    /var/cache/man/zh_CN
0    /var/cache/man/zh_TW/cat1
0    /var/cache/man/zh_TW/cat5
0    /var/cache/man/zh_TW/cat8
13K    /var/cache/man/zh_TW
937K    /var/cache/man
0    /var/cache/pm-utils
0    /var/cache/pppconfig
0    /var/cache/samba
1.8M    /var/cache/software-center/xapian
1.8M    /var/cache/software-center
30M    /var/cache
4.0K    /var/lib/udisks
43K    /var/lib/update-rc.d
4.0K    /var/lib/localechooser
4.0K    /var/lib/update-manager
0    /var/lib/plymouth
12K    /var/lib/xkb
0    /var/lib/update-notifier/user.d
4.0K    /var/lib/update-notifier
4.0K    /var/lib/urandom
8.0K    /var/lib/dhcp3
4.0K    /var/lib/NetworkManager
4.0K    /var/lib/dbus
du: cannot read directory `/var/lib/polkit-1': Permission denied
0    /var/lib/polkit-1
0    /var/lib/apt/lists/partial
12M    /var/lib/apt/lists
7.0K    /var/lib/apt/keyrings
0    /var/lib/apt/mirrors/partial
0    /var/lib/apt/mirrors
0    /var/lib/apt/periodic
12M    /var/lib/apt
48K    /var/lib/belocs
6.5K    /var/lib/locales/supported.d
6.5K    /var/lib/locales
36K    /var/lib/gconf/debian.defaults
0    /var/lib/gconf/debian.mandatory
2.4M    /var/lib/gconf/defaults
2.4M    /var/lib/gconf
37K    /var/lib/dpkg/alternatives
29M    /var/lib/dpkg/info
0    /var/lib/dpkg/parts
4.0K    /var/lib/dpkg/triggers
0    /var/lib/dpkg/updates
34M    /var/lib/dpkg
0    /var/lib/acpi-support
0    /var/lib/alsa
0    /var/lib/apparmor
10M    /var/lib/apt-xapian-index/index.1
10M    /var/lib/apt-xapian-index
0    /var/lib/aptitude
3.4M    /var/lib/aspell
0    /var/lib/avahi-autoipd
1.0K    /var/lib/binfmts
0    /var/lib/computer-janitor
46K    /var/lib/defoma/fontconfig.d
0    /var/lib/defoma/gs.d/dirs/CMap
6.5K    /var/lib/defoma/gs.d/dirs/fonts
6.5K    /var/lib/defoma/gs.d/dirs
48K    /var/lib/defoma/gs.d
58K    /var/lib/defoma/libwmf0.2-7.d
3.0K    /var/lib/defoma/pango.d
157K    /var/lib/defoma/psfontmgr.d
69K    /var/lib/defoma/scripts
0    /var/lib/defoma/x-ttcidfont-conf.d/dirs/CID
6.5K    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
6.5K    /var/lib/defoma/x-ttcidfont-conf.d/dirs
9.5K    /var/lib/defoma/x-ttcidfont-conf.d
499K    /var/lib/defoma
512    /var/lib/dictionaries-common/aspell
512    /var/lib/dictionaries-common/hunspell
1.0K    /var/lib/dictionaries-common/wordlist
2.0K    /var/lib/dictionaries-common
18K    /var/lib/doc-base/documents
34K    /var/lib/doc-base/info
1.0K    /var/lib/doc-base/omf/cups
1.5K    /var/lib/doc-base/omf/dc
1.0K    /var/lib/doc-base/omf/doc-base
1.0K    /var/lib/doc-base/omf/esound
1.0K    /var/lib/doc-base/omf/fontconfig-user
1.0K    /var/lib/doc-base/omf/gnupg-faq
1.0K    /var/lib/doc-base/omf/gnupginterface
1.0K    /var/lib/doc-base/omf/install-docs-man
2.0K    /var/lib/doc-base/omf/libpng12
1.5K    /var/lib/doc-base/omf/mako
1.0K    /var/lib/doc-base/omf/man-db
1.0K    /var/lib/doc-base/omf/nano-faq
1.0K    /var/lib/doc-base/omf/nat
1.0K    /var/lib/doc-base/omf/packet-filter
1.0K    /var/lib/doc-base/omf/pnm2ppa-calibrate
1.0K    /var/lib/doc-base/omf/pnm2ppa-color
1.5K    /var/lib/doc-base/omf/pnm2ppa-ppa-networking
1.0K    /var/lib/doc-base/omf/python-policy
1.0K    /var/lib/doc-base/omf/python-pycurl
1.0K    /var/lib/doc-base/omf/shared-mime-info
1.0K    /var/lib/doc-base/omf/time
1.0K    /var/lib/doc-base/omf/users-and-groups
1.0K    /var/lib/doc-base/omf/xterm-ctlseqs
1.0K    /var/lib/doc-base/omf/xterm-faq
27K    /var/lib/doc-base/omf
78K    /var/lib/doc-base
du: cannot read directory `/var/lib/gdm': Permission denied
0    /var/lib/gdm
0    /var/lib/hal
512    /var/lib/hp
512    /var/lib/initramfs-tools
0    /var/lib/initscripts
0    /var/lib/insserv
0    /var/lib/libuuid
2.0K    /var/lib/libxml-sax-perl/ParserDetails.d
2.0K    /var/lib/libxml-sax-perl
0    /var/lib/logrotate
0    /var/lib/misc
3.2M    /var/lib/mlocate
0    /var/lib/ntpdate
5.3M    /var/lib/openoffice/basis3.2/program
512    /var/lib/openoffice/basis3.2/share/config
512    /var/lib/openoffice/basis3.2/share
5.3M    /var/lib/openoffice/basis3.2
5.3M    /var/lib/openoffice
0    /var/lib/os-prober
3.0K    /var/lib/pam
512    /var/lib/partconf/fstab.d
512    /var/lib/partconf
0    /var/lib/pulseaudio
512    /var/lib/pycentral
0    /var/lib/samba
0    /var/lib/sgml-base
0    /var/lib/snmp
0    /var/lib/synaptic
27K    /var/lib/ucf/cache
35K    /var/lib/ucf
0    /var/lib/upower
0    /var/lib/ureadahead/debugfs
0    /var/lib/ureadahead
360K    /var/lib/usbutils
0    /var/lib/vim/addons
0    /var/lib/vim
1.0K    /var/lib/x11
512    /var/lib/xfonts
17K    /var/lib/xml-core
71M    /var/lib
4.0K    /var/log/cups
du: cannot read directory `/var/log/gdm': Permission denied
0    /var/log/gdm
4.0K    /var/log/ConsoleKit
12K    /var/log/installer
0    /var/log/news
0    /var/log/apparmor
38K    /var/log/apt
0    /var/log/dist-upgrade
1.0K    /var/log/fsck
0    /var/log/samba
0    /var/log/speech-dispatcher
0    /var/log/unattended-upgrades
1.6M    /var/log
0    /var/backups
0    /var/games
0    /var/local
4.0K    /var/lock
0    /var/mail
0    /var/opt
du: cannot read directory `/var/run/gdm': Permission denied
0    /var/run/gdm
0    /var/run/pm-utils/pm-powersave/storage
0    /var/run/pm-utils/pm-powersave
0    /var/run/pm-utils/locks
0    /var/run/pm-utils
4.0K    /var/run/console
0    /var/run/pppconfig
4.0K    /var/run/ConsoleKit
0    /var/run/udev-configure-printer
du: cannot read directory `/var/run/cups/certs': Permission denied
0    /var/run/cups/certs
8.0K    /var/run/cups
0    /var/run/screen
4.0K    /var/run/avahi-daemon
4.0K    /var/run/network
4.0K    /var/run/dbus
0    /var/run/sendsigs.omit.d
76K    /var/run
0    /var/tmp
104M    /var

``````
 du /boot -h 
ubuntu@ubuntu:/home$ du /boot -h
4.0K    /boot/grub
3.0M    /boot

```
```
 du /usr -h 

This one gave pages and pages of output ... you really want it all?  here is a small sampling of what was listed:  

0    /usr/src/linux-headers-2.6.32-21-generic/include/config/x86/powernow
0    /usr/src/linux-headers-2.6.32-21-generic/include/config/x86/reroute/for/broken/boot
0    /usr/src/linux-headers-2.6.32-21-generic/include/config/x86/reroute/for/broken
0    /usr/src/linux-headers-2.6.32-21-generic/include/config/x86/reroute/for
0    /usr/src/linux-headers-2.6.32-21-generic/include/config/x86/reroute
0    /usr/src/linux-headers-2.6.32-21-generic/include/config/x86/reserve/low
0    /usr/src/linux-headers-2.6.32-21-generic/include/config/x86/reserve
0    /usr/src/linux-headers-2.6.32-21-generic/include/config/x86/speedstep
0    /usr/src/linux-headers-2.6.32-21-generic/include/config/x86/supports/memory
0    /usr/src/linux-headers-2.6.32-21-generic/include/config/x86/supports
0    /usr/src/linux-headers-2.6.32-21-generic/include/config/x86/thermal
0    /usr/src/linux-headers-2.6.32-21-generic/include/config/x86/wp/works
0    /usr/src/linux-headers-2.6.32-21-generic/include/config/x86/wp
0    /usr/src/linux-headers-2.6.32-21-generic/include/config/x86
0    /usr/src/linux-headers-2.6.32-21-generic/include/config/xen/blkdev
0    /usr/src/linux-headers-2.6.32-21-generic/include/config/xen/compat
0    /usr/src/linux-headers-2.6.32-21-generic/include/config/xen/dev
0    /usr/src/linux-headers-2.6.32-21-generic/include/config/xen/fbdev
0    /usr/src/linux-headers-2.6.32-21-generic/include/config/xen/kbddev
0    /usr/src/linux-headers-2.6.32-21-generic/include/config/xen/max/domain
0    /usr/src/linux-headers-2.6.32-21-generic/include/config/xen/max
0    /usr/src/linux-headers-2.6.32-21-generic/include/config/xen/netdev
0    /usr/src/linux-headers-2.6.32-21-generic/include/config/xen/save
0    /usr/src/linux-headers-2.6.32-21-generic/include/config/xen/scrub
0    /usr/src/linux-headers-2.6.32-21-generic/include/config/xen/sys
0    /usr/src/linux-headers-2.6.32-21-generic/include/config/xen
0    /usr/src/linux-headers-2.6.32-21-generic/include/config/xfrm
0    /usr/src/linux-headers-2.6.32-21-generic/include/config/xfs/posix
0    /usr/src/linux-headers-2.6.32-21-generic/include/config/xfs
0    /usr/src/linux-headers-2.6.32-21-generic/include/config/xor
0    /usr/src/linux-headers-2.6.32-21-generic/include/config/yenta/ene
0    /usr/src/linux-headers-2.6.32-21-generic/include/config/yenta
0    /usr/src/linux-headers-2.6.32-21-generic/include/config/zeroplus
0    /usr/src/linux-headers-2.6.32-21-generic/include/config/zlib
0    /usr/src/linux-headers-2.6.32-21-generic/include/config/zone/dma
0    /usr/src/linux-headers-2.6.32-21-generic/include/config/zone
155K    /usr/src/linux-headers-2.6.32-21-generic/include/config
132K    /usr/src/linux-headers-2.6.32-21-generic/include/linux
292K    /usr/src/linux-headers-2.6.32-21-generic/include
8.5K    /usr/src/linux-headers-2.6.32-21-generic/kernel
49K    /usr/src/linux-headers-2.6.32-21-generic/scripts/basic
294K    /usr/src/linux-headers-2.6.32-21-generic/scripts/genksyms
389K    /usr/src/linux-headers-2.6.32-21-generic/scripts/kconfig
173K    /usr/src/linux-headers-2.6.32-21-generic/scripts/mod
24K    /usr/src/linux-headers-2.6.32-21-generic/scripts/selinux/mdp
24K    /usr/src/linux-headers-2.6.32-21-generic/scripts/selinux
962K    /usr/src/linux-headers-2.6.32-21-generic/scripts
2.0M    /usr/src/linux-headers-2.6.32-21-generic
44M    /usr/src
1.6G    /usr
ubuntu@ubuntu:/home$ 


```

---

### Post by TXpaniolo on 2010-08-02
> **blur xc said:**
> I checked the du man page and here's a revised command which will throw out some more relevant information- 

```
du -hx --max-depth 1 / 2> /dev/null

Printout:
ubuntu@ubuntu:/media/1198ecf0-2399-41bb-bfc5-8de670143c46$ du -hx --max-depth 1 / 2> /dev/null
4.0K    /media
0    /root
3.0M    /boot
1.6G    /usr
56M    /home
104M    /var
7.8M    /etc
2.0K    /cdrom
0    /tmp
0    /rofs
7.7M    /bin
0    /dev
138M    /lib
0    /mnt
0    /opt
0    /proc
9.9M    /sbin
0    /selinux
0    /srv
0    /sys
1.9G    /
ubuntu@ubuntu:/media/


```

These add up to about 4G as it started out.  Don't see anything here, but my 11g partition is giving an error?

---

### Post by blur xc on 2010-08-02
Well, I re-read your original posts and the terminal output you posted and I'm pretty sure your problem is over my head.

Sorry...  Hopefully someone smarter than me will chime in w/ the 30sec fix...

Just as an FYI- when doing commands that search root folders (du, find, etc..) you will find there are folder that just can't be accessed (like /proc).  Dunno why- I think they aren't "real" filesystems or are special in some way...but either way, it spits out a lot of irrelevant error messages.  If you put the "2> /dev/null" it redirects the error output to limbo.  Just try it when you get a chance- enter "dafdsa" and hit enter on the command line and it'll tell you command not found, etc. etc...  Now enter "dafdasfs 2> /dev/null"...  error message supressed.

Good luck w/ your problem.

BM

---

### Post by linux18 on 2010-08-02
du -hx --max-depth 1 / 2> /dev/null

Thats what i was actually trying to think of, but the problem is that your entering these through a live cd.
you must mount your hard drive and look for it in /media
assuming your mounted drive is /media/disk-1 the command to type is:
```
 du /media/disk-1 -hx --max-depth 1 2> /dev/null 
```

---

### Post by TXpaniolo on 2010-08-02
BlurXC, thanks for your help, appreciate it!

linux18,  see the output from my post #8.  I changed to media and the numbers are the UUID of the partition for root on the harddrive.

Again it is saying just over 4Gig in files from the du command, but that partition is showing as 100% full??

Did you still want the output from those other du commands on the mounted root partition?

---

### Post by TXpaniolo on 2010-08-02
Here is the output from df ... 

```

ubuntu@ubuntu:/media/1198ecf0-2399-41bb-bfc5-8de670143c46$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
aufs                    996140     96596    899544  10% /
none                    990896       288    990608   1% /dev
/dev/sr0                714310    714310         0 100% /cdrom
/dev/loop0              682368    682368         0 100% /rofs
none                    996140       276    995864   1% /dev/shm
tmpfs                   996140      1536    994604   1% /tmp
none                    996140        88    996052   1% /var/run
none                    996140         4    996136   1% /var/lock
none                    996140         0    996140   0% /lib/init/rw
/dev/sda1             10118080  10095460         0 100% /media/1198ecf0-2399-41bb-bfc5-8de670143c46
ubuntu@ubuntu:/media/1198ecf0-2399-41bb-bfc5-8de670143c46$ 


```

As you can see /dev/sda1 is almost double what showed up with the du -hx --max-depth 1 / 2> /dev/null command on the directory??  Shown again below.

```

ubuntu@ubuntu:/media/1198ecf0-2399-41bb-bfc5-8de670143c46$ du -hx --max-depth 1 / 2> /dev/null
4.0K    /media
0    /root
3.0M    /boot
1.6G    /usr
59M    /home
104M    /var
7.8M    /etc
2.0K    /cdrom
0    /tmp
0    /rofs
7.7M    /bin
0    /dev
138M    /lib
0    /mnt
0    /opt
0    /proc
9.9M    /sbin
0    /selinux
0    /srv
0    /sys
1.9G    /
ubuntu@ubuntu:/media/1198ecf0-2399-41bb-bfc5-8de670143c46$ 


```

---

### Post by dream_coder on 2010-08-03
personally if it was me and I always have backups I would just try a reinstall to save time finding the problem and see if that fixes it, but if you want to try and find a solution perhaps a more experienced person will post and help - sorry I could'nt help mate.


just to mention have you deleted any files using "sudo nautilus" ? if so I came across similar problem before doing this and the files did not show up in baobab or even terminal but where definitely there, I would rm all log files from /var/log using "sudo find /var/log -type f -delete" may help? and also check roots bin see if there are any files in there also that may be taking up space.

---

### Post by TXpaniolo on 2010-08-03
Yeah, I kind of thought even yesterday that reinstalling would probably save me a lot of time and frustration.  Though I do have /home backed up with rsynch and also on a separate partition, I have never done it and am just kind of scared of it.  Unreasonable, I realize!

Last night I was resigned to reinstalling, but thought the problems started after adjusting the root partition down to 10gig after moving /home to a separate partition.  So figured I would use Gparted again and see what happens.  Increased / partition to 20G from 10g while I was asleep last night.  Booted from HD this am and things seem to be running as normal.

But I am still concerned/perplexed by the output from these codes:

```
df
system@David-desktop:/home$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sdb1             21109424  12263372   7773732  62% /
none                    991620       288    991332   1% /dev
none                    996128       264    995864   1% /dev/shm
none                    996128        88    996040   1% /var/run
none                    996128         4    996124   1% /var/lock
none                    996128         0    996128   0% /lib/init/rw
/dev/sdb7            447109656  44004476 380393296  11% /home
system@David-desktop:/home$ 

```Why are the root and home devices showing as sdb1 and sdb7?  I had put these partitions on the first hard drive sda?  Also, I assume that taking the col of 1k-blocks and subtracting Used should give you Available.  For sbd7, that has like 39g of files this is showing 440g used?  But 380g still available?  Am I reading this wrong, or is something weird?

```
du -hx --max-depth 1 / 2> /dev/null
system@David-desktop:/home$ du -hx --max-depth 1 / 2> /dev/null
4.0K    /selinux
412M    /lib
0    /dev
200K    /srv
0    /proc
0    /sys
2.8G    /usr
49M    /boot
252M    /opt
8.3M    /sbin
898M    /var
13M    /lib32
7.8M    /bin
15M    /etc
4.0K    /cdrom
4.0K    /root
16K    /lost+found
3.2M    /tmp
4.0K    /mnt
4.0K    /home
14G    /media
18G    /
system@David-desktop:/home$ 

```When I add these values I get about 36.7g ... I would have expected these values to equal the amount shown in root above, sdb1 of 12.3g used?  Am I looking at this wrong?

OK this is even weirder ... I scrolled up in terminal to the du -hx --max-depth 1 / 2> /dev/null code I ran 5 min ago and I have been doing nothing but writing this post ... the /media and / entry has almost doubled.  Here is earlier output:

```
system@David-desktop:~$ du -hx --max-depth 1 / 2> /dev/null
4.0K    /selinux
412M    /lib
0    /dev
200K    /srv
0    /proc
0    /sys
2.8G    /usr
49M    /boot
252M    /opt
8.3M    /sbin
899M    /var
13M    /lib32
7.8M    /bin
15M    /etc
4.0K    /cdrom
4.0K    /root
16K    /lost+found
2.1M    /tmp
4.0K    /mnt
4.0K    /home
5.1G    /media
9.5G    /
system@David-desktop:~$ 
```... and literally as I was typing this a root file system out of space warning just popped up???

Sigh, guess I need to figure out how to reinstall and hope I did the right things to preserve /home and all my settings.

Sorry for the length, kind of a stream of consciousness as things actually happened, rather than just deleting the whole post, I will leave it for someone else having problems.  Unless the mods see it as pointless, feel free to remove.

---

### Post by TXpaniolo on 2010-08-03
> **dream_coder said:**
> I had a similar problem mine was log files that were getting far too big, 

Dream_coder and Blur xc were on the right path.  But it wasn't log files, it was SimpleBackup.  When I set up backups with the new partitions I thought I set destination as my 2nd internal drive, but I guess I set it to my main drive.  I never saw it in /root, but it was getting set in /media.  So every day it would back up the prior days back up resulting in a doubling of root every day.  

I went to check the backup location in nautilus before reinstalling to make sure I had a current one.  When it wasn't where I expected I finally tracked it down and went #-o

Everything seems back to normal now.  I love wasting whole days on non problems that I create myself!  Thanks for the help.

---

### Post by dream_coder on 2010-08-04
I am glad you found the problem, it is one of the things I love about linux solving problems and when I finally do and it takes days it makes it so much more worth it and the community is always full of ideas.

:)

---

