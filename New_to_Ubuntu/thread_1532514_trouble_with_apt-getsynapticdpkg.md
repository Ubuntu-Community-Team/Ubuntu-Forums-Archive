---
title: "trouble with apt-get/synaptic/dpkg"
date: 2010-07-16
forum: New to Ubuntu
---

### Post by phobophilia on 2010-07-16
Hey all- I'm having trouble running a routine update, embarrassingly enough. Running Ubuntu 10.04, Kernel 2.6.32-23-generic, was up to date as of 2 days ago.

I try to run it through synaptic in the regular way, right? After downloading the new packages, the following comes up and it aborts the operation:

Could not exec dpkg!
E: Sub-process /usr/bin/dpkg returned an error code (100)
A package failed to install. Trying to recover:
sh: dpkg: Permission denied.

Of this, I understand "there's a permission problem." Okay, so I try the terminal:

(me)@(computer):~$ sudo apt-get update
sudo: apt-get: command not found

That's weird. Apt-get? Are you out there? So...

(me)@(computer):~$ man apt-get
Manual page apt-get(8) line?/? (END)

So tell me, gurus of linux: what am I doing wrong here? Many thanks for the help.

---

### Post by nothingspecial on 2010-07-16
Have you done anything outside of the ordinary to your system recently?

---

### Post by phobophilia on 2010-07-16
Nothing outside of the ordinary updates. I'm a pretty low-key user, but I'm trying to learn. Apt-get being gone makes absolutely no sense to me- it has downloaded the packages, but then...?

---

### Post by phobophilia on 2010-07-16
Something else strange: I went to do a bit of security tweaking for safety's sake, and found this:

(me)@(computer):~$ sudo chown root:admin /bin/sudo
[sudo] password for (me): 
chown: cannot access `/bin/sudo': No such file or directory
(me)@(computer):~$ man sudo
man: fork failed: Resource temporarily unavailable

I checked it out, and there is, in fact, no sudo file in /bin. Whaa?

---

### Post by sisco311 on 2010-07-16
> **phobophilia said:**
> Something else strange: I went to do a bit of security tweaking for safety's sake, and found this:

(me)@(computer):~$ sudo chown root:admin /bin/sudo
[sudo] password for (me): 
chown: cannot access `/bin/sudo': No such file or directory
(me)@(computer):~$ man sudo
man: fork failed: Resource temporarily unavailable

I checked it out, and there is, in fact, no sudo file in /bin. Whaa?

sudo is in /usr/bin, chown clears the setuid bit. DON'T CHANGE THE OWNER OF sudo!

What are the permissions of dpkg and apt-get?
```
ls -al /usr/bin/dpkg
ls -al /usr/bin/apt-get
```

---

### Post by Zeike on 2010-07-16
> **phobophilia said:**
> I checked it out, and there is, in fact, no sudo file in /bin. Whaa?

Thats because sudo is in /usr/bin/

EDIT: sisco311 beat me to it.

---

### Post by phobophilia on 2010-07-16
About chown: ah, thanks for the heads up. Like I said, I'm learning, and every bit helps.

The permissions are thus:
(me)@(computer):~$ ls -al /usr/bin/dpkg
---------- 1 root root 379700 2010-06-28 12:27 /usr/bin/dpkg
(me)@(computer):~$ ls -al /usr/bin/apt-get
---------- 1 root root 116996 2010-05-14 11:37 /usr/bin/apt-get

---

### Post by sisco311 on 2010-07-16
> **phobophilia said:**
> About chown: ah, thanks for the heads up. Like I said, I'm learning, and every bit helps.

The permissions are thus:
(me)@(computer):~$ ls -al /usr/bin/dpkg
---------- 1 root root 379700 2010-06-28 12:27 /usr/bin/dpkg
(me)@(computer):~$ ls -al /usr/bin/apt-get
---------- 1 root root 116996 2010-05-14 11:37 /usr/bin/apt-get

Change the permissions to 0755:
```
sudo chmod 0755 /usr/bin/apt-get
sudo chmod 0755 /usr/bin/dpkg
```

Are the permissions of other file in /usr/bin correct?
```
ls -al /usr/bin/
```

---

### Post by phobophilia on 2010-07-16
Changed permissions as you recommended. The output for that line of code is as follows, and I haven't a clue as to whether this output means things are kosher or not:

-rwxr-xr-x  1 root   root       9604 2010-03-24 12:08 prezip-bin
lrwxrwxrwx  1 root   root         11 2010-04-29 15:13 print -> run-mailcap
-rwxr-xr-x  1 root   root        428 2010-07-12 13:40 printafm
-rwxr-xr-x  1 root   root      30216 2010-03-04 22:29 printenv
-rwxr-xr-x  1 root   root      17832 2009-11-10 11:12 printerbanner
-rwxr-xr-x  1 root   root       5640 2010-03-25 04:12 printer-profile
-rwxr-xr-x  1 root   root      38464 2010-03-04 22:29 printf
-rwxr-xr-x  1 root   root       9744 2010-02-10 19:58 protoc
-rwxr-xr-x  1 root   root       9439 2010-04-23 04:22 prove
-rwxr-xr-x  1 root   root      13760 2010-01-18 03:10 prtstat
-rwxr-xr-x  1 root   root        786 2010-07-12 13:40 ps2ascii
-rwxr-xr-x  1 root   root       2825 2010-07-12 13:40 ps2epsi
lrwxrwxrwx  1 root   root         24 2010-07-13 21:39 ps2pdf -> /etc/alternatives/ps2pdf
-rwxr-xr-x  1 root   root        260 2010-07-12 13:40 ps2pdf12
-rwxr-xr-x  1 root   root        260 2010-07-12 13:40 ps2pdf13
-rwxr-xr-x  1 root   root        260 2010-07-12 13:40 ps2pdf14
-rwxr-xr-x  1 root   root       1130 2010-07-12 13:40 ps2pdfwr
-rwxr-xr-x  1 root   root        676 2010-07-12 13:40 ps2ps
-rwxr-xr-x  1 root   root        704 2010-07-12 13:40 ps2ps2
lrwxrwxrwx  1 root   root          8 2010-07-13 21:38 ps2txt -> ps2ascii
-rwxr-xr-x  2 root   root      53325 2010-04-23 04:22 psed
lrwxrwxrwx  1 root   root          9 2010-04-29 15:13 psfaddtable -> psfxtable
lrwxrwxrwx  1 root   root          9 2010-04-29 15:13 psfgettable -> psfxtable
lrwxrwxrwx  1 root   root          9 2010-04-29 15:13 psfstriptable -> psfxtable
-rwxr-xr-x  1 root   root      17880 2010-03-12 02:05 psfxtable
-rwxr-xr-x  1 root   root      18052 2010-01-18 03:10 pstree
lrwxrwxrwx  1 root   root          6 2010-04-29 15:13 pstree.x11 -> pstree
-rwxr-xr-x  2 root   root      36601 2010-04-23 04:22 pstruct
-rwxr-xr-x  1 root   root       2788 2010-04-23 04:22 ptar
-rwxr-xr-x  1 root   root       2514 2010-04-23 04:22 ptardiff
-rwxr-xr-x  1 root   root      63132 2010-03-04 22:29 ptx
-rwxr-xr-x  1 root   root      66880 2010-03-26 19:40 pulseaudio
-rwxr-xr-x  1 root   root       7962 2010-03-09 14:18 purple-remote
-rwxr-xr-x  1 root   root        776 2010-03-09 14:18 purple-send
-rwxr-xr-x  1 root   root        635 2010-03-09 14:18 purple-send-async
-rwxr-xr-x  1 root   root      11965 2010-03-09 14:18 purple-url-handler
-rwxr-xr-x  1 root   root       5536 2009-12-16 14:34 pwdx
-rwxr-xr-x  1 root   root       3752 2010-03-31 10:26 py3_compilefiles
-rwxr-xr-x  1 root   root      94805 2010-03-31 10:26 pycentral
-rwxr-xr-x  1 root   root       8615 2010-03-31 13:09 pyclean
-rwxr-xr-x  1 root   root      14241 2010-03-31 13:09 pycompile
-rwxr-xr-x  1 root   root       3723 2010-03-31 10:26 py_compilefiles
lrwxrwxrwx  1 root   root          8 2010-04-29 15:13 pydoc -> pydoc2.6
-rwxr-xr-x  1 root   root         79 2010-04-16 09:59 pydoc2.6
lrwxrwxrwx  1 root   root         12 2010-04-29 15:13 pygettext -> pygettext2.6
-rwxr-xr-x  1 root   root      22103 2010-04-16 09:59 pygettext2.6
-rwxr-xr-x  1 root   root        545 2010-04-15 00:06 pyhtmlizer
lrwxrwxrwx  1 root   root          9 2010-04-29 15:13 python -> python2.6
lrwxrwxrwx  1 root   root          9 2010-04-29 15:13 python2 -> python2.6
-rwxr-xr-x  1 root   root    2288240 2010-04-16 10:06 python2.6
lrwxrwxrwx  1 root   root         29 2010-04-29 15:13 pyversions -> ../share/python/pyversions.py
-rwxr-xr-x  1 root   root      51236 2010-04-14 02:26 qdbus
-rwxr-xr-x  1 root   root      53492 2010-03-25 04:12 qpdldecode
-rwxr-xr-x  1 root   root      50908 2010-06-18 06:15 ranlib
-rwxr-xr-x  1 root   root       5516 2009-11-17 14:25 rarian-example
-rwxr-xr-x  1 root   root       1495 2009-11-17 14:25 rarian-sk-config
-rwxr-xr-x  1 root   root        563 2009-11-17 14:25 rarian-sk-extract
-rwxr-xr-x  1 root   root       5512 2009-11-17 14:25 rarian-sk-gen-uuid
-rwxr-xr-x  1 root   root      71464 2009-11-17 14:25 rarian-sk-get-cl
-rwxr-xr-x  1 root   root        399 2009-11-17 14:25 rarian-sk-get-content-list
-rwxr-xr-x  1 root   root        419 2009-11-17 14:25 rarian-sk-get-extended-content-list
-rwxr-xr-x  1 root   root        382 2009-11-17 14:25 rarian-sk-get-scripts
-rwxr-xr-x  1 root   root       1171 2009-11-17 14:25 rarian-sk-install
-rwxr-xr-x  1 root   root      79688 2009-11-17 14:25 rarian-sk-migrate
-rwxr-xr-x  1 root   root      67340 2009-11-17 14:25 rarian-sk-preinstall
-rwxr-xr-x  1 root   root        821 2009-11-17 14:25 rarian-sk-rebuild
-rwxr-xr-x  1 root   root       9525 2009-11-17 14:25 rarian-sk-update
lrwxrwxrwx  1 root   root         21 2010-04-29 15:13 rcp -> /etc/alternatives/rcp
-rwxr-xr-x  1 root   root     216212 2010-03-06 23:31 rdesktop
-rwxr-xr-x  1 root   root        298 2009-12-21 17:41 rdfpipe
-rwxr-xr-x  1 root   root     278444 2010-06-18 06:15 readelf
-rwxr-xr-x  1 root   root     172688 2010-03-19 15:43 readom
lrwxrwxrwx  1 root   root          7 2010-04-29 15:13 red -> /bin/ed
lrwxrwxrwx  1 root   root         24 2010-04-29 15:13 rename -> /etc/alternatives/rename
-rwxr-xr-x  1 root   root       5532 2010-03-22 13:51 rename.ul
-rwxr-xr-x  1 root   root       9620 2010-03-22 13:51 renice
lrwxrwxrwx  1 root   root          4 2010-04-29 15:13 reset -> tset
-rwxr-xr-x  1 root   root       9676 2010-03-31 05:47 resize
-rwxr-xr-x  1 root   root      13864 2010-03-12 02:05 resizecons
-rwxr-xr-x  1 root   root       5544 2010-03-22 13:51 rev
-rwxr-xr-x  1 root   root      30800 2010-04-09 06:35 rfcomm
-rwxr-xr-x  1 root   root         30 2010-03-04 23:47 rgrep
-rwxr-xr-x  1 root   root      30480 2010-06-25 07:00 rhythmbox
-rwxr-xr-x  1 root   root      22916 2010-06-25 07:00 rhythmbox-client
lrwxrwxrwx  1 root   root         24 2010-04-29 15:13 rlogin -> /etc/alternatives/rlogin
-rwxr-xr-x  1 root   root        173 2009-12-26 13:26 routef
-rwxr-xr-x  1 root   root       1262 2009-12-26 13:26 routel
-rwxr-xr-x  1 root   root    5388288 2010-04-09 11:29 rpcclient
-rwxr-xr-x  1 root   root      79684 2010-06-14 10:36 rpcgen
-rwxr-xr-x  1 root   root      13800 2010-06-14 10:35 rpcinfo
-rwxr-xr-x  1 root   root      21944 2009-12-05 16:41 rpl8
lrwxrwxrwx  1 root   root         21 2010-04-29 15:13 rsh -> /etc/alternatives/rsh
-rwxr-xr-x  1 root   root       2613 2009-12-07 09:01 rstart
-rwxr-xr-x  1 root   root       1435 2009-12-07 09:01 rstartd
-rwxr-xr-x  1 root   root     370328 2010-03-30 05:02 rsync
lrwxrwxrwx  1 root   root          6 2010-04-29 15:13 rtstat -> lnstat
-rwxr-xr-x  1 root   root      34364 2010-03-04 22:29 runcon
lrwxrwxrwx  1 root   root         25 2010-04-29 21:31 run_erl -> ../lib/erlang/bin/run_erl
-rwxr-xr-x  1 root   root      16898 2010-01-15 19:05 run-mailcap
-rwxr-xr-x  1 root   root         57 2010-03-24 12:08 run-with-aspell
lrwxrwxrwx  1 root   root         23 2010-04-29 15:13 rview -> /etc/alternatives/rview
-rwxr-xr-x  2 root   root      53325 2010-04-23 04:22 s2p
-rwxr-xr-x  1 root   root     129208 2010-04-14 22:24 sane-find-scanner
-rwxr-xr-x  1 root   root       9760 2009-12-08 08:00 savelog
-rwxr-xr-x  1 root   root      42940 2010-04-14 22:24 scanimage
-rwxr-xr-x  1 root   root      50616 2010-05-19 12:31 scp
-rwxr-sr-x  1 root   utmp     340604 2009-11-10 13:06 screen
-rwxr-xr-x  1 root   root       9648 2010-03-12 02:05 screendump
lrwxrwxrwx  1 root   root         23 2010-06-25 11:40 screen-launcher -> /usr/bin/byobu-launcher
lrwxrwxrwx  1 root   root         21 2010-06-25 11:40 screen-profiles-status -> /usr/bin/byobu-status
-rwxr-xr-x  1 root   root      13824 2010-03-22 13:51 script
-rwxr-xr-x  1 root   root       9656 2010-03-22 13:51 scriptreplay
lrwxrwxrwx  1 root   root         16 2010-04-29 15:13 scrollkeeper-config -> rarian-sk-config
lrwxrwxrwx  1 root   root         17 2010-04-29 15:13 scrollkeeper-extract -> rarian-sk-extract
lrwxrwxrwx  1 root   root         18 2010-04-29 15:13 scrollkeeper-gen-seriesid -> rarian-sk-gen-uuid
lrwxrwxrwx  1 root   root         16 2010-04-29 15:13 scrollkeeper-get-cl -> rarian-sk-get-cl
lrwxrwxrwx  1 root   root         26 2010-04-29 15:13 scrollkeeper-get-content-list -> rarian-sk-get-content-list
lrwxrwxrwx  1 root   root         35 2010-04-29 15:13 scrollkeeper-get-extended-content-list -> rarian-sk-get-extended-content-list
lrwxrwxrwx  1 root   root         21 2010-04-29 15:13 scrollkeeper-get-index-from-docpath -> rarian-sk-get-scripts
lrwxrwxrwx  1 root   root         21 2010-04-29 15:13 scrollkeeper-get-toc-from-docpath -> rarian-sk-get-scripts
lrwxrwxrwx  1 root   root         21 2010-04-29 15:13 scrollkeeper-get-toc-from-id -> rarian-sk-get-scripts
lrwxrwxrwx  1 root   root         17 2010-04-29 15:13 scrollkeeper-install -> rarian-sk-install
lrwxrwxrwx  1 root   root         20 2010-04-29 15:13 scrollkeeper-preinstall -> rarian-sk-preinstall
lrwxrwxrwx  1 root   root         17 2010-04-29 15:13 scrollkeeper-rebuilddb -> rarian-sk-rebuild
lrwxrwxrwx  1 root   root         17 2010-04-29 15:13 scrollkeeper-uninstall -> rarian-sk-install
lrwxrwxrwx  1 root   root         16 2010-04-29 15:13 scrollkeeper-update -> rarian-sk-update
-rwxr-xr-x  1 root   root      38820 2009-11-10 04:46 sctp_darn
-rwxr-xr-x  1 root   root      18024 2009-11-10 04:46 sctp_status
-rwxr-xr-x  1 root   root      26216 2009-11-10 04:46 sctp_test
-rwxr-xr-x  1 root   root      22136 2009-11-05 01:31 sdiff
-rwxr-xr-x  1 root   root      75112 2010-04-09 06:35 sdptool
-rwxr-xr-x  1 root   root     620152 2010-04-09 06:08 seahorse
-rwxr-xr-x  1 root   root     529316 2010-04-09 06:08 seahorse-daemon
lrwxrwxrwx  1 root   root         11 2010-04-29 15:13 see -> run-mailcap
-rwxr-xr-x  1 root   root        474 2010-01-20 19:05 select-default-iwrap
-rwxr-xr-x  1 root   root       1197 2010-04-08 20:45 select-editor
-rwxr-xr-x  1 root   root       1388 2010-04-08 20:45 sensible-browser
-rwxr-xr-x  1 root   root       1109 2010-04-08 20:45 sensible-editor
-rwxr-xr-x  1 root   root        288 2010-04-08 20:45 sensible-pager
-rwxr-xr-x  1 root   root      17988 2010-02-15 12:17 sensors
-rwxr-xr-x  1 root   root      14018 2010-02-15 12:17 sensors-conf-convert
-rwxr-xr-x  1 root   root      34336 2010-03-04 22:29 seq
lrwxrwxrwx  1 root   root         17 2010-04-29 15:13 service -> /usr/sbin/service
-rwxr-xr-x  1 root   root       9652 2010-03-19 18:51 sessreg
-rwxr-xr-x  1 root   root       9904 2010-03-22 13:51 setarch
-rwxr-xr-x  1 root   root       9636 2010-03-12 02:05 setkeycodes
-rwxr-xr-x  1 root   root       9684 2010-03-12 02:05 setleds
-rwxr-xr-x  1 root   root       5532 2010-03-12 02:05 setlogcons
-rwxr-xr-x  1 root   root       5604 2010-03-12 02:05 setmetamode
-rwxr-xr-x  1 root   root      13788 2010-03-09 17:08 setpci
-rwxr-xr-x  1 root   root       5520 2010-03-22 13:51 setsid
-rwxr-xr-x  1 root   root      22232 2010-03-22 13:51 setterm
-rwxr-xr-x  1 root   root      21988 2009-12-07 09:04 setxkbmap
-rwxr-xr-x  1 root   root      87488 2010-05-19 12:31 sftp
lrwxrwxrwx  1 root   root          6 2010-04-29 15:13 sg -> newgrp
-rwxr-xr-x  1 root   root      42604 2010-03-04 22:29 sha1sum
-rwxr-xr-x  1 root   root      46704 2010-03-04 22:29 sha224sum
-rwxr-xr-x  1 root   root      46704 2010-03-04 22:29 sha256sum
-rwxr-xr-x  1 root   root     104048 2010-03-04 22:29 sha384sum
-rwxr-xr-x  1 root   root     104048 2010-03-04 22:29 sha512sum
-rwxr-xr-x  1 root   root      82488 2010-04-15 01:15 shares-admin
-rwxr-xr-x  1 root   root       7655 2010-04-23 04:22 shasum
-rwxr-xr-x  1 root   root      13780 2010-03-12 02:05 showconsolefont
-rwxr-xr-x  1 root   root      13760 2010-03-07 01:28 showfont
-rwxr-xr-x  1 root   root       9652 2010-03-12 02:05 showkey
-rwxr-xr-x  1 root   root       5520 2010-03-19 18:51 showrgb
-rwxr-xr-x  1 root   root      55000 2010-03-04 22:29 shred
-rwxr-xr-x  1 root   root      38548 2010-03-04 22:29 shuf
-rwxr-xr-x  1 root   root     120744 2010-05-26 15:56 sigtool
-rwxr-xr-x  1 root   root     109136 2010-04-29 01:12 simple-scan
-rwxr-xr-x  1 root   root      22320 2010-06-18 06:15 size
-rwxr-xr-x  1 root   root      13804 2009-12-16 14:34 skill
-rwxr-xr-x  1 root   root      13780 2009-12-16 14:34 slabtop
lrwxrwxrwx  1 root   root          3 2010-06-15 17:51 slogin -> ssh
-rwxr-xr-x  1 root   root      53492 2010-03-25 04:12 slxdecode
-rwxr-xr-x  1 root   root      88756 2010-03-06 22:37 smartdimmer
-rwxr-xr-x  1 root   root    5242336 2010-04-09 11:29 smbcacls
-rwxr-xr-x  1 root   root    5168640 2010-04-09 11:29 smbclient
-rwxr-xr-x  1 root   root    5090784 2010-04-09 11:29 smbcquotas
-rwxr-xr-x  1 root   root    5197276 2010-04-09 11:29 smbget
-rwxr-xr-x  1 root   root    5094880 2010-04-09 11:29 smbpasswd
-rwxr-xr-x  1 root   root    2484556 2010-04-09 11:29 smbspool
-rwxr-xr-x  1 root   root       4910 2010-04-09 11:27 smbtar
-rwxr-xr-x  1 root   root    5070300 2010-04-09 11:29 smbtree
-rwxr-xr-x  1 root   root      17976 2009-12-07 09:01 smproxy
lrwxrwxrwx  1 root   root          5 2010-04-29 15:13 snice -> skill
-rwxr-xr-x  1 root   root      30344 2010-02-22 05:21 soelim
lrwxrwxrwx  1 root   root         33 2010-06-15 17:53 soffice -> ../lib/openoffice/program/soffice
lrwxrwxrwx  1 root   root         40 2010-06-15 17:55 software-center -> ../share/software-center/software-center
-rwxr-xr-x  1 root   root       4307 2010-04-15 01:02 software-properties-gtk
-rwxr-xr-x  1 root   root      79820 2010-03-04 22:29 sort
-rwxr-xr-x  1 root   root        142 2010-04-15 09:04 spd-conf
-rwxr-xr-x  1 root   root      14144 2010-04-15 09:05 spd-say
-rwxr-xr-x  1 root   root      22160 2010-03-28 19:02 speaker-test
-rwxr-xr-x  1 root   root     116764 2010-04-15 09:05 speech-dispatcher
-rwxr-xr-x  1 root   root       2369 2010-04-15 09:04 speechd-server-spawn
-rwxr-xr-x  1 root   root      17452 2010-04-23 04:22 splain
-rwxr-xr-x  1 root   root      54964 2010-03-04 22:29 split
-rwxr-xr-x  1 root   root       5524 2010-03-12 02:05 splitfont
-rwxr-xr-x  1 root   root      22076 2010-06-14 10:36 sprof
-rwxr-xr-x  1 root   root     321988 2010-05-19 12:31 ssh
-rwxr-xr-x  1 root   root     100324 2010-05-19 12:31 ssh-add
-rwxr-sr-x  1 root   ssh       79240 2010-05-19 12:31 ssh-agent
-rwxr-xr-x  1 root   root       1452 2010-05-19 12:31 ssh-argv0
lrwxrwxrwx  1 root   root         29 2010-04-29 15:13 ssh-askpass -> /etc/alternatives/ssh-askpass
-rwxr-xr-x  1 root   root       1316 2010-05-19 12:31 ssh-copy-id
-rwxr-xr-x  1 root   root     124904 2010-05-19 12:31 ssh-keygen
-rwxr-xr-x  1 root   root     174328 2010-05-19 12:31 ssh-keyscan
-rwxr-xr-x  1 root   root      88040 2010-05-19 12:31 ssh-vulnkey
lrwxrwxrwx  1 root   root         23 2010-04-29 21:31 start_embedded -> ../lib/erlang/bin/start
-rwxr-xr-x  1 root   root       1246 2010-03-26 19:37 start-pulseaudio-x11
-rwxr-xr-x  1 root   root       4481 2009-12-07 09:07 startx
-rwxr-xr-x  1 root   root      50824 2010-03-04 22:29 stat
-rwxr-xr-x  1 root   root    6307832 2010-03-30 00:45 stellarium
-rwxr-xr-x  1 root   root     206584 2010-02-15 12:35 strace
-rwxr-xr-x  1 root   root       5504 2009-11-26 18:22 stream
-rwxr-xr-x  1 root   root      22304 2010-06-18 06:15 strings
-rwxr-xr-x  1 root   root     192268 2010-06-18 06:15 strip
-rwsr-xr-x  2 root   root     127664 2010-06-18 16:40 sudo
-rwsr-xr-x  2 root   root     127664 2010-06-18 16:40 sudoedit
-rwxr-xr-x  1 root   root      38516 2010-03-04 22:29 sum
-rwxr-xr-x  1 root   root       3031 2010-02-04 12:42 su-to-root
-rwxr-xr-x  1 root   root      16368 2010-04-15 17:17 synclient
-rwxr-xr-x  1 root   root       9708 2010-04-15 17:17 syndaemon
-rwxr-xr-x  1 root   root      28956 2008-07-15 09:06 syslinux
-rwxr-xr-x  1 root   root       1421 2008-07-15 09:06 syslinux2ansi
-rwxr-xr-x  1 root   root         95 2010-05-03 09:58 system-config-printer
-rwxr-xr-x  1 root   root         80 2010-05-03 09:58 system-config-printer-applet
-rwxr-xr-x  1 root   root       9704 2010-03-06 22:33 tabs
-rwxr-xr-x  1 root   root      34432 2010-03-04 22:29 tac
-rwxr-xr-x  1 root   root      50864 2010-03-04 22:29 tail
-rwxr-xr-x  1 root   root        535 2010-04-15 00:06 tap2deb
-rwxr-xr-x  1 root   root        622 2010-04-15 00:06 tap2rpm
-rwxr-xr-x  1 root   root        603 2010-04-15 00:06 tapconvert
-rwxr-xr-x  1 root   root      22478 2010-03-19 19:33 tasksel
-rwxr-xr-x  1 root   root       9652 2010-03-22 13:51 taskset
-rwxr-xr-x  1 root   root     116396 2010-02-22 05:21 tbl
lrwxrwxrwx  1 root   root         23 2010-04-29 15:13 tclsh -> /etc/alternatives/tclsh
-rwxr-xr-x  1 root   root       5492 2009-11-06 06:49 tclsh8.4
-rwxr-xr-x  1 root   root      30240 2010-03-04 22:29 tee
lrwxrwxrwx  1 root   root         24 2010-04-29 15:13 telnet -> /etc/alternatives/telnet
-rwxr-xr-x  1 root   root      80056 2010-03-06 22:23 telnet.netkit
-rwxr-xr-x  1 root   root      26188 2010-03-04 22:29 test
lrwxrwxrwx  1 root   root         26 2010-04-29 15:13 testparm -> /etc/alternatives/testparm
-rwxr-xr-x  1 root   root     952660 2010-04-09 11:29 testparm.samba3
-rwxr-xr-x  1 root   root       2295 2009-11-13 13:45 tgz
-rwxr-xr-x  1 root   root      50852 2010-03-06 22:33 tic
-rwxr-xr-x  1 root   root      13960 2010-03-07 00:48 time
-rwxr-xr-x  1 root   root      94932 2010-04-15 01:15 time-admin
-rwxr-xr-x  1 root   root       9668 2009-12-16 14:34 tload
-rwxr-xr-x  1 root   root       9716 2010-03-06 22:33 toe
-rwxr-xr-x  1 root   root       1561 2010-04-29 02:11 tomboy
-rwxr-xr-x  1 root   root        570 2010-04-29 02:11 tomboy-panel
-rwxr-xr-x  1 root   root      68524 2009-12-16 14:34 top
-rwxr-xr-x  1 root   root      88984 2010-02-04 14:23 toshset
-rwxr-xr-x  1 root   root     463708 2010-05-19 10:38 totem
-rwxr-xr-x  1 root   root     151432 2010-05-19 10:38 totem-audio-preview
-rwxr-xr-x  1 root   root     155532 2010-05-19 10:38 totem-video-indexer
-rwxr-xr-x  1 root   root     167100 2010-05-19 10:38 totem-video-thumbnailer
lrwxrwxrwx  1 root   root         10 2010-04-29 15:13 touch -> /bin/touch
-rwxr-xr-x  1 root   root       9752 2010-03-06 22:33 tput
-rwxr-xr-x  1 root   root      46688 2010-03-04 22:29 tr
-rwxr-xr-x  1 root   root       9676 2010-03-11 18:12 tracepath
-rwxr-xr-x  1 root   root       9700 2010-03-11 18:12 tracepath6
lrwxrwxrwx  1 root   root         29 2010-04-29 15:13 traceroute6 -> /etc/alternatives/traceroute6
-rwxr-xr-x  1 root   root      13952 2010-03-11 18:12 traceroute6.iputils
-rwxr-xr-x  1 root   root     698020 2010-06-18 05:22 transmission
-rwxr-xr-x  1 root   root        677 2010-04-15 00:06 trial
-rwxr-xr-x  1 root   root     479820 2010-02-22 05:21 troff
-rwxr-xr-x  1 root   root      50848 2010-03-04 22:29 truncate
-rwxr-xr-x  1 root   root      92344 2010-02-08 22:37 tsclient
-rwxr-xr-x  1 root   root      18016 2010-03-06 22:33 tset
-rwxr-xr-x  1 root   root      38420 2010-03-04 22:29 tsort
-rwxr-xr-x  1 root   root      30216 2010-03-04 22:29 tty
-rwxr-xr-x  1 root   root        614 2010-04-15 00:06 twistd
-rwxr-xr-x  1 root   root       7261 2010-06-14 10:16 tzselect
-rwxr-xr-x  1 root   root      11387 2010-06-02 05:37 u1sdtool
lrwxrwxrwx  1 root   root         10 2010-04-29 21:28 ubuntu-bug -> apport-bug
-rwxr-xr-x  1 root   root       2549 2010-06-02 05:37 ubuntuone-launch
-rwxr-xr-x  1 root   root      41972 2010-06-02 05:37 ubuntuone-preferences
-rwxr-xr-x  1 root   root       6037 2010-06-01 06:05 ubuntu-support-status
-rwxr-xr-x  1 root   root      37925 2009-08-27 01:16 ucf
-rwxr-xr-x  1 root   root      19290 2008-05-30 02:22 ucfq
-rwxr-xr-x  1 root   root      10405 2008-05-30 02:22 ucfr
-rwxr-xr-x  1 root   root      17868 2010-01-11 10:28 ucs2any
-rwxr-xr-x  1 root   root      43312 2010-06-08 04:23 udisks
-rwxr-xr-x  1 root   root      13752 2009-11-10 11:12 ul
-rwxr-xr-x  1 root   root     174700 2010-04-14 22:24 umax_pp
-rwxr-xr-x  1 root   root      19931 2010-04-29 11:02 unattended-upgrade
lrwxrwxrwx  1 root   root         18 2010-05-17 20:05 unattended-upgrades -> unattended-upgrade
-rwxr-xr-x  1 root   root      34396 2010-03-04 22:29 unexpand
-rwxr-xr-x  1 root   root        530 2010-03-12 02:05 unicode_stop
-rwxr-xr-x  1 root   root      38452 2010-03-04 22:29 uniq
-rwxr-xr-x  1 root   root      30212 2010-03-04 22:29 unlink
lrwxrwxrwx  1 root   root          4 2010-04-29 15:13 unlzma -> lzma
-rwxr-xr-x  1 root   root         50 2010-06-03 02:01 unopkg
-rwxr-xr-x  1 root   root       5516 2010-03-22 13:51 unshare
-rwxr-xr-x  1 root   root     153336 2010-03-07 01:04 unzip
-rwxr-xr-x  1 root   root      67220 2010-03-07 01:04 unzipsfx
-rwxr-xr-x  1 root   root      37191 2010-06-28 12:27 update-alternatives
lrwxrwxrwx  1 root   root         26 2010-04-29 15:13 updatedb -> /etc/alternatives/updatedb
-rwxr-xr-x  1 root   root      34492 2010-03-24 06:16 updatedb.mlocate
-rwxr-xr-x  1 root   root      13932 2010-04-09 06:37 update-desktop-database
-rwxr-xr-x  1 root   root       5297 2010-03-30 08:43 update-gconf-defaults
-rwxr-xr-x  1 root   root       4380 2010-06-01 06:05 update-manager
-rwxr-xr-x  1 root   root     116968 2010-02-04 12:42 update-menus
-rwxr-xr-x  1 root   root        672 2010-04-16 21:57 update-mime-database
-rwxr-xr-x  1 root   root      42836 2010-04-16 21:57 update-mime-database.real
-rwxr-xr-x  1 root   root      60004 2010-04-13 16:52 update-notifier
-rwxr-xr-x  1 root   root       3331 2010-03-09 17:08 update-pciids
-rwxr-xr-x  1 root   root       6165 2010-01-18 02:56 update-perl-sax-parsers
-rwxr-xr-x  1 root   root      18028 2010-03-05 05:20 upower
-rwxr-xr-x  1 root   root       5488 2009-12-16 14:34 uptime
-rwxr-xr-x  1 root   root       3089 2010-04-13 11:53 usb-creator-gtk
-rwxr-xr-x  1 root   root       4202 2009-11-06 12:20 usb-devices
-rwxr-xr-x  1 root   root       5520 2010-03-25 04:12 usb_printerid
-rwxr-xr-x  1 root   root      30244 2010-03-04 22:29 users
-rwxr-xr-x  1 root   root     122176 2010-04-15 01:15 users-admin
-rwxr-xr-x  1 root   root       5524 2010-03-22 13:51 uuidgen
-rwxr-xr-x  1 root   root       3674 2010-03-31 05:47 uxterm
-rwxr-xr-x  1 root   root       2220 2009-11-13 13:45 uz
lrwxrwxrwx  1 root   root         20 2010-04-29 15:13 vi -> /etc/alternatives/vi
lrwxrwxrwx  1 root   root         22 2010-04-29 15:13 view -> /etc/alternatives/view
-rwxr-xr-x  1 root   root      18440 2010-03-22 16:23 viewres
-rwxr-xr-x  1 root   root     638492 2010-04-16 08:49 vim.tiny
-rwxr-xr-x  1 root   root     279360 2010-06-24 20:29 vinagre
-rwxr-xr-x  1 root   root       9688 2010-04-09 04:05 vino-passwd
-rwxr-xr-x  1 root   root      51460 2010-04-09 04:05 vino-preferences
-rwxr-xr-x  1 root   root       5492 2010-04-22 10:48 vmmouse_detect
-rwxr-xr-x  1 root   root      22024 2009-12-16 14:34 vmstat
-rwxr-xr-x  1 root   root       5520 2009-11-09 19:20 volname
lrwxrwxrwx  1 root   root         19 2010-04-29 15:13 w -> /etc/alternatives/w
-rwxr-xr-x  1 root   root    1192164 2009-11-10 13:02 w3m
-rwxr-xr-x  1 root   root       1132 2009-11-10 13:02 w3mman
-rwxr-sr-x  1 root   tty       13864 2010-03-22 13:51 wall
-rwxr-xr-x  1 root   root      14212 2009-12-16 14:34 watch
-rwxr-xr-x  1 root   root      42636 2010-03-04 22:29 wc
-rwxr-xr-x  1 root   root        326 2010-07-12 13:40 wftopfa
-rwxr-xr-x  1 root   root     333364 2010-01-06 09:02 wget
-rwxr-xr-x  1 root   root     102344 2010-03-02 05:31 whatis
-rwxr-xr-x  1 root   root       9912 2010-03-22 13:51 whereis
lrwxrwxrwx  1 root   root         10 2010-04-29 15:13 which -> /bin/which
-rwxr-xr-x  1 root   root      22100 2010-02-23 15:42 whiptail
-rwxr-xr-x  1 root   root      38548 2010-03-04 22:29 who
-rwxr-xr-x  1 root   root      30220 2010-03-04 22:29 whoami
-rwxr-xr-x  1 root   root      41912 2010-03-19 21:23 whois
lrwxrwxrwx  1 root   root         22 2010-04-29 15:13 wish -> /etc/alternatives/wish
-rwxr-xr-x  1 root   root       5500 2009-11-06 07:02 wish8.4
-rwxr-xr-x  1 root   root        210 2009-11-10 04:46 withsctp
-rwxr-xr-x  1 root   root     371208 2010-03-19 15:43 wodim
-rwxr-xr-x  1 root   root       5512 2010-03-24 12:08 word-list-compress
-rwxr-xr-x  1 root   root      22180 2010-03-07 01:24 wpa_passphrase
-rwxr-xr-x  1 root   root      13844 2009-12-16 14:34 w.procps
lrwxrwxrwx  1 root   root         23 2010-04-29 15:13 write -> /etc/alternatives/write##########################################################################
lrwxrwxrwx  1 root   root         29 2010-04-29 15:13 www-browser -> /etc/alternatives/www-browser
-rwsr-sr-x  1 root   root       9664 2010-04-08 19:53 X
lrwxrwxrwx  1 root   root          1 2010-04-29 15:13 X11 -> .
-rwxr-xr-x  1 root   root     113008 2010-03-12 13:30 x11perf
-rwxr-xr-x  1 root   root       2703 2010-03-12 13:30 x11perfcomp
-rwxr-xr-x  1 root   root      34392 2010-03-09 08:22 xargs
-rwxr-xr-x  1 root   root      30780 2009-12-07 09:06 xauth
-rwxr-xr-x  1 root   root      15228 2010-03-12 13:30 xbiff
-rwxr-xr-x  1 root   root      75672 2010-02-16 21:10 xbrlapi
-rwxr-xr-x  1 root   root      26768 2010-03-12 13:30 xcalc
-rwxr-xr-x  1 root   root      14020 2010-03-12 13:30 xclipboard
-rwxr-xr-x  1 root   root      36400 2010-03-12 13:30 xclock
-rwxr-xr-x  1 root   root      30560 2010-03-19 18:51 xcmsdb
-rwxr-xr-x  1 root   root      14560 2010-03-12 13:30 xconsole
-rwxr-xr-x  1 root   root      13816 2010-03-12 13:30 xcursorgen
-rwxr-xr-x  1 root   root       9864 2010-03-12 13:30 xcutsel
-rwxr-xr-x  1 root   root      14806 2010-03-12 02:54 xdg-desktop-icon
-rwxr-xr-x  1 root   root      39267 2010-03-12 02:54 xdg-desktop-menu
-rwxr-xr-x  1 root   root      17738 2010-03-12 02:54 xdg-email
-rwxr-xr-x  1 root   root      24129 2010-03-12 02:54 xdg-icon-resource
-rwxr-xr-x  1 root   root      28264 2010-03-12 02:54 xdg-mime
-rwxr-xr-x  1 root   root      10229 2010-03-12 02:54 xdg-open
-rwxr-xr-x  1 root   root      19319 2010-03-12 02:54 xdg-screensaver
-rwxr-xr-x  1 root   root        234 2010-04-16 18:03 xdg-user-dir
-rwxr-xr-x  1 root   root      18100 2010-01-25 12:21 xdg-user-dirs-gtk-update
-rwxr-xr-x  1 root   root      17944 2010-04-16 18:03 xdg-user-dirs-update
-rwxr-xr-x  1 root   root      59796 2010-03-12 13:30 xditview
-rwxr-xr-x  1 root   root      26628 2010-03-22 16:23 xdpyinfo
-rwxr-xr-x  1 root   root       5500 2010-03-22 16:23 xdriinfo
-rwxr-xr-x  1 root   root     526004 2010-03-12 13:30 xedit
-rwxr-xr-x  1 root   root      22104 2010-03-22 16:23 xev
-rwxr-xr-x  1 root   root      18992 2010-03-12 13:30 xeyes
-rwxr-xr-x  1 root   root      23112 2010-03-22 16:23 xfd
-rwxr-xr-x  1 root   root      31340 2010-03-22 16:23 xfontsel
-rwxr-xr-x  1 root   root       5516 2010-03-07 01:28 xfsinfo
-rwxr-xr-x  1 root   root       9624 2010-03-19 18:51 xgamma
-rwxr-xr-x  1 root   root      53284 2010-03-12 13:30 xgc
-rwxr-xr-x  1 root   root      13812 2010-03-19 18:51 xhost
-rwxr-xr-x  1 root   root      13876 2009-12-07 09:07 xinit
-rwxr-xr-x  1 root   root      38836 2010-04-15 10:01 xinput
-rwxr-xr-x  1 root   root       9640 2009-12-07 09:04 xkbbell
-rwxr-xr-x  1 root   root     181408 2009-12-07 09:04 xkbcomp
-rwxr-xr-x  1 root   root      30244 2009-12-07 09:04 xkbevd
-rwxr-xr-x  1 root   root      89800 2009-12-07 09:04 xkbprint
-rwxr-xr-x  1 root   root      18420 2009-12-07 09:04 xkbvleds
-rwxr-xr-x  1 root   root      14356 2009-12-07 09:04 xkbwatch
-rwxr-xr-x  1 root   root      14495 2010-03-19 18:51 xkeystone
-rwxr-xr-x  1 root   root       9744 2010-03-22 16:23 xkill
-rwxr-xr-x  1 root   root      14288 2010-03-12 13:30 xload
-rwxr-xr-x  1 root   root      14408 2010-03-12 13:30 xlogo
-rwxr-xr-x  1 root   root       9628 2010-03-22 16:23 xlsatoms
-rwxr-xr-x  1 root   root       9652 2010-03-22 16:23 xlsclients
-rwxr-xr-x  1 root   root      22064 2010-03-22 16:23 xlsfonts
-rwxr-xr-x  1 root   root      31672 2010-03-12 13:30 xmag
-rwxr-xr-x  1 root   root      53120 2010-03-12 13:30 xman
-rwxr-xr-x  1 root   root      14360 2010-03-22 16:23 xmessage
-rwxr-xr-x  1 root   root       7204 2010-04-19 02:26 xml2po
-rwxr-xr-x  1 root   root      13792 2009-12-15 23:50 xmlcatalog
-rwxr-xr-x  1 root   root      55760 2009-12-15 23:50 xmllint
-rwxr-xr-x  1 root   root      26376 2010-03-19 18:51 xmodmap
-rwxr-xr-x  1 root   root       9748 2010-03-12 13:30 xmore
-rwxr-xr-x  1 root   root    1749448 2010-06-16 05:37 Xorg
-rwxr-xr-x  1 root   root       4961 2010-01-18 02:58 xpath
lrwxrwxrwx  1 root   root         33 2010-06-29 22:05 xpcshell-1.9.2 -> ../lib/xulrunner-1.9.2.6/xpcshell
-rwxr-xr-x  1 root   root      31504 2010-03-22 16:23 xprop
-rwxr-xr-x  1 root   root      53492 2010-03-25 04:12 xqxdecode
-rwxr-xr-x  1 root   root      46708 2010-03-19 18:51 xrandr
-rwxr-xr-x  1 root   root      22100 2010-03-19 18:51 xrdb
-rwxr-xr-x  1 root   root       9820 2010-03-19 18:51 xrefresh
-rwxr-xr-x  1 root   root     113440 2010-04-15 07:47 xscreensaver-getimage
-rwxr-xr-x  1 root   root      16299 2010-04-15 07:47 xscreensaver-getimage-file
-rwxr-xr-x  1 root   root       5044 2010-04-15 07:47 xscreensaver-getimage-video
-rwxr-xr-x  1 root   root      17892 2010-04-15 07:47 xscreensaver-gl-helper
-rwxr-xr-x  1 root   root      26805 2010-04-15 07:47 xscreensaver-text
lrwxrwxrwx  1 root   root         35 2010-04-29 15:13 x-session-manager -> /etc/alternatives/x-session-manager
-rwxr-xr-x  1 root   root      30296 2010-03-19 18:51 xset
-rwxr-xr-x  1 root   root       5524 2010-03-19 18:51 xsetmode
-rwxr-xr-x  1 root   root       9624 2010-03-19 18:51 xsetpointer
-rwxr-xr-x  1 root   root      13804 2010-03-19 18:51 xsetroot
-rwxr-xr-x  1 root   root      34348 2010-04-22 16:55 xsetwacom
-rwxr-xr-x  1 root   root      22056 2010-01-19 07:32 xsltproc
-rwxr-xr-x  1 root   root      75892 2009-12-07 09:01 xsm
-rwxr-xr-x  1 root   root      10052 2010-03-19 18:51 xstdcmap
-rwxr-xr-x  1 root   root       4093 2010-04-23 04:22 xsubpp
-rwxr-sr-x  1 root   utmp     354444 2010-03-31 05:47 xterm
lrwxrwxrwx  1 root   root         37 2010-04-29 15:13 x-terminal-emulator -> /etc/alternatives/x-terminal-emulator
lrwxrwxrwx  1 root   root         27 2010-06-29 22:05 xulrunner -> /etc/alternatives/xulrunner
lrwxrwxrwx  1 root   root         34 2010-06-29 22:05 xulrunner-1.9.2 -> ../lib/xulrunner-1.9.2.6/xulrunner
-rwxr-xr-x  1 root   root      31292 2010-03-19 18:51 xvidtune
-rwxr-xr-x  1 root   root       9632 2010-03-22 16:23 xvinfo
-rwxr-xr-x  1 root   root      22048 2010-03-12 13:30 xwd
lrwxrwxrwx  1 root   root         34 2010-04-29 15:13 x-window-manager -> /etc/alternatives/x-window-manager
-rwxr-xr-x  1 root   root      26144 2010-03-22 16:23 xwininfo
-rwxr-xr-x  1 root   root      26120 2010-03-12 13:30 xwud
lrwxrwxrwx  1 root   root         31 2010-04-29 15:13 x-www-browser -> /etc/alternatives/x-www-browser
-rwxr-xr-x  1 root   root      13876 2010-04-16 08:50 xxd
-rwxr-xr-x  1 root   root     270720 2010-04-16 20:15 yelp
-rwxr-xr-x  1 root   root      30208 2010-03-04 22:29 yes
-rwxr-xr-x  1 root   root      13764 2010-06-14 10:35 zdump
-rwxr-xr-x  1 root   root      66444 2010-03-29 07:02 zenity
-rwxr-xr-x  1 root   root     181104 2010-02-15 12:40 zip
-rwxr-xr-x  1 root   root      80352 2010-02-15 12:40 zipcloak
-rwxr-xr-x  1 root   root       2953 2010-03-07 01:04 zipgrep
-rwxr-xr-x  1 root   root     153336 2010-03-07 01:04 zipinfo
-rwxr-xr-x  1 root   root      76060 2010-02-15 12:40 zipnote
-rwxr-xr-x  1 root   root      80156 2010-02-15 12:40 zipsplit
-rwxr-xr-x  1 root   root      57588 2010-03-25 04:12 zjsdecode
-rwxr-xr-x  1 root   root      88168 2010-03-02 05:31 zsoelim

---

### Post by sisco311 on 2010-07-16
Anything else looks fine. Does apt-get work now?
```
sudo apt-get update
```

P.S. Next time please include the output of commands between ```
 tags:
[noparse][code]...output here...
```[/noparse]

---

### Post by phobophilia on 2010-07-16
It does! Thanks, you're my hero. I'll make a note of the code brackets, too- I don't have enough major problems to warrant asking the forums much, but I'll keep that in the forefront next time I'm around.

---

