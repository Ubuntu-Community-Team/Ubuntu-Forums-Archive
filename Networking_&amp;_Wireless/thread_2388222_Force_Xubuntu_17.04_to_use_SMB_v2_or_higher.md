---
title: "Force Xubuntu 17.04 to use SMB v2 or higher"
date: 2018-03-30
forum: Networking &amp; Wireless
---

### Post by fozziebear on 2018-03-30
Since Microsoft have released the Creators edition it has automatically disabled SMB v1. As a result I can no longer browse the shares on my windows 10 machines from my Ubuntu machines.

On the face of it Microsoft have implemented a fix to resolve a security hole in SMB v1. It therefore makes no sense to reinstall SMB v1 on my windows machines. However how do I force Xubuntu 17.04 to use SMB v2 or higher.
This question has been asked before and the main response has been to edit the **/etc/samba/smb.conf** file. However on a new install there is no **/etc/samba/smb.conf **presumably as I have not installed Samba Server. On a machine which does have Samba Servber installed the /etc/samba/smb.conf looks nothing like the examples on other forums. There is a lot of commented out information but under the Global settings there are no entries apart from the workgroup which I changed.
To clarify all I want to do in File Manager is browse the network and connect to Windows shares. I can do that to all other windows 7 and early build windows 10 machines but not upgraded ones. I do not connect to the Ubuntu machines from Windows machines.
Should there already be entries in the Global section such as 
[COLOR=#111111][FONT=Consolas]client min protocol = SMB2
[/FONT][/COLOR][COLOR=#111111][FONT=Consolas]client max protocol = SMB3
[/FONT][/COLOR]or are there no existing entries and I have to add these from scratch?
I am a Linux newbie and learning all the time but struggle with Terminal and Nano. Is there a graphical program like Mousepad that allows you to edit the file with Sudo permissions?

As an aside is there a valid technical reason for smb v1 to still be included in Linux builds considering how old the technology is? Or am I missing the point
Many thanks
Fozzie

---

### Post by jeremy31 on 2018-03-30
Unfortunately Ubuntu 17.04 is no longer supported and isn't patched for spectre/meltdown.  Please switch to 16.04 or 17.10

---

### Post by fozziebear on 2018-03-30
Apologies Not sure why I said 17.04 confused with 16.04 on one machine. I am actually using 17.10
Fozzy

---

### Post by Morbius1 on 2018-03-30
Sounds like a bad install to me.

** smb.conf exists by default in Xubuntu 17.04 [COLOR=#0000cd]-- same for 17.10[/COLOR]
** mousepad exists by default in Xubuntu 17.04[COLOR=#0000cd] -- same for 17.10[/COLOR]

gksu isn't installed by default so you will need to add it so that you can run:
```
gksu mousepad /etc/samba/smb.conf
```
If you don't want to add gksu you can run it this way:
```
sudo -H mousepad /etc/samba/smb.conf
```
> Should there already be entries in the Global section such as 
[COLOR=#111111][FONT=Consolas]client min protocol = SMB2
[/FONT][/COLOR][COLOR=#111111][FONT=Consolas]client max protocol = SMB3
[/FONT][/COLOR]or are there no existing entries and I have to add these from scratch?
smb.conf is a file you use to add to or override the default settings - which are located elsewhere - of both samba client and server. The default settings set client max to SMB1 and the min value pre-dates SMB1. 

If you want to change the defaults to the values you listed above you will have to add them to your smb.conf - I would put them in the [global] section under the workgroup line.

Please note that if you set the max protocol to anything other than NT1 ( what samba calls SMB1 ) it will disable host browsing completly. You will howver be able to connect to a Windos machine that disabled SMB1 but you will have to connect to it explicitly by name or ip address as in smb://192.168.0.100 in Thunar.

---

### Post by fozziebear on 2018-03-30
Thanks for detailed response Morbius1.
I have checked on two installations (both clean installs from ISO's downloaded from XuBuntu website). One is 17.10 and the other 17.10.1. Neither have a folder under ```
/etc
``` called samba. Could this be a hidden folder? If so How do I view it? 
I assume the  ***/etc*** folder can be viewed in file manager and is the one listed below ***dev*** and above ***home***?? Unless I am looking in the wrong place!!!!

I tried running ```
[COLOR=#000000][FONT=&quot]sudo -H mousepad /etc /samba /smb.conf[/FONT][/COLOR]
``` but I get warning errors.  In terminal a ***gtk-Warning Theme Parsing Error.......outside border is deprecated.....*** 
Mousepad opens with a blank page containg no text like Global etc like other systems with text commented out.

I seem to remember having to manually install Samaba on Xubuntu 14 but both 16.04 and 17.10 browse a windows network and connect to a windows share without error except Windows 10. I had assumed that the samba client was therefore built in.

Fozzie

---

### Post by Morbius1 on 2018-03-30
I can not explain your symptoms. I can run Xubuntu 17.10 from the install disc and smb.conf is present

What exactly do you see when you run:
```
ls -l /etc
```
Are you sure you aren't running MATE?

---

### Post by fozziebear on 2018-03-31
Hi Morbius 1
I am running Xubuntu which I believe has XFCE?
Below is the output from terminal after running ```
[COLOR=#000000][FONT=&amp]ls -l /etc[/FONT][/COLOR]
```

```
john@Xubuntu-Pavillion:~$ ls -l /etc
total 1116
drwxr-xr-x  3 root root    4096 Jan  5 21:09 acpi
-rw-r--r--  1 root root    3028 Jan  5 21:04 adduser.conf
drwxr-xr-x  2 root root    4096 Mar 29 16:36 alternatives
-rw-r--r--  1 root root     401 May 29  2017 anacrontab
drwxr-xr-x  3 root root    4096 Mar 29 16:29 apache2
drwxr-xr-x  6 root root    4096 Jan  5 21:06 apm
drwxr-xr-x  3 root root    4096 Mar 29 16:20 apparmor
drwxr-xr-x  8 root root    4096 Mar 29 16:20 apparmor.d
drwxr-xr-x  5 root root    4096 Jan  5 21:09 apport
-rw-r--r--  1 root root     769 Aug  4  2017 appstream.conf
drwxr-xr-x  6 root root    4096 Mar 29 16:28 apt
drwxr-xr-x  3 root root    4096 Jan  5 21:10 avahi
-rw-r--r--  1 root root    2188 May 17  2017 bash.bashrc
-rw-r--r--  1 root root      45 Aug 12  2015 bash_completion
drwxr-xr-x  2 root root    4096 Mar 29 16:17 bash_completion.d
-rw-r--r--  1 root root     367 Jan 27  2016 bindresvport.blacklist
drwxr-xr-x  2 root root    4096 Oct  4 13:28 binfmt.d
drwxr-xr-x  2 root root    4096 Jan  5 21:08 bluetooth
-rw-r-----  1 root root      33 Jan  5 21:09 brlapi.key
drwxr-xr-x  7 root root    4096 Jan  5 21:08 brltty
-rw-r--r--  1 root root   23499 Aug  7  2017 brltty.conf
drwxr-xr-x  3 root root    4096 Jan  5 21:04 ca-certificates
-rw-r--r--  1 root root    6488 Jan  5 21:05 ca-certificates.conf
drwxr-xr-x  2 root root    4096 Jan  5 21:08 calendar
drwxr-s---  2 root dip     4096 Jan  5 21:09 chatscripts
drwxr-xr-x  4 root root    4096 Mar 29 16:24 chromium-browser
drwxr-xr-x  2 root root    4096 Jan  5 21:05 console-setup
drwxr-xr-x  2 root root    4096 Jan  5 21:09 cron.d
drwxr-xr-x  2 root root    4096 Jan  5 21:10 cron.daily
drwxr-xr-x  2 root root    4096 Jan  5 21:05 cron.hourly
drwxr-xr-x  2 root root    4096 Jan  5 21:08 cron.monthly
-rw-r--r--  1 root root     722 Aug 21  2017 crontab
drwxr-xr-x  2 root root    4096 Mar 29 16:14 cron.weekly
drwxr-xr-x  5 root lp      4096 Mar 31 00:12 cups
drwxr-xr-x  2 root root    4096 Jan  5 21:10 cupshelpers
drwxr-xr-x  4 root root    4096 Jan  5 21:04 dbus-1
-rw-r--r--  1 root root    2969 Jul 12  2017 debconf.conf
-rw-r--r--  1 root root      12 Apr 30  2015 debian_version
drwxr-xr-x  2 root root    4096 Mar 29 16:30 default
-rw-r--r--  1 root root     604 Oct 31  2016 deluser.conf
drwxr-xr-x  2 root root    4096 Jan  5 21:05 depmod.d
drwxr-xr-x  4 root root    4096 Mar 29 16:17 dhcp
drwxr-xr-x  2 root root    4096 Mar 29 16:00 dictionaries-common
drwxr-xr-x  3 root root    4096 Jan  5 21:06 doc-base
drwxr-xr-x  4 root root    4096 Jan  5 21:04 dpkg
-rw-r--r--  1 root root    9129 Oct  3 13:49 drirc
drwxr-xr-x  3 root root    4096 Jan  5 21:08 emacs
-rw-r--r--  1 root root      96 Jan  5 21:04 environment
-rw-r--r--  1 root root    9103 Sep 12  2017 ffserver.conf
drwxr-xr-x  2 root root    4096 Mar 29 16:20 firefox
drwxr-xr-x  4 root root    4096 Jan  5 21:09 fonts
-rw-rw-r--  1 root root     550 Mar 29 15:50 fstab
-rw-r--r--  1 root root     280 Jun 20  2014 fuse.conf
drwxr-xr-x  3 root root    4096 Jan  5 21:07 fwupd
-rw-r--r--  1 root root     610 Sep  1  2017 fwupd.conf
-rw-r--r--  1 root root    2584 Aug  2  2017 gai.conf
drwxr-xr-x  5 root root    4096 Jan  5 21:07 gconf
drwxr-xr-x  2 root root    4096 Jan  5 21:10 gdb
drwxr-xr-x  2 root root    4096 Mar 29 16:30 get_iplayer
drwxr-xr-x  4 root root    4096 Jan  5 21:06 ghostscript
drwxr-xr-x  2 root root    4096 Jan  5 21:08 gnome
drwxr-xr-x  2 root root    4096 Jan  5 21:10 gnome-system-tools
drwxr-xr-x  2 root root    4096 Jan  5 21:08 groff
-rw-r--r--  1 root root     975 Mar 29 15:58 group
-rw-------  1 root root     971 Mar 29 15:58 group-
drwxr-xr-x  2 root root    4096 Mar 29 16:17 grub.d
-rw-r-----  1 root shadow   815 Mar 29 15:58 gshadow
-rw-------  1 root root     811 Mar 29 15:58 gshadow-
drwxr-xr-x  3 root root    4096 Jan  5 21:06 gss
drwxr-xr-x  2 root root    4096 Jan  5 21:08 gtk-2.0
drwxr-xr-x  2 root root    4096 Jan  5 21:10 gtk-3.0
drwxr-xr-x  2 root root    4096 Sep  4  2017 guest-session
-rw-r--r--  1 root root    6748 Oct 29  2012 hddtemp.db
-rw-r--r--  1 root root    4781 Jan 24  2017 hdparm.conf
-rw-r--r--  1 root root      92 Oct 22  2015 host.conf
-rw-r--r--  1 root root      18 Mar 29 15:57 hostname
-rw-r--r--  1 root root     232 Mar 29 15:57 hosts
-rw-r--r--  1 root root     411 Jan  5 21:09 hosts.allow
-rw-r--r--  1 root root     711 Jan  5 21:09 hosts.deny
drwxr-xr-x  2 root root    4096 Jan  5 21:10 hp
drwxr-xr-x  3 root root    4096 Jan  5 21:07 ifplugd
drwxr-xr-x  2 root root    4096 Jan  5 21:08 ImageMagick-6
drwxr-xr-x  2 root root    4096 Mar 29 16:17 init
drwxr-xr-x  2 root root    4096 Mar 29 16:20 init.d
drwxr-xr-x  5 root root    4096 Mar 29 16:20 initramfs-tools
-rw-r--r--  1 root root    1748 Sep 17  2016 inputrc
-rw-r--r--  1 root root      71 Feb  9  2017 inxi.conf
drwxr-xr-x  3 root root    4096 Mar 29 16:17 iproute2
-rw-r--r--  1 root root      20 Oct 16 08:46 issue
-rw-r--r--  1 root root      13 Oct 16 08:46 issue.net
drwxr-xr-x  6 root root    4096 Jan  5 21:05 kernel
-rw-r--r--  1 root root     110 Mar 29 16:02 kernel-img.conf
-rw-r--r--  1 root root    1308 May 22  2017 kerneloops.conf
drwxr-xr-x  2 root root    4096 Jan  5 21:05 ldap
-rw-r--r--  1 root root   78190 Mar 29 16:37 ld.so.cache
-rw-r--r--  1 root root      34 Jan 27  2016 ld.so.conf
drwxr-xr-x  2 root root    4096 Mar 29 16:14 ld.so.conf.d
-rw-r--r--  1 root root     267 Oct 22  2015 legal
-rw-r--r--  1 root root      27 Jan  8  2015 libao.conf
-rw-r--r--  1 root root     191 Aug  5  2017 libaudit.conf
drwxr-xr-x  2 root root    4096 Jan  5 21:08 libnl-3
drwxr-xr-x  2 root root    4096 Apr 28  2017 libpaper.d
drwxr-xr-x  2 root root    4096 Mar 29 16:00 libreoffice
drwxr-xr-x  3 root root    4096 Mar 29 15:58 lightdm
drwxr-xr-x  4 root root    4096 Mar 29 16:30 lighttpd
-rw-r--r--  1 root root    1251 Oct 12 16:50 lintianrc
-rw-r--r--  1 root root    2995 Oct 11 21:21 locale.alias
-rw-r--r--  1 root root    9303 Mar 29 16:18 locale.gen
lrwxrwxrwx  1 root root      33 Mar 29 15:58 localtime -> /usr/share/zoneinfo/Europe/London
drwxr-xr-x  3 root root    4096 Jan  5 21:05 logcheck
-rw-r--r--  1 root root   10551 Aug 21  2017 login.defs
-rw-r--r--  1 root root     703 Aug 21  2017 logrotate.conf
drwxr-xr-x  2 root root    4096 Jan  5 21:10 logrotate.d
-rw-r--r--  1 root root      99 Oct 16 08:46 lsb-release
-rw-r--r--  1 root root   14867 Oct 13  2016 ltrace.conf
-r--r--r--  1 root root      33 Mar 29 16:08 machine-id
-rw-r--r--  1 root root     111 Sep  4  2017 magic
-rw-r--r--  1 root root     111 Sep  4  2017 magic.mime
-rw-r--r--  1 root root   35941 Mar 29 16:36 mailcap
-rw-r--r--  1 root root     449 Jul 15  2016 mailcap.order
-rw-r--r--  1 root root    5174 Dec 13  2016 manpath.config
-rw-r--r--  1 root root   24301 Jul 15  2016 mime.types
-rw-r--r--  1 root root     973 Aug  4  2017 mke2fs.conf
drwxr-xr-x  2 root root    4096 Jan  5 21:08 modprobe.d
-rw-r--r--  1 root root     195 Jan  5 21:05 modules
drwxr-xr-x  2 root root    4096 Jan  5 21:10 modules-load.d
lrwxrwxrwx  1 root root      19 Mar 29 16:01 mtab -> ../proc/self/mounts
-rw-r--r--  1 root root    9333 Jul 21  2017 nanorc
drwxr-xr-x  2 root root    4096 Jan  5 21:14 netplan
drwxr-xr-x  6 root root    4096 Mar 29 15:57 network
drwxr-xr-x  7 root root    4096 Jan  5 21:10 NetworkManager
-rw-r--r--  1 root root      91 Oct 22  2015 networks
drwxr-xr-x  2 root root    4096 Jan  5 21:05 newt
-rw-r--r--  1 root root     529 Jan  5 21:10 nsswitch.conf
drwxr-xr-x  2 root root    4096 Mar 29 16:29 openal
drwxr-xr-x  2 root root    4096 Jan  5 21:04 opt
lrwxrwxrwx  1 root root      21 Mar 29 15:50 os-release -> ../usr/lib/os-release
drwxr-xr-x  2 root root    4096 Jan  5 21:10 PackageKit
-rw-r--r--  1 root root     552 Apr 21  2017 pam.conf
drwxr-xr-x  2 root root    4096 Mar 29 16:14 pam.d
-rw-rw-r--  1 root root       3 Mar 29 16:01 papersize
-rw-r--r--  1 root root    2237 Mar 29 15:58 passwd
-rw-------  1 root root    2230 Mar 29 15:58 passwd-
drwxr-xr-x  2 root root    4096 Jan  5 21:08 pcmcia
drwxr-xr-x  5 root root    4096 Jan  5 21:10 perl
drwxr-xr-x  4 root root    4096 Jan  5 21:07 pki
drwxr-xr-x  3 root root    4096 Jan  5 21:06 pm
-rw-r--r--  1 root root    7649 Jan  5 21:10 pnm2ppa.conf
drwxr-xr-x  5 root root    4096 Jan  5 21:06 polkit-1
-rw-rw-r--  1 root root     350 Mar 29 16:01 popularity-contest.conf
drwxr-xr-x  7 root dip     4096 Jan  5 21:09 ppp
-rw-r--r--  1 root root     581 Apr 22  2016 profile
drwxr-xr-x  2 root root    4096 Jan  5 21:10 profile.d
-rw-r--r--  1 root root    2932 Dec 26  2016 protocols
drwxr-xr-x  2 root root    4096 Mar 29 16:20 pulse
drwxr-xr-x  2 root root    4096 Jan  5 21:08 purple
drwxr-xr-x  2 root root    4096 Jan  5 21:09 python
drwxr-xr-x  2 root root    4096 Jan  5 21:06 python2.7
drwxr-xr-x  2 root root    4096 Jan  5 21:05 python3
drwxr-xr-x  2 root root    4096 Jan  5 21:04 python3.6
drwxr-xr-x  2 root root    4096 Mar 29 16:14 rc0.d
drwxr-xr-x  2 root root    4096 Mar 29 16:04 rc1.d
drwxr-xr-x  2 root root    4096 Mar 29 16:04 rc2.d
drwxr-xr-x  2 root root    4096 Mar 29 16:04 rc3.d
drwxr-xr-x  2 root root    4096 Mar 29 16:04 rc4.d
drwxr-xr-x  2 root root    4096 Mar 29 16:04 rc5.d
drwxr-xr-x  2 root root    4096 Mar 29 16:14 rc6.d
drwxr-xr-x  2 root root    4096 Mar 29 16:14 rcS.d
drwxr-xr-x  3 root root    4096 Jan  5 21:06 resolvconf
lrwxrwxrwx  1 root root      39 Mar 29 15:57 resolv.conf -> ../run/systemd/resolve/stub-resolv.conf
-rwxr-xr-x  1 root root     268 Jul 21  2017 rmt
-rw-r--r--  1 root root     887 Dec 26  2016 rpc
-rw-r--r--  1 root root    1359 Jun 26  2017 rsyslog.conf
drwxr-xr-x  2 root root    4096 Jan  5 21:09 rsyslog.d
drwxr-xr-x  3 root root    4096 Jan  5 21:10 sane.d
-rw-r--r--  1 root root    4038 Aug 21  2017 securetty
drwxr-xr-x  4 root root    4096 Jan  5 21:05 security
drwxr-xr-x  2 root root    4096 Jan  5 21:04 selinux
-rw-r--r--  1 root root   10368 Apr  5  2017 sensors3.conf
drwxr-xr-x  2 root root    4096 Jan  5 21:08 sensors.d
-rw-r--r--  1 root root   19183 Dec 26  2016 services
-rw-r-----  1 root shadow  1245 Mar 29 15:58 shadow
-rw-------  1 root root    1148 Mar 29 15:58 shadow-
-rw-r--r--  1 root root      73 Jan  5 21:04 shells
drwxr-xr-x  3 root root    4096 Jan  5 21:10 skel
drwxr-xr-x  4 root root    4096 Jan  5 21:10 speech-dispatcher
drwxr-xr-x  2 root root    4096 Mar 29 16:18 ssh
drwxr-xr-x  4 root root    4096 Mar 29 16:18 ssl
-rw-r--r--  1 root root      18 Mar 29 15:58 subgid
-rw-------  1 root root       0 Jan  5 21:04 subgid-
-rw-r--r--  1 root root      18 Mar 29 15:58 subuid
-rw-------  1 root root       0 Jan  5 21:04 subuid-
-r--r-----  1 root root     755 Jun 12  2017 sudoers
drwxr-xr-x  2 root root    4096 Jan  5 21:05 sudoers.d
-rw-r--r--  1 root root    3174 Jun 12  2017 sudoers.dist
-rw-r--r--  1 root root    2683 Jul 10  2016 sysctl.conf
drwxr-xr-x  2 root root    4096 Jan  5 21:05 sysctl.d
drwxr-xr-x  5 root root    4096 Jan  5 21:05 systemd
drwxr-xr-x  2 root root    4096 Jan  5 21:04 terminfo
drwxr-xr-x  2 root root    4096 Jan  5 21:09 thermald
drwxr-xr-x  2 root root    4096 Mar 29 16:00 thunderbird
-rw-r--r--  1 root root      14 Mar 29 15:58 timezone
drwxr-xr-x  2 root root    4096 Mar 29 16:36 timidity
drwxr-xr-x  2 root root    4096 Oct  4 13:28 tmpfiles.d
-rw-r--r--  1 root root    1260 Mar 16  2016 ucf.conf
drwxr-xr-x  4 root root    4096 Jan  5 21:05 udev
drwxr-xr-x  2 root root    4096 Jan  5 21:09 udisks2
drwxr-xr-x  3 root root    4096 Jan  5 21:09 ufw
-rw-r--r--  1 root root     403 Apr 28  2017 updatedb.conf
drwxr-xr-x  3 root root    4096 Mar 29 16:20 update-manager
drwxr-xr-x  2 root root    4096 Mar 29 16:20 update-motd.d
drwxr-xr-x  2 root root    4096 Sep  6  2017 update-notifier
drwxr-xr-x  2 root root    4096 Jan  5 21:09 UPower
-rw-r--r--  1 root root    1523 Aug 26  2017 usb_modeswitch.conf
drwxr-xr-x  2 root root    4096 Aug 25  2017 usb_modeswitch.d
-rw-r--r--  1 root root      51 Feb 19  2016 vdpau_wrapper.cfg
drwxr-xr-x  2 root root    4096 Jan  5 21:05 vim
lrwxrwxrwx  1 root root      23 Mar 29 15:50 vtrgb -> /etc/alternatives/vtrgb
-rw-r--r--  1 root root    4942 Oct 23 20:17 wgetrc
drwxr-xr-x  2 root root    4096 Jan  5 21:09 wpa_supplicant
drwxr-xr-x 11 root root    4096 Jan  5 21:10 X11
drwxr-xr-x  9 root root    4096 Jan  5 21:08 xdg
drwxr-xr-x  2 root root    4096 Jan  5 21:10 xfce4
-rw-r--r--  1 root root     477 Dec 20 18:20 zsh_command_not_found
john@Xubuntu-Pavillion:~$ 

```

Hope this is of assistance
Fozzie

---

### Post by Morbius1 on 2018-03-31
I booted into a Xubuntu 17.10 Install DVD and this is what Xubuntu installs by default:

```
libsmbclient
libwbclient0
python-samba
samba-common
samba-common-bin
samba-libs
```

I would install them all.

If you want the samba server package then install that package:
```
samba
```

---

### Post by fozziebear on 2018-03-31
Thanks for the quick reply. I don't understand why the components you have listed are not being installed. I downloaded both ISO's from the Xubuntu repositories and installed them on a clean disk. 

That said, how is it that I can already browse network shares and connect to them without samba being installed? The only shares I cannot connect to are Windows 10 Creators edition where smb v1 has been removed as part of the upgrade process. All other windows shares are accessible through File Manager. I am just prompted for a user name and password of the machine I am connecting to.?
Fozzie

---

### Post by Morbius1 on 2018-03-31
> That said, how is it that I can already browse network shares and connect to them without samba being installed?
Thunar uses a gvfs module gvfsd-smb-browse to "discover" other smb hosts. gvfsd-smb-browse comes from the package gvfs-backends. One of the dependencies of gvfs-backends is libsmbclient. It's libsmbclient that does all the work and ultimately makes the connection.

libsmbclient looks to smb.conf for any client side modifications the user may make. Although I have no first hand knowledge of this since I don't remember your situation ever mentioned before,  it apparently doesn't stop it from doing it's job if there is no smb.conf.

If you also do not have libsmbclient then my guess as to how you can connect to your other machines ..... magic.

As for why you don't have all of these packages installed by default I honestly do not know.

[COLOR=#0000cd]**Edit**[/COLOR]: More of an FYI but if you can wait a month or so for Xubuntu 18.04 the default client max protocol will be set to SMB3 by default. As is most things Linux however that will bring a host of other problems: [Bionic Beaver can not discover samba hosts - netbios. ]("https://ubuntuforums.org/showthread.php?t=2384959")

---

### Post by fozziebear on 2018-04-01
Firstly many thanks [COLOR=#000000]Morbius1 [/COLOR]for all your assistance and especially your patience with a Linux Newbie!!

I was brought up with windows and networking and have learned a fair amount about it from courses and supporting clients, but was never really initiated with command line use. Over the years I have used command line more and more but its still my area of weakness and as such transition to Linux has been slow particularly as there are some differences between different flavours of linux. That said I will persevere and am learning. 

During searches to esatablish if Samba was installed by default in Xubuntu I noted from the Xubuntu website that Thunar can browse networks but" [COLOR=#111111][FONT=&quot]In order to connect to Samba networks (Windows shares) using the [/FONT][/COLOR][COLOR=#111111][FONT=&quot]**Thunar File Manager**[/FONT][/COLOR][COLOR=#111111][FONT=&quot], you will need to have the package [/FONT][/COLOR][IMG]https://docs.xubuntu.org/1710/libs-common/images/icon_package.png[/IMG]gvfs-backends[COLOR=#111111][FONT=&quot]installed."  
[/FONT][/COLOR]
As you rightly assume I suppose it is gvs-backends thats currently doing the work. I also notice I also have Gigolo installed by default. I believe this is this module that allows me to "bookmark" remote network shares so perhaps there is no magic.

 Finally thank you for the tip on Ubuntu 18  and inclusion of SMBv3 by default. This seems the sensible way forward and I can test a live CD before upgrading to see if it resolves my current issue.
Thank you again for you help.
Fozzie

---

