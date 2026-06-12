---
title: "Can't access rkhunter.log"
date: 2009-08-02
forum: New to Ubuntu
---

### Post by rumo59 on 2009-08-02
Have just ran rkhunter, all fine except this bit:

  Performing filesystem checks
    Checking /dev for suspicious file types                  [ Warning ]
    Checking for hidden files and directories                [ None found ]

[Press <ENTER> to continue]


Checking application versions...

    Checking version of Exim MTA                             [ OK ]
    Checking version of GnuPG                                [ OK ]
    Checking version of OpenSSL                              [ OK ]


System checks summary
=====================

File properties checks...
    Files checked: 127
    Suspect files: 0

Rootkit checks...
    Rootkits checked : 109
    Possible rootkits: 0

Applications checks...
    Applications checked: 3
    Suspect applications: 0

The system checks took: 45 seconds

All results have been written to the logfile (/var/log/rkhunter.log)

One or more warnings have been found while checking the system.
_**Please check the log file (/var/log/rkhunter.log)**_

Access to this file is denied, am I doing something wrong?
PS I'm very green with the system.:(

---

### Post by gorgon on 2009-08-02
hi,

what is the exact message that you're getting?

can you access the file as superuser/root? i.e :
```
gksudu gedit /var/log/rkhunter.log
```

---

### Post by rumo59 on 2009-08-02
Hi gorgon

Tried that but got "command not found"

---

### Post by rumo59 on 2009-08-02
Have just got into rkhunter.log (Commands are getting easier)
Can someone please tell me if this looks ok:

[15:01:11] Running Rootkit Hunter version 1.3.2 on les59-laptop
[15:01:11]
[15:01:11] Info: Start date is Sun Aug  2 15:01:11 BST 2009
[15:01:11]
[15:01:11] Checking configuration file and command-line options...
[15:01:11] Info: Detected operating system is 'Linux'
[15:01:11] Info: Found O/S name: Ubuntu 9.04
[15:01:11] Info: Command line is /usr/bin/rkhunter --checkall
[15:01:11] Info: Environment shell is /bin/bash; rkhunter is using dash
[15:01:11] Info: Using configuration file '/etc/rkhunter.conf'
[15:01:11] Info: Installation directory is '/usr'
[15:01:11] Info: Using language 'en'
[15:01:11] Info: Using '/var/lib/rkhunter/db' as the database directory
[15:01:11] Info: Using '/usr/share/rkhunter/scripts' as the support script directory
[15:01:11] Info: Using '/usr/local/sbin /usr/local/bin /usr/sbin /usr/bin /sbin /bin /usr/X11R6/bin /bin /usr/bin /sbin /usr/sbin /usr/local/bin /usr/local/sbin /usr/libexec /usr/local/libexec' as the command directories
[15:01:11] Info: Using '/' as the root directory
[15:01:11] Info: Using '/var/lib/rkhunter/tmp' as the temporary directory
[15:01:11] Info: No mail-on-warning address configured
[15:01:11] Info: X will be automatically detected
[15:01:12] Info: Using second color set
[15:01:12] Info: Found the 'diff' command: /usr/bin/diff
[15:01:12] Info: Found the 'file' command: /usr/bin/file
[15:01:12] Info: Found the 'find' command: /usr/bin/find
[15:01:12] Info: Found the 'ifconfig' command: /sbin/ifconfig
[15:01:12] Info: Found the 'ip' command: /sbin/ip
[15:01:12] Info: Found the 'ldd' command: /usr/bin/ldd
[15:01:12] Info: Found the 'lsattr' command: /usr/bin/lsattr
[15:01:12] Info: Found the 'lsmod' command: /sbin/lsmod
[15:01:12] Info: Found the 'lsof' command: /usr/bin/lsof
[15:01:12] Info: Found the 'mktemp' command: /bin/mktemp
[15:01:12] Info: Found the 'netstat' command: /bin/netstat
[15:01:12] Info: Found the 'perl' command: /usr/bin/perl
[15:01:12] Info: Found the 'ps' command: /bin/ps
[15:01:12] Info: Found the 'pwd' command: /bin/pwd
[15:01:12] Info: Found the 'readlink' command: /bin/readlink
[15:01:12] Info: Found the 'sort' command: /usr/bin/sort
[15:01:12] Info: Found the 'stat' command: /usr/bin/stat
[15:01:12] Info: Found the 'strings' command: /usr/bin/strings
[15:01:12] Info: Found the 'uniq' command: /usr/bin/uniq
[15:01:12] Info: System is not using prelinking
[15:01:12] Info: Using the '/usr/bin/sha1sum' command for the file hash checks
[15:01:12] Info: Stored hash values used hash function '/usr/bin/sha1sum'
[15:01:12] Info: Stored hash values did not use a package manager
[15:01:12] Info: The hash function field index is set to 1
[15:01:12] Info: No package manager specified: using hash function '/usr/bin/sha1sum'
[15:01:12] Info: Previous file attributes were stored
[15:01:12] Info: Enabled tests are: all
[15:01:12] Info: Disabled tests are: suspscan hidden_procs deleted_files packet_cap_apps
[15:01:12] Info: Found ksym file '/proc/kallsyms'
[15:01:12]
[15:01:12] Checking if the O/S has changed since last time...
[15:01:12] Info: Nothing seems to have changed
[15:01:12]
[15:01:12] Starting system checks...
[15:01:12]
[15:01:12] Checking system commands...
[15:01:12] Info: Starting test name 'system_commands'
[15:01:12]
[15:01:12] Performing 'strings' command checks
[15:01:12] Info: Starting test name 'strings'
[15:01:12] Scanning for string /usr/sbin/ntpsx               [ OK ]
[15:01:12] Scanning for string /usr/lib/.../ls               [ OK ]
[15:01:12] Scanning for string /usr/lib/.../netstat          [ OK ]
[15:01:12] Scanning for string /usr/lib/.../lsof             [ OK ]
[15:01:12] Scanning for string /usr/lib/.../bkit-ssh/bkit-shdcfg [ OK ]
[15:01:12] Scanning for string /usr/lib/.../bkit-ssh/bkit-shhk [ OK ]
[15:01:12] Scanning for string /usr/lib/.../bkit-ssh/bkit-pw [ OK ]
[15:01:12] Scanning for string /usr/lib/.../bkit-ssh/bkit-shrs [ OK ]
[15:01:12] Scanning for string /usr/lib/.../uconf.inv        [ OK ]
[15:01:12] Scanning for string /usr/lib/.../psr              [ OK ]
[15:01:12] Scanning for string /usr/lib/.../find             [ OK ]
[15:01:12] Scanning for string /usr/lib/.../pstree           [ OK ]
[15:01:12] Scanning for string /usr/lib/.../slocate          [ OK ]
[15:01:12] Scanning for string /usr/lib/.../du               [ OK ]
[15:01:12] Scanning for string /usr/lib/.../top              [ OK ]
[15:01:12] Scanning for string /usr/lib/...                  [ OK ]
[15:01:12] Scanning for string /usr/lib/.../bkit-ssh         [ OK ]
[15:01:12] Scanning for string /usr/lib/.bkit-               [ OK ]
[15:01:12] Scanning for string /tmp/.bkp                     [ OK ]
[15:01:13] Scanning for string /tmp/.cinik                   [ OK ]
[15:01:13] Scanning for string /tmp/.font-unix/.cinik        [ OK ]
[15:01:13] Scanning for string /lib/.sso                     [ OK ]
[15:01:13] Scanning for string /lib/.so                      [ OK ]
[15:01:13] Scanning for string /var/run/...dica/clean        [ OK ]
[15:01:13] Scanning for string /var/run/...dica/xl           [ OK ]
[15:01:13] Scanning for string /var/run/...dica/xdr          [ OK ]
[15:01:13] Scanning for string /var/run/...dica/psg          [ OK ]
[15:01:13] Scanning for string /var/run/...dica/secure       [ OK ]
[15:01:13] Scanning for string /var/run/...dica/rdx          [ OK ]
[15:01:13] Scanning for string /var/run/...dica/va           [ OK ]
[15:01:13] Scanning for string /var/run/...dica/cl.sh        [ OK ]
[15:01:13] Scanning for string /usr/bin/.etc                 [ OK ]
[15:01:13] Scanning for string /usr/lib/.fx/sched_host.2     [ OK ]
[15:01:13] Scanning for string /usr/lib/.fx/random_d.2       [ OK ]
[15:01:13] Scanning for string /usr/lib/.fx/set_pid.2        [ OK ]
[15:01:13] Scanning for string /usr/lib/.fx/cons.saver       [ OK ]
[15:01:13] Scanning for string /usr/lib/.fx/adore/adore/adore.ko [ OK ]
[15:01:13] Scanning for string /bin/sysback                  [ OK ]
[15:01:13] Scanning for string /usr/local/bin/sysback        [ OK ]
[15:01:13] Scanning for string /usr/lib/.tbd                 [ OK ]
[15:01:13] Scanning for string /dev/.lib/lib/lib/t0rns       [ OK ]
[15:01:13] Scanning for string /dev/.lib/lib/lib/du          [ OK ]
[15:01:13] Scanning for string /dev/.lib/lib/lib/ls          [ OK ]
[15:01:13] Scanning for string /dev/.lib/lib/lib/t0rnsb      [ OK ]
[15:01:13] Scanning for string /dev/.lib/lib/lib/ps          [ OK ]
[15:01:13] Scanning for string /dev/.lib/lib/lib/t0rnp       [ OK ]
[15:01:13] Scanning for string /dev/.lib/lib/lib/find        [ OK ]
[15:01:13] Scanning for string /dev/.lib/lib/lib/ifconfig    [ OK ]
[15:01:13] Scanning for string /dev/.lib/lib/lib/pg          [ OK ]
[15:01:13] Scanning for string /dev/.lib/lib/lib/ssh.tgz     [ OK ]
[15:01:13] Scanning for string /dev/.lib/lib/lib/top         [ OK ]
[15:01:13] Scanning for string /dev/.lib/lib/lib/sz          [ OK ]
[15:01:13] Scanning for string /dev/.lib/lib/lib/login       [ OK ]
[15:01:13] Scanning for string /dev/.lib/lib/lib/in.fingerd  [ OK ]
[15:01:13] Scanning for string /dev/.lib/lib/lib/1i0n.sh     [ OK ]
[15:01:13] Scanning for string /dev/.lib/lib/lib/pstree      [ OK ]
[15:01:13] Scanning for string /dev/.lib/lib/lib/in.telnetd  [ OK ]
[15:01:13] Scanning for string /dev/.lib/lib/lib/mjy         [ OK ]
[15:01:13] Scanning for string /dev/.lib/lib/lib/sush        [ OK ]
[15:01:13] Scanning for string /dev/.lib/lib/lib/tfn         [ OK ]
[15:01:13] Scanning for string /dev/.lib/lib/lib/name        [ OK ]
[15:01:14] Scanning for string /dev/.lib/lib/lib/getip.sh    [ OK ]
[15:01:14] Scanning for string /usr/info/.torn/sh*           [ OK ]
[15:01:14] Scanning for string /usr/src/.****/.1addr         [ OK ]
[15:01:14] Scanning for string /usr/src/.****/.1file         [ OK ]
[15:01:14] Scanning for string /usr/src/.****/.1proc         [ OK ]
[15:01:14] Scanning for string /usr/src/.****/.1logz         [ OK ]
[15:01:14] Scanning for string /usr/info/.t0rn               [ OK ]
[15:01:14] Scanning for string /dev/.lib                     [ OK ]
[15:01:14] Scanning for string /dev/.lib/lib                 [ OK ]
[15:01:14] Scanning for string /dev/.lib/lib/lib             [ OK ]
[15:01:14] Scanning for string /dev/.lib/lib/lib/dev         [ OK ]
[15:01:14] Scanning for string /dev/.lib/lib/scan            [ OK ]
[15:01:14] Scanning for string /usr/src/.****                [ OK ]
[15:01:14] Scanning for string /usr/man/man1/man1            [ OK ]
[15:01:14] Scanning for string /usr/man/man1/man1/lib        [ OK ]
[15:01:14] Scanning for string /usr/man/man1/man1/lib/.lib   [ OK ]
[15:01:14] Scanning for string /usr/man/man1/man1/lib/.lib/.backup [ OK ]
[15:01:14]
[15:01:14] Performing 'shared libraries' checks
[15:01:14] Info: Starting test name 'shared_libs'
[15:01:14] Checking for preloading variables                 [ None found ]
[15:01:14] Checking for preload file                         [ Not found ]
[15:01:14] Info: Starting test name 'shared_libs_path'
[15:01:14] Checking LD_LIBRARY_PATH variable                 [ Not found ]
[15:01:14]
[15:01:14] Performing file properties checks
[15:01:14] Info: Starting test name 'properties'
[15:01:14] Checking for prerequisites                        [ OK ]
[15:01:14] /bin/bash                                         [ OK ]
[15:01:14] /bin/cat                                          [ OK ]
[15:01:14] /bin/chmod                                        [ OK ]
[15:01:15] /bin/chown                                        [ OK ]
[15:01:15] /bin/cp                                           [ OK ]
[15:01:15] /bin/date                                         [ OK ]
[15:01:15] /bin/df                                           [ OK ]
[15:01:15] /bin/dmesg                                        [ OK ]
[15:01:15] /bin/echo                                         [ OK ]
[15:01:15] /bin/ed                                           [ OK ]
[15:01:15] /bin/egrep                                        [ OK ]
[15:01:15] Info: Found file '/bin/egrep': it is whitelisted for the 'script replacement' check.
[15:01:15] /bin/fgrep                                        [ OK ]
[15:01:15] Info: Found file '/bin/fgrep': it is whitelisted for the 'script replacement' check.
[15:01:15] /bin/fuser                                        [ OK ]
[15:01:15] /bin/grep                                         [ OK ]
[15:01:15] /bin/ip                                           [ OK ]
[15:01:16] /bin/kill                                         [ OK ]
[15:01:16] /bin/login                                        [ OK ]
[15:01:16] /bin/ls                                           [ OK ]
[15:01:16] /bin/lsmod                                        [ OK ]
[15:01:16] /bin/mktemp                                       [ OK ]
[15:01:16] /bin/more                                         [ OK ]
[15:01:16] /bin/mount                                        [ OK ]
[15:01:16] /bin/mv                                           [ OK ]
[15:01:16] /bin/netstat                                      [ OK ]
[15:01:16] /bin/ps                                           [ OK ]
[15:01:16] /bin/pwd                                          [ OK ]
[15:01:17] /bin/readlink                                     [ OK ]
[15:01:17] /bin/sed                                          [ OK ]
[15:01:17] /bin/sh                                           [ OK ]
[15:01:17] /bin/su                                           [ OK ]
[15:01:17] /bin/touch                                        [ OK ]
[15:01:17] /bin/uname                                        [ OK ]
[15:01:17] /bin/which                                        [ OK ]
[15:01:17] Info: Found file '/bin/which': it is whitelisted for the 'script replacement' check.
[15:01:17] /bin/dash                                         [ OK ]
[15:01:17] /usr/bin/awk                                      [ OK ]
[15:01:17] /usr/bin/basename                                 [ OK ]
[15:01:17] /usr/bin/chattr                                   [ OK ]
[15:01:18] /usr/bin/cut                                      [ OK ]
[15:01:18] /usr/bin/diff                                     [ OK ]
[15:01:18] /usr/bin/dirname                                  [ OK ]
[15:01:18] /usr/bin/dpkg                                     [ OK ]
[15:01:18] /usr/bin/dpkg-query                               [ OK ]
[15:01:18] /usr/bin/du                                       [ OK ]
[15:01:18] /usr/bin/env                                      [ OK ]
[15:01:18] /usr/bin/file                                     [ OK ]
[15:01:18] /usr/bin/find                                     [ OK ]
[15:01:18] /usr/bin/GET                                      [ OK ]
[15:01:18] /usr/bin/groups                                   [ OK ]
[15:01:18] Info: Found file '/usr/bin/groups': it is whitelisted for the 'script replacement' check.
[15:01:19] /usr/bin/head                                     [ OK ]
[15:01:19] /usr/bin/id                                       [ OK ]
[15:01:19] /usr/bin/killall                                  [ OK ]
[15:01:19] /usr/bin/last                                     [ OK ]
[15:01:19] /usr/bin/lastlog                                  [ OK ]
[15:01:19] /usr/bin/ldd                                      [ OK ]
[15:01:19] Info: Found file '/usr/bin/ldd': it is whitelisted for the 'script replacement' check.
[15:01:19] /usr/bin/less                                     [ OK ]
[15:01:19] /usr/bin/locate                                   [ OK ]
[15:01:19] /usr/bin/logger                                   [ OK ]
[15:01:19] /usr/bin/lsattr                                   [ OK ]
[15:01:19] /usr/bin/lsof                                     [ OK ]
[15:01:19] /usr/bin/mail                                     [ OK ]
[15:01:20] /usr/bin/md5sum                                   [ OK ]
[15:01:20] /usr/bin/mlocate                                  [ OK ]
[15:01:20] /usr/bin/newgrp                                   [ OK ]
[15:01:20] /usr/bin/passwd                                   [ OK ]
[15:01:20] /usr/bin/perl                                     [ OK ]
[15:01:20] /usr/bin/pstree                                   [ OK ]
[15:01:20] /usr/bin/rkhunter                                 [ OK ]
[15:01:20] /usr/bin/runcon                                   [ OK ]
[15:01:20] /usr/bin/sha1sum                                  [ OK ]
[15:01:20] /usr/bin/size                                     [ OK ]
[15:01:20] /usr/bin/sort                                     [ OK ]
[15:01:21] /usr/bin/stat                                     [ OK ]
[15:01:21] /usr/bin/strace                                   [ OK ]
[15:01:21] /usr/bin/strings                                  [ OK ]
[15:01:21] /usr/bin/sudo                                     [ OK ]
[15:01:21] /usr/bin/tail                                     [ OK ]
[15:01:21] /usr/bin/test                                     [ OK ]
[15:01:21] /usr/bin/top                                      [ OK ]
[15:01:21] /usr/bin/touch                                    [ OK ]
[15:01:21] /usr/bin/tr                                       [ OK ]
[15:01:21] /usr/bin/uniq                                     [ OK ]
[15:01:21] /usr/bin/users                                    [ OK ]
[15:01:21] /usr/bin/vmstat                                   [ OK ]
[15:01:22] /usr/bin/w                                        [ OK ]
[15:01:22] /usr/bin/watch                                    [ OK ]
[15:01:22] /usr/bin/wc                                       [ OK ]
[15:01:22] /usr/bin/wget                                     [ OK ]
[15:01:22] /usr/bin/whatis                                   [ OK ]
[15:01:22] /usr/bin/whereis                                  [ OK ]
[15:01:22] /usr/bin/which                                    [ OK ]
[15:01:22] /usr/bin/who                                      [ OK ]
[15:01:22] /usr/bin/whoami                                   [ OK ]
[15:01:22] /usr/bin/mawk                                     [ OK ]
[15:01:22] /usr/bin/lwp-request                              [ OK ]
[15:01:22] Info: Found file '/usr/bin/lwp-request': it is whitelisted for the 'script replacement' check.
[15:01:22] /usr/bin/bsd-mailx                                [ OK ]
[15:01:23] /usr/bin/w.procps                                 [ OK ]
[15:01:23] /sbin/depmod                                      [ OK ]
[15:01:23] /sbin/ifconfig                                    [ OK ]
[15:01:23] /sbin/ifdown                                      [ OK ]
[15:01:23] /sbin/ifup                                        [ OK ]
[15:01:23] /sbin/init                                        [ OK ]
[15:01:23] /sbin/insmod                                      [ OK ]
[15:01:23] /sbin/ip                                          [ OK ]
[15:01:23] /sbin/lsmod                                       [ OK ]
[15:01:23] /sbin/modinfo                                     [ OK ]
[15:01:24] /sbin/modprobe                                    [ OK ]
[15:01:24] /sbin/rmmod                                       [ OK ]
[15:01:24] /sbin/runlevel                                    [ OK ]
[15:01:24] /sbin/sulogin                                     [ OK ]
[15:01:24] /sbin/sysctl                                      [ OK ]
[15:01:24] /sbin/syslogd                                     [ OK ]
[15:01:24] /usr/sbin/adduser                                 [ OK ]
[15:01:24] Info: Found file '/usr/sbin/adduser': it is whitelisted for the 'script replacement' check.
[15:01:24] /usr/sbin/chroot                                  [ OK ]
[15:01:24] /usr/sbin/cron                                    [ OK ]
[15:01:25] /usr/sbin/groupadd                                [ OK ]
[15:01:25] /usr/sbin/groupdel                                [ OK ]
[15:01:25] /usr/sbin/groupmod                                [ OK ]
[15:01:25] /usr/sbin/grpck                                   [ OK ]
[15:01:25] /usr/sbin/nologin                                 [ OK ]
[15:01:25] /usr/sbin/pwck                                    [ OK ]
[15:01:25] /usr/sbin/tcpd                                    [ OK ]
[15:01:25] /usr/sbin/unhide                                  [ OK ]
[15:01:25] /usr/sbin/useradd                                 [ OK ]
[15:01:26] /usr/sbin/userdel                                 [ OK ]
[15:01:26] /usr/sbin/usermod                                 [ OK ]
[15:01:26] /usr/sbin/vipw                                    [ OK ]
[15:01:26] /usr/sbin/unhide-linux26                          [ OK ]
[15:01:30]
[15:01:30] Checking for rootkits...
[15:01:30] Info: Starting test name 'rootkits'
[15:01:30]
[15:01:30] Performing check of known rootkit files and directories
[15:01:30] Info: Starting test name 'known_rkts'
[15:01:30]
[15:01:30] Checking for 55808 Trojan - Variant A...
[15:01:30]   Checking for file '/tmp/.../r'                  [ Not found ]
[15:01:30]   Checking for file '/tmp/.../a'                  [ Not found ]
[15:01:30] 55808 Trojan - Variant A                          [ Not found ]
[15:01:30]
[15:01:30] Checking for ADM Worm...
[15:01:30]   Checking for string 'w0rm'                      [ Not found ]
[15:01:30] ADM Worm                                          [ Not found ]
[15:01:30]
[15:01:30] Checking for AjaKit Rootkit...
[15:01:30]   Checking for file '/dev/tux/.addr'              [ Not found ]
[15:01:30]   Checking for file '/dev/tux/.proc'              [ Not found ]
[15:01:30]   Checking for file '/dev/tux/.file'              [ Not found ]
[15:01:30]   Checking for file '/lib/.libgh-gh/cleaner'      [ Not found ]
[15:01:30]   Checking for file '/lib/.libgh-gh/Patch/patch'  [ Not found ]
[15:01:30]   Checking for file '/lib/.libgh-gh/sb0k'         [ Not found ]
[15:01:30]   Checking for directory '/dev/tux'               [ Not found ]
[15:01:30]   Checking for directory '/lib/.libgh-gh'         [ Not found ]
[15:01:30] AjaKit Rootkit                                    [ Not found ]
[15:01:30]
[15:01:30] Checking for aPa Kit...
[15:01:30]   Checking for file '/usr/share/.aPa'             [ Not found ]
[15:01:30] aPa Kit                                           [ Not found ]
[15:01:30]
[15:01:30] Checking for Apache Worm...
[15:01:30]   Checking for file '/bin/.log'                   [ Not found ]
[15:01:30] Apache Worm                                       [ Not found ]
[15:01:30]
[15:01:30] Checking for Ambient (ark) Rootkit...
[15:01:30]   Checking for file '/usr/lib/.ark?'              [ Not found ]
[15:01:30]   Checking for file '/dev/ptyxx/.log'             [ Not found ]
[15:01:30]   Checking for file '/dev/ptyxx/.file'            [ Not found ]
[15:01:30]   Checking for directory '/dev/ptyxx'             [ Not found ]
[15:01:30] Ambient (ark) Rootkit                             [ Not found ]
[15:01:30]
[15:01:30] Checking for Balaur Rootkit...
[15:01:30]   Checking for file '/usr/lib/liblog.o'           [ Not found ]
[15:01:30]   Checking for directory '/usr/lib/.kinetic'      [ Not found ]
[15:01:30]   Checking for directory '/usr/lib/.egcs'         [ Not found ]
[15:01:30]   Checking for directory '/usr/lib/.wormie'       [ Not found ]
[15:01:30] Balaur Rootkit                                    [ Not found ]
[15:01:30]
[15:01:30] Checking for BeastKit Rootkit...
[15:01:30]   Checking for file '/usr/sbin/arobia'            [ Not found ]
[15:01:30]   Checking for file '/usr/sbin/idrun'             [ Not found ]
[15:01:30]   Checking for file '/usr/lib/elm/arobia/elm'     [ Not found ]
[15:01:31]   Checking for file '/usr/lib/elm/arobia/elm/hk'  [ Not found ]
[15:01:31]   Checking for file '/usr/lib/elm/arobia/elm/hk.pub' [ Not found ]
[15:01:31]   Checking for file '/usr/lib/elm/arobia/elm/sc'  [ Not found ]
[15:01:31]   Checking for file '/usr/lib/elm/arobia/elm/sd.pp' [ Not found ]
[15:01:31]   Checking for file '/usr/lib/elm/arobia/elm/sdco' [ Not found ]
[15:01:31]   Checking for file '/usr/lib/elm/arobia/elm/srsd' [ Not found ]
[15:01:31]   Checking for directory '/lib/ldd.so/bktools'    [ Not found ]
[15:01:31] BeastKit Rootkit                                  [ Not found ]
[15:01:31]
[15:01:31] Checking for beX2 Rootkit...
[15:01:31]   Checking for directory '/usr/include/bex'       [ Not found ]
[15:01:31] beX2 Rootkit                                      [ Not found ]
[15:01:31]
[15:01:31] Checking for BOBKit Rootkit...
[15:01:31]   Checking for file '/usr/sbin/ntpsx'             [ Not found ]
[15:01:31]   Checking for file '/usr/lib/.../ls'             [ Not found ]
[15:01:31]   Checking for file '/usr/lib/.../netstat'        [ Not found ]
[15:01:31]   Checking for file '/usr/lib/.../lsof'           [ Not found ]
[15:01:31]   Checking for file '/usr/lib/.../bkit-ssh/bkit-shdcfg' [ Not found ]
[15:01:31]   Checking for file '/usr/lib/.../bkit-ssh/bkit-shhk' [ Not found ]
[15:01:31]   Checking for file '/usr/lib/.../bkit-ssh/bkit-pw' [ Not found ]
[15:01:31]   Checking for file '/usr/lib/.../bkit-ssh/bkit-shrs' [ Not found ]
[15:01:31]   Checking for file '/usr/lib/.../uconf.inv'      [ Not found ]
[15:01:31]   Checking for file '/usr/lib/.../psr'            [ Not found ]
[15:01:31]   Checking for file '/usr/lib/.../find'           [ Not found ]
[15:01:31]   Checking for file '/usr/lib/.../pstree'         [ Not found ]
[15:01:31]   Checking for file '/usr/lib/.../slocate'        [ Not found ]
[15:01:31]   Checking for file '/usr/lib/.../du'             [ Not found ]
[15:01:31]   Checking for file '/usr/lib/.../top'            [ Not found ]
[15:01:31]   Checking for directory '/usr/lib/...'           [ Not found ]
[15:01:31]   Checking for directory '/usr/lib/.../bkit-ssh'  [ Not found ]
[15:01:31]   Checking for directory '/usr/lib/.bkit-'        [ Not found ]
[15:01:31]   Checking for directory '/tmp/.bkp'              [ Not found ]
[15:01:31] BOBKit Rootkit                                    [ Not found ]
[15:01:31]
[15:01:31] Checking for CiNIK Worm (Slapper.B variant)...
[15:01:31]   Checking for file '/tmp/.cinik'                 [ Not found ]
[15:01:31]   Checking for directory '/tmp/.font-unix/.cinik' [ Not found ]
[15:01:31] CiNIK Worm (Slapper.B variant)                    [ Not found ]
[15:01:31]
[15:01:31] Checking for Danny-Boy's Abuse Kit...
[15:01:31]   Checking for file '/dev/mdev'                   [ Not found ]
[15:01:31]   Checking for file '/usr/lib/libX.a'             [ Not found ]
[15:01:31] Danny-Boy's Abuse Kit                             [ Not found ]
[15:01:31]
[15:01:31] Checking for Devil RootKit...
[15:01:31]   Checking for file '/var/lib/games/.src'         [ Not found ]
[15:01:31]   Checking for file '/dev/dsx'                    [ Not found ]
[15:01:31]   Checking for file '/dev/caca'                   [ Not found ]
[15:01:32] Devil RootKit                                     [ Not found ]
[15:01:32]
[15:01:32] Checking for Dica-Kit Rootkit...
[15:01:32]   Checking for file '/lib/.sso'                   [ Not found ]
[15:01:32]   Checking for file '/lib/.so'                    [ Not found ]
[15:01:32]   Checking for file '/var/run/...dica/clean'      [ Not found ]
[15:01:32]   Checking for file '/var/run/...dica/xl'         [ Not found ]
[15:01:32]   Checking for file '/var/run/...dica/xdr'        [ Not found ]
[15:01:32]   Checking for file '/var/run/...dica/psg'        [ Not found ]
[15:01:32]   Checking for file '/var/run/...dica/secure'     [ Not found ]
[15:01:32]   Checking for file '/var/run/...dica/rdx'        [ Not found ]
[15:01:32]   Checking for file '/var/run/...dica/va'         [ Not found ]
[15:01:32]   Checking for file '/var/run/...dica/cl.sh'      [ Not found ]
[15:01:32]   Checking for file '/usr/bin/.etc'               [ Not found ]
[15:01:32]   Checking for directory '/var/run/...dica'       [ Not found ]
[15:01:32]   Checking for directory '/var/run/...dica/mh'    [ Not found ]
[15:01:32]   Checking for directory '/var/run/...dica/scan'  [ Not found ]
[15:01:32] Dica-Kit Rootkit                                  [ Not found ]
[15:01:32]
[15:01:32] Checking for Dreams Rootkit...
[15:01:32]   Checking for file '/dev/ttyoa'                  [ Not found ]
[15:01:32]   Checking for file '/dev/ttyof'                  [ Not found ]
[15:01:32]   Checking for file '/dev/ttyop'                  [ Not found ]
[15:01:32]   Checking for file '/usr/bin/sense'              [ Not found ]
[15:01:32]   Checking for file '/usr/bin/sl2'                [ Not found ]
[15:01:32]   Checking for file '/usr/bin/logclear'           [ Not found ]
[15:01:32]   Checking for file '/usr/bin/(swapd)'            [ Not found ]
[15:01:32]   Checking for file '/usr/bin/snfs'               [ Not found ]
[15:01:32]   Checking for file '/usr/lib/libsss'             [ Not found ]
[15:01:32]   Checking for directory '/dev/ida/.hpd'          [ Not found ]
[15:01:32] Dreams Rootkit                                    [ Not found ]
[15:01:32]
[15:01:32] Checking for Duarawkz Rootkit...
[15:01:32]   Checking for file '/usr/bin/duarawkz/loginpass' [ Not found ]
[15:01:32]   Checking for directory '/usr/bin/duarawkz'      [ Not found ]
[15:01:32] Duarawkz Rootkit                                  [ Not found ]
[15:01:32]
[15:01:32] Checking for Enye LKM...
[15:01:32]   Checking for file '/etc/.enyelkmHIDE^IT.ko'     [ Not found ]
[15:01:32] Enye LKM                                          [ Not found ]
[15:01:32]
[15:01:32] Checking for Flea Linux Rootkit...
[15:01:32]   Checking for file '/etc/ld.so.hash'             [ Not found ]
[15:01:32]   Checking for file '/lib/security/.config/ssh/ssh_host_key' [ Not found ]
[15:01:32]   Checking for file '/lib/security/.config/ssh/ssh_host_key.pub' [ Not found ]
[15:01:32]   Checking for file '/lib/security/.config/ssh/ssh_random_seed' [ Not found ]
[15:01:32]   Checking for file '/usr/bin/ssh2d'              [ Not found ]
[15:01:32]   Checking for file '/usr/lib/ldlibns.so'         [ Not found ]
[15:01:32]   Checking for file '/usr/lib/ldlibpst.so'        [ Not found ]
[15:01:33]   Checking for file '/usr/lib/ldlibdu.so'         [ Not found ]
[15:01:33]   Checking for file '/usr/lib/ldlibct.so'         [ Not found ]
[15:01:33]   Checking for directory '/lib/security/.config/ssh' [ Not found ]
[15:01:33]   Checking for directory '/dev/..0'               [ Not found ]
[15:01:33]   Checking for directory '/dev/..0/backup'        [ Not found ]
[15:01:33] Flea Linux Rootkit                                [ Not found ]
[15:01:33]
[15:01:33] Checking for FreeBSD Rootkit...
[15:01:33]   Checking for file '/usr/lib/.fx/sched_host.2'   [ Not found ]
[15:01:33]   Checking for file '/usr/lib/.fx/random_d.2'     [ Not found ]
[15:01:33]   Checking for file '/usr/lib/.fx/set_pid.2'      [ Not found ]
[15:01:33]   Checking for file '/usr/lib/.fx/cons.saver'     [ Not found ]
[15:01:33]   Checking for file '/usr/lib/.fx/adore/adore/adore.ko' [ Not found ]
[15:01:33]   Checking for file '/bin/sysback'                [ Not found ]
[15:01:33]   Checking for file '/usr/local/bin/sysback'      [ Not found ]
[15:01:33]   Checking for directory '/usr/lib/.fx'           [ Not found ]
[15:01:33]   Checking for directory '/usr/lib/.fx/adore'     [ Not found ]
[15:01:33] FreeBSD Rootkit                                   [ Not found ]
[15:01:33]
[15:01:33] Checking for ****`it Rootkit...
[15:01:33]   Checking for file '/dev/proc/fuckit/hax0r'      [ Not found ]
[15:01:33]   Checking for file '/dev/proc/fuckit/hax0rshell' [ Not found ]
[15:01:33]   Checking for file '/dev/proc/fuckit/config/lports' [ Not found ]
[15:01:33]   Checking for file '/dev/proc/fuckit/config/rports' [ Not found ]
[15:01:33]   Checking for file '/dev/proc/fuckit/config/rkconf' [ Not found ]
[15:01:33]   Checking for file '/dev/proc/fuckit/config/password' [ Not found ]
[15:01:33]   Checking for file '/dev/proc/fuckit/config/progs' [ Not found ]
[15:01:33]   Checking for file '/dev/proc/system-bins/init'  [ Not found ]
[15:01:33] ****`it Rootkit                                   [ Not found ]
[15:01:33]
[15:01:33] Checking for GasKit Rootkit...
[15:01:33]   Checking for file '/dev/dev/gaskit/sshd/sshdd'  [ Not found ]
[15:01:33]   Checking for directory '/dev/dev'               [ Not found ]
[15:01:33]   Checking for directory '/dev/dev/gaskit'        [ Not found ]
[15:01:33]   Checking for directory '/dev/dev/gaskit/sshd'   [ Not found ]
[15:01:33] GasKit Rootkit                                    [ Not found ]
[15:01:33]
[15:01:33] Checking for Heroin LKM...
[15:01:33]   Checking for kernel symbol 'heroin'             [ Not found ]
[15:01:33] Heroin LKM                                        [ Not found ]
[15:01:33]
[15:01:33] Checking for HjC Kit...
[15:01:33]   Checking for directory '/dev/.hijackerz'        [ Not found ]
[15:01:33] HjC Kit                                           [ Not found ]
[15:01:33]
[15:01:33] Checking for ignoKit Rootkit...
[15:01:33]   Checking for file '/lib/defs/p'                 [ Not found ]
[15:01:33]   Checking for file '/lib/defs/q'                 [ Not found ]
[15:01:33]   Checking for file '/lib/defs/r'                 [ Not found ]
[15:01:34]   Checking for file '/lib/defs/s'                 [ Not found ]
[15:01:34]   Checking for file '/lib/defs/t'                 [ Not found ]
[15:01:34]   Checking for file '/usr/lib/defs/p'             [ Not found ]
[15:01:34]   Checking for file '/usr/lib/defs/q'             [ Not found ]
[15:01:34]   Checking for file '/usr/lib/defs/r'             [ Not found ]
[15:01:34]   Checking for file '/usr/lib/defs/s'             [ Not found ]
[15:01:34]   Checking for file '/usr/lib/defs/t'             [ Not found ]
[15:01:34]   Checking for file '/usr/lib/.libigno/pkunsec'   [ Not found ]
[15:01:34]   Checking for file '/usr/lib/.libigno/.igno/psybnc/psybnc' [ Not found ]
[15:01:34]   Checking for directory '/usr/lib/.libigno'      [ Not found ]
[15:01:34]   Checking for directory '/usr/lib/.libigno/.igno' [ Not found ]
[15:01:34] ignoKit Rootkit                                   [ Not found ]
[15:01:34]
[15:01:34] Checking for ImperalsS-FBRK Rootkit...
[15:01:34]   Checking for directory '/dev/fd/.88'            [ Not found ]
[15:01:34]   Checking for directory '/dev/fd/.99'            [ Not found ]
[15:01:34] ImperalsS-FBRK Rootkit                            [ Not found ]
[15:01:34]
[15:01:34] Checking for Irix Rootkit...
[15:01:34]   Checking for directory '/dev/pts/01'            [ Not found ]
[15:01:34]   Checking for directory '/dev/pts/01/backup'     [ Not found ]
[15:01:34]   Checking for directory '/dev/pts/01/etc'        [ Not found ]
[15:01:34]   Checking for directory '/dev/pts/01/tmp'        [ Not found ]
[15:01:34] Irix Rootkit                                      [ Not found ]
[15:01:34]
[15:01:34] Checking for Kitko Rootkit...
[15:01:34]   Checking for directory '/usr/src/redhat/SRPMS/...' [ Not found ]
[15:01:34] Kitko Rootkit                                     [ Not found ]
[15:01:34]
[15:01:34] Checking for Knark Rootkit...
[15:01:34]   Checking for file '/proc/knark/pids'            [ Not found ]
[15:01:34]   Checking for directory '/proc/knark'            [ Not found ]
[15:01:34] Knark Rootkit                                     [ Not found ]
[15:01:34]
[15:01:34] Checking for Li0n Worm...
[15:01:34]   Checking for file '/bin/in.telnetd'             [ Not found ]
[15:01:34]   Checking for file '/bin/mjy'                    [ Not found ]
[15:01:34]   Checking for file '/usr/man/man1/man1/lib/.lib/mjy' [ Not found ]
[15:01:34]   Checking for file '/usr/man/man1/man1/lib/.lib/in.telnetd' [ Not found ]
[15:01:34]   Checking for file '/usr/man/man1/man1/lib/.lib/.x' [ Not found ]
[15:01:34]   Checking for file '/dev/.lib/lib/scan/1i0n.sh'  [ Not found ]
[15:01:34]   Checking for file '/dev/.lib/lib/scan/hack.sh'  [ Not found ]
[15:01:34]   Checking for file '/dev/.lib/lib/scan/bind'     [ Not found ]
[15:01:34]   Checking for file '/dev/.lib/lib/scan/randb'    [ Not found ]
[15:01:34]   Checking for file '/dev/.lib/lib/scan/scan.sh'  [ Not found ]
[15:01:34]   Checking for file '/dev/.lib/lib/scan/pscan'    [ Not found ]
[15:01:34]   Checking for file '/dev/.lib/lib/scan/star.sh'  [ Not found ]
[15:01:34]   Checking for file '/dev/.lib/lib/scan/bindx.sh' [ Not found ]
[15:01:35]   Checking for file '/dev/.lib/lib/scan/bindname.log' [ Not found ]
[15:01:35]   Checking for file '/dev/.lib/lib/1i0n.sh'       [ Not found ]
[15:01:35]   Checking for file '/dev/.lib/lib/lib/netstat'   [ Not found ]
[15:01:35]   Checking for file '/dev/.lib/lib/lib/dev/.1addr' [ Not found ]
[15:01:35]   Checking for file '/dev/.lib/lib/lib/dev/.1logz' [ Not found ]
[15:01:35]   Checking for file '/dev/.lib/lib/lib/dev/.1proc' [ Not found ]
[15:01:35]   Checking for file '/dev/.lib/lib/lib/dev/.1file' [ Not found ]
[15:01:35] Li0n Worm                                         [ Not found ]
[15:01:35]
[15:01:35] Checking for Lockit / LJK2 Rootkit...
[15:01:35]   Checking for file '/usr/lib/libmen.oo/.LJK2/ssh_config' [ Not found ]
[15:01:35]   Checking for file '/usr/lib/libmen.oo/.LJK2/ssh_host_key' [ Not found ]
[15:01:35]   Checking for file '/usr/lib/libmen.oo/.LJK2/ssh_host_key.pub' [ Not found ]
[15:01:35]   Checking for file '/usr/lib/libmen.oo/.LJK2/ssh_random_seed*' [ Not found ]
[15:01:35]   Checking for file '/usr/lib/libmen.oo/.LJK2/sshd_config' [ Not found ]
[15:01:35]   Checking for file '/usr/lib/libmen.oo/.LJK2/backdoor/RK1bd' [ Not found ]
[15:01:35]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/du' [ Not found ]
[15:01:35]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/ifconfig' [ Not found ]
[15:01:35]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/inetd.conf' [ Not found ]
[15:01:35]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/locate' [ Not found ]
[15:01:35]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/login' [ Not found ]
[15:01:35]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/ls' [ Not found ]
[15:01:35]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/netstat' [ Not found ]
[15:01:35]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/ps' [ Not found ]
[15:01:35]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/pstree' [ Not found ]
[15:01:35]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/rc.sysinit' [ Not found ]
[15:01:35]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/syslogd' [ Not found ]
[15:01:35]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/tcpd' [ Not found ]
[15:01:35]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/top' [ Not found ]
[15:01:35]   Checking for file '/usr/lib/libmen.oo/.LJK2/clean/RK1sauber' [ Not found ]
[15:01:35]   Checking for file '/usr/lib/libmen.oo/.LJK2/clean/RK1wted' [ Not found ]
[15:01:35]   Checking for file '/usr/lib/libmen.oo/.LJK2/hack/RK1parser' [ Not found ]
[15:01:35]   Checking for file '/usr/lib/libmen.oo/.LJK2/hack/RK1sniff' [ Not found ]
[15:01:35]   Checking for file '/usr/lib/libmen.oo/.LJK2/hide/.RK1addr' [ Not found ]
[15:01:35]   Checking for file '/usr/lib/libmen.oo/.LJK2/hide/.RK1dir' [ Not found ]
[15:01:35]   Checking for file '/usr/lib/libmen.oo/.LJK2/hide/.RK1log' [ Not found ]
[15:01:35]   Checking for file '/usr/lib/libmen.oo/.LJK2/hide/.RK1proc' [ Not found ]
[15:01:35]   Checking for file '/usr/lib/libmen.oo/.LJK2/hide/RK1phidemod.c' [ Not found ]
[15:01:35]   Checking for file '/usr/lib/libmen.oo/.LJK2/modules/README.modules' [ Not found ]
[15:01:35]   Checking for file '/usr/lib/libmen.oo/.LJK2/modules/RK1hidem.c' [ Not found ]
[15:01:35]   Checking for file '/usr/lib/libmen.oo/.LJK2/modules/RK1phide' [ Not found ]
[15:01:35]   Checking for file '/usr/lib/libmen.oo/.LJK2/sshconfig/RK1ssh' [ Not found ]
[15:01:35]   Checking for directory '/usr/lib/libmen.oo/.LJK2' [ Not found ]
[15:01:35] Lockit / LJK2 Rootkit                             [ Not found ]
[15:01:35]
[15:01:35] Checking for Mood-NT Rootkit...
[15:01:35]   Checking for file '/sbin/init__mood-nt-_-_cthulhu' [ Not found ]
[15:01:36]   Checking for file '/_cthulhu/mood-nt.init'      [ Not found ]
[15:01:36]   Checking for file '/_cthulhu/mood-nt.conf'      [ Not found ]
[15:01:36]   Checking for file '/_cthulhu/mood-nt.sniff'     [ Not found ]
[15:01:36]   Checking for directory '/_cthulhu'              [ Not found ]
[15:01:36] Mood-NT Rootkit                                   [ Not found ]
[15:01:36]
[15:01:36] Checking for MRK Rootkit...
[15:01:36]   Checking for file '/dev/ida/.inet/pid'          [ Not found ]
[15:01:36]   Checking for file '/dev/ida/.inet/ssh_host_key' [ Not found ]
[15:01:36]   Checking for file '/dev/ida/.inet/ssh_random_seed' [ Not found ]
[15:01:36]   Checking for file '/dev/ida/.inet/tcp.log'      [ Not found ]
[15:01:36]   Checking for directory '/dev/ida/.inet'         [ Not found ]
[15:01:36]   Checking for directory '/var/spool/cron/.sh'    [ Not found ]
[15:01:36] MRK Rootkit                                       [ Not found ]
[15:01:36]
[15:01:36] Checking for Ni0 Rootkit...
[15:01:36]   Checking for file '/var/lock/subsys/...datafile.../...net...' [ Not found ]
[15:01:36]   Checking for file '/var/lock/subsys/...datafile.../...port...' [ Not found ]
[15:01:36]   Checking for file '/var/lock/subsys/...datafile.../...ps...' [ Not found ]
[15:01:36]   Checking for file '/var/lock/subsys/...datafile.../...file...' [ Not found ]
[15:01:36]   Checking for directory '/tmp/waza'              [ Not found ]
[15:01:36]   Checking for directory '/var/lock/subsys/...datafile...' [ Not found ]
[15:01:36]   Checking for directory '/usr/sbin/es'           [ Not found ]
[15:01:36] Ni0 Rootkit                                       [ Not found ]
[15:01:36]
[15:01:36] Checking for Ohhara Rootkit...
[15:01:36]   Checking for file '/var/lock/subsys/...datafile.../...datafile.../in.smbd.log' [ Not found ]
[15:01:36]   Checking for directory '/var/lock/subsys/...datafile...' [ Not found ]
[15:01:36]   Checking for directory '/var/lock/subsys/...datafile.../...datafile...' [ Not found ]
[15:01:36]   Checking for directory '/var/lock/subsys/...datafile.../...datafile.../bin' [ Not found ]
[15:01:36]   Checking for directory '/var/lock/subsys/...datafile.../...datafile.../usr/bin' [ Not found ]
[15:01:36]   Checking for directory '/var/lock/subsys/...datafile.../...datafile.../usr/sbin' [ Not found ]
[15:01:36]   Checking for directory '/var/lock/subsys/...datafile.../...datafile.../lib/security' [ Not found ]
[15:01:36] Ohhara Rootkit                                    [ Not found ]
[15:01:36]
[15:01:36] Checking for Optic Kit (Tux) Worm...
[15:01:36]   Checking for directory '/dev/tux'               [ Not found ]
[15:01:36]   Checking for directory '/usr/bin/xchk'          [ Not found ]
[15:01:36]   Checking for directory '/usr/bin/xsf'           [ Not found ]
[15:01:36]   Checking for directory '/usr/bin/ssh2d'         [ Not found ]
[15:01:36] Optic Kit (Tux) Worm                              [ Not found ]
[15:01:36]
[15:01:36] Checking for Oz Rootkit...
[15:01:36]   Checking for file '/dev/.oz/.nap/rkit/terror'   [ Not found ]
[15:01:36]   Checking for directory '/dev/.oz'               [ Not found ]
[15:01:36] Oz Rootkit                                        [ Not found ]
[15:01:36]
[15:01:36] Checking for Phalanx Rootkit...
[15:01:36]   Checking for file '/usr/share/.home.ph1/cb'     [ Not found ]
[15:01:36]   Checking for file '/etc/host.ph1'               [ Not found ]
[15:01:37]   Checking for file '/bin/host.ph1'               [ Not found ]
[15:01:37]   Checking for file '/usr/share/.home.ph1/phalanx' [ Not found ]
[15:01:37]   Checking for directory '/usr/share/.home.ph1'   [ Not found ]
[15:01:37] Phalanx Rootkit                                   [ Not found ]
[15:01:37]
[15:01:37] Checking for Phalanx Rootkit (strings)...
[15:01:37]   Checking for string 'phalanx'                   [ Not found ]
[15:01:37] Phalanx Rootkit (strings)                         [ Not found ]
[15:01:37]
[15:01:37] Checking for Portacelo Rootkit...
[15:01:37]   Checking for file '/var/lib/.../.ak'            [ Not found ]
[15:01:37]   Checking for file '/var/lib/.../.hk'            [ Not found ]
[15:01:37]   Checking for file '/var/lib/.../.rs'            [ Not found ]
[15:01:37]   Checking for file '/var/lib/.../.p'             [ Not found ]
[15:01:37]   Checking for file '/var/lib/.../getty'          [ Not found ]
[15:01:37]   Checking for file '/var/lib/.../lkt.o'          [ Not found ]
[15:01:37]   Checking for file '/var/lib/.../show'           [ Not found ]
[15:01:37]   Checking for file '/var/lib/.../nlkt.o'         [ Not found ]
[15:01:37]   Checking for file '/var/lib/.../ssshrc'         [ Not found ]
[15:01:37]   Checking for file '/var/lib/.../sssh_equiv'     [ Not found ]
[15:01:37]   Checking for file '/var/lib/.../sssh_known_hosts' [ Not found ]
[15:01:37]   Checking for file '/var/lib/.../sssh_pid'       [ Not found ]
[15:01:37]   Checking for file '~/.sssh/known_hosts'         [ Not found ]
[15:01:37] Portacelo Rootkit                                 [ Not found ]
[15:01:37]
[15:01:37] Checking for R3dstorm Toolkit...
[15:01:37]   Checking for file '/var/log/tk02/see_all'       [ Not found ]
[15:01:37]   Checking for file '/bin/.../sshd/sbin/sshd1'    [ Not found ]
[15:01:37]   Checking for file '/bin/.../hate/sk'            [ Not found ]
[15:01:37]   Checking for file '/bin/.../see_all'            [ Not found ]
[15:01:37]   Checking for directory '/var/log/tk02'          [ Not found ]
[15:01:37]   Checking for directory '/var/log/tk02/old'      [ Not found ]
[15:01:37]   Checking for directory '/bin/...'               [ Not found ]
[15:01:37] R3dstorm Toolkit                                  [ Not found ]
[15:01:37]
[15:01:37] Checking for RH-Sharpe's Rootkit...
[15:01:37]   Checking for file '/bin/lps'                    [ Not found ]
[15:01:37]   Checking for file '/usr/bin/lpstree'            [ Not found ]
[15:01:37]   Checking for file '/usr/bin/ltop'               [ Not found ]
[15:01:37]   Checking for file '/usr/bin/lkillall'           [ Not found ]
[15:01:37]   Checking for file '/usr/bin/ldu'                [ Not found ]
[15:01:37]   Checking for file '/usr/bin/lnetstat'           [ Not found ]
[15:01:37]   Checking for file '/usr/bin/wp'                 [ Not found ]
[15:01:37]   Checking for file '/usr/bin/shad'               [ Not found ]
[15:01:37]   Checking for file '/usr/bin/vadim'              [ Not found ]
[15:01:37]   Checking for file '/usr/bin/slice'              [ Not found ]
[15:01:37]   Checking for file '/usr/bin/cleaner'            [ Not found ]
[15:01:37]   Checking for file '/usr/include/rpcsvc/du'      [ Not found ]
[15:01:38] RH-Sharpe's Rootkit                               [ Not found ]
[15:01:38]
[15:01:38] Checking for RSHA's Rootkit...
[15:01:38]   Checking for file '/bin/kr4p'                   [ Not found ]
[15:01:38]   Checking for file '/usr/bin/n3tstat'            [ Not found ]
[15:01:38]   Checking for file '/usr/bin/chsh2'              [ Not found ]
[15:01:38]   Checking for file '/usr/bin/slice2'             [ Not found ]
[15:01:38]   Checking for file '/usr/src/linux/arch/alpha/lib/.lib/.1proc' [ Not found ]
[15:01:38]   Checking for file '/etc/rc.d/arch/alpha/lib/.lib/.1addr' [ Not found ]
[15:01:38]   Checking for directory '/etc/rc.d/rsha'         [ Not found ]
[15:01:38]   Checking for directory '/etc/rc.d/arch/alpha/lib/.lib' [ Not found ]
[15:01:38] RSHA's Rootkit                                    [ Not found ]
[15:01:38]
[15:01:38] Checking for Scalper Worm...
[15:01:38]   Checking for file '/tmp/.a'                     [ Not found ]
[15:01:38]   Checking for file '/tmp/.uua'                   [ Not found ]
[15:01:38] Scalper Worm                                      [ Not found ]
[15:01:38]
[15:01:38] Checking for Sebek LKM...
[15:01:38]   Checking for kernel symbol 'adore or sebek'     [ Not found ]
[15:01:38] Sebek LKM                                         [ Not found ]
[15:01:38]
[15:01:38] Checking for Shutdown Rootkit...
[15:01:38]   Checking for file '/usr/man/man5/.. /.dir/scannah/asus' [ Not found ]
[15:01:38]   Checking for file '/usr/man/man5/.. /.dir/see'  [ Not found ]
[15:01:38]   Checking for file '/usr/man/man5/.. /.dir/nscd' [ Not found ]
[15:01:38]   Checking for file '/usr/man/man5/.. /.dir/alpd' [ Not found ]
[15:01:38]   Checking for file '/etc/rc.d/rc.local '         [ Not found ]
[15:01:38]   Checking for directory '/usr/man/man5/.. /.dir' [ Not found ]
[15:01:38]   Checking for directory '/usr/man/man5/.. /.dir/scannah' [ Not found ]
[15:01:38]   Checking for directory '/etc/rc.d/rc0.d/.. /.dir' [ Not found ]
[15:01:38] Shutdown Rootkit                                  [ Not found ]
[15:01:38]
[15:01:38] Checking for SHV4 Rootkit...
[15:01:38]   Checking for file '/etc/ld.so.hash'             [ Not found ]
[15:01:38]   Checking for file '/lib/libext-2.so.7'          [ Not found ]
[15:01:39]   Checking for file '/lib/lidps1.so'              [ Not found ]
[15:01:39]   Checking for file '/usr/sbin/xntps'             [ Not found ]
[15:01:39]   Checking for directory '/lib/security/.config'  [ Not found ]
[15:01:39]   Checking for directory '/lib/security/.config/ssh' [ Not found ]
[15:01:39] SHV4 Rootkit                                      [ Not found ]
[15:01:39]
[15:01:39] Checking for SHV5 Rootkit...
[15:01:39]   Checking for file '/etc/sh.conf'                [ Not found ]
[15:01:39]   Checking for file '/dev/srd0'                   [ Not found ]
[15:01:39]   Checking for directory '/usr/lib/libsh'         [ Not found ]
[15:01:39] SHV5 Rootkit                                      [ Not found ]
[15:01:39]
[15:01:39] Checking for Sin Rootkit...
[15:01:39]   Checking for file '/dev/.haos/haos1/.f/Denyed'  [ Not found ]
[15:01:39]   Checking for file '/dev/ttyoa'                  [ Not found ]
[15:01:39]   Checking for file '/dev/ttyof'                  [ Not found ]
[15:01:39]   Checking for file '/dev/ttyop'                  [ Not found ]
[15:01:39]   Checking for file '/dev/ttyos'                  [ Not found ]
[15:01:39]   Checking for file '/usr/lib/.lib'               [ Not found ]
[15:01:39]   Checking for file '/usr/lib/sn/.X'              [ Not found ]
[15:01:39]   Checking for file '/usr/lib/sn/.sys'            [ Not found ]
[15:01:39]   Checking for file '/usr/lib/ld/.X'              [ Not found ]
[15:01:39]   Checking for file '/usr/man/man1/...'           [ Not found ]
[15:01:39]   Checking for file '/usr/man/man1/.../.m'        [ Not found ]
[15:01:39]   Checking for file '/usr/man/man1/.../.w'        [ Not found ]
[15:01:39]   Checking for directory '/usr/lib/sn'            [ Not found ]
[15:01:39]   Checking for directory '/usr/lib/man1/...'      [ Not found ]
[15:01:39]   Checking for directory '/dev/.haos'             [ Not found ]
[15:01:39] Sin Rootkit                                       [ Not found ]
[15:01:39]
[15:01:39] Checking for Slapper Worm...
[15:01:39]   Checking for file '/tmp/.bugtraq'               [ Not found ]
[15:01:39]   Checking for file '/tmp/.uubugtraq'             [ Not found ]
[15:01:39]   Checking for file '/tmp/.bugtraq.c'             [ Not found ]
[15:01:39]   Checking for file '/tmp/httpd'                  [ Not found ]
[15:01:39]   Checking for file '/tmp/.unlock'                [ Not found ]
[15:01:39]   Checking for file '/tmp/update'                 [ Not found ]
[15:01:39]   Checking for file '/tmp/.cinik'                 [ Not found ]
[15:01:39]   Checking for file '/tmp/.b'                     [ Not found ]
[15:01:39] Slapper Worm                                      [ Not found ]
[15:01:39]
[15:01:39] Checking for Sneakin Rootkit...
[15:01:39]   Checking for directory '/tmp/.X11-unix/.../rk'  [ Not found ]
[15:01:39] Sneakin Rootkit                                   [ Not found ]
[15:01:39]
[15:01:39] Checking for Suckit Rootkit...
[15:01:39]   Checking for file '/sbin/initsk12'              [ Not found ]
[15:01:39]   Checking for file '/sbin/initxrk'               [ Not found ]
[15:01:39]   Checking for file '/usr/bin/null'               [ Not found ]
[15:01:40]   Checking for file '/usr/share/locale/sk/.sk12/sk' [ Not found ]
[15:01:40]   Checking for file '/etc/rc.d/rc0.d/S23kmdac'    [ Not found ]
[15:01:40]   Checking for file '/etc/rc.d/rc1.d/S23kmdac'    [ Not found ]
[15:01:40]   Checking for file '/etc/rc.d/rc2.d/S23kmdac'    [ Not found ]
[15:01:40]   Checking for file '/etc/rc.d/rc3.d/S23kmdac'    [ Not found ]
[15:01:40]   Checking for file '/etc/rc.d/rc4.d/S23kmdac'    [ Not found ]
[15:01:40]   Checking for file '/etc/rc.d/rc5.d/S23kmdac'    [ Not found ]
[15:01:40]   Checking for file '/etc/rc.d/rc6.d/S23kmdac'    [ Not found ]
[15:01:40]   Checking for directory '/dev/sdhu0/tehdrakg'    [ Not found ]
[15:01:40]   Checking for directory '/etc/.MG'               [ Not found ]
[15:01:40]   Checking for directory '/usr/share/locale/sk/.sk12' [ Not found ]
[15:01:40]   Checking for directory '/usr/lib/perl5/site_perl/i386-linux/auto/TimeDate/.packlist' [ Not found ]
[15:01:40] Suckit Rootkit                                    [ Not found ]
[15:01:40]
[15:01:40] Checking for SunOS Rootkit...
[15:01:40]   Checking for file '/etc/ld.so.hash'             [ Not found ]
[15:01:40]   Checking for file '/lib/libext-2.so.7'          [ Not found ]
[15:01:40]   Checking for file '/usr/bin/ssh2d'              [ Not found ]
[15:01:40]   Checking for file '/bin/xlogin'                 [ Not found ]
[15:01:40]   Checking for file '/usr/lib/crth.o'             [ Not found ]
[15:01:40]   Checking for file '/usr/lib/crtz.o'             [ Not found ]
[15:01:40]   Checking for file '/sbin/login'                 [ Not found ]
[15:01:40]   Checking for file '/lib/security/.config/sn'    [ Not found ]
[15:01:40]   Checking for file '/lib/security/.config/lpsched' [ Not found ]
[15:01:40]   Checking for file '/dev/kmod'                   [ Not found ]
[15:01:40]   Checking for file '/dev/dos'                    [ Not found ]
[15:01:40] SunOS Rootkit                                     [ Not found ]
[15:01:40]
[15:01:40] Checking for SunOS / NSDAP Rootkit...
[15:01:40]   Checking for file '/usr/lib/vold/nsdap/.kit'    [ Not found ]
[15:01:40]   Checking for file '/usr/lib/vold/nsdap/defines' [ Not found ]
[15:01:40]   Checking for file '/usr/lib/vold/nsdap/patcher' [ Not found ]
[15:01:40]   Checking for file '/usr/lib/vold/nsdap/pg'      [ Not found ]
[15:01:40]   Checking for file '/usr/lib/vold/nsdap/cleaner' [ Not found ]
[15:01:40]   Checking for file '/usr/lib/vold/nsdap/utime'   [ Not found ]
[15:01:40]   Checking for file '/usr/lib/vold/nsdap/crypt'   [ Not found ]
[15:01:40]   Checking for file '/usr/lib/vold/nsdap/findkit' [ Not found ]
[15:01:40]   Checking for file '/usr/lib/vold/nsdap/sn2'     [ Not found ]
[15:01:40]   Checking for file '/usr/lib/vold/nsdap/sniffload' [ Not found ]
[15:01:40]   Checking for file '/usr/lib/vold/nsdap/runsniff' [ Not found ]
[15:01:40]   Checking for file '/usr/lib/lpset'              [ Not found ]
[15:01:40]   Checking for directory '/usr/lib/vold/nsdap'    [ Not found ]
[15:01:40] SunOS / NSDAP Rootkit                             [ Not found ]
[15:01:40]
[15:01:40] Checking for Superkit Rootkit...
[15:01:40]   Checking for file '/usr/man/.sman/sk'           [ Not found ]
[15:01:40] Superkit Rootkit                                  [ Not found ]
[15:01:41]
[15:01:41] Checking for TBD (Telnet BackDoor)...
[15:01:41]   Checking for file '/usr/lib/.tbd'               [ Not found ]
[15:01:41] TBD (Telnet BackDoor)                             [ Not found ]
[15:01:41]
[15:01:41] Checking for TeLeKiT Rootkit...
[15:01:41]   Checking for file '/usr/man/man3/.../TeLeKiT/bin/sniff' [ Not found ]
[15:01:41]   Checking for file '/usr/man/man3/.../TeLeKiT/bin/telnetd' [ Not found ]
[15:01:41]   Checking for file '/usr/man/man3/.../TeLeKiT/bin/teleulo' [ Not found ]
[15:01:41]   Checking for file '/usr/man/man3/.../cl'        [ Not found ]
[15:01:41]   Checking for file '/dev/ptyr'                   [ Not found ]
[15:01:41]   Checking for file '/dev/ptyp'                   [ Not found ]
[15:01:41]   Checking for file '/dev/ptyq'                   [ Not found ]
[15:01:41]   Checking for file '/dev/hda06'                  [ Not found ]
[15:01:41]   Checking for file '/usr/info/libc1.so'          [ Not found ]
[15:01:41]   Checking for directory '/usr/man/man3/...'      [ Not found ]
[15:01:41]   Checking for directory '/usr/man/man3/.../lsniff' [ Not found ]
[15:01:41]   Checking for directory '/usr/man/man3/.../TeLeKiT' [ Not found ]
[15:01:41] TeLeKiT Rootkit                                   [ Not found ]
[15:01:41]
[15:01:41] Checking for T0rn Rootkit...
[15:01:41]   Checking for file '/dev/.lib/lib/lib/t0rns'     [ Not found ]
[15:01:41]   Checking for file '/dev/.lib/lib/lib/du'        [ Not found ]
[15:01:41]   Checking for file '/dev/.lib/lib/lib/ls'        [ Not found ]
[15:01:41]   Checking for file '/dev/.lib/lib/lib/t0rnsb'    [ Not found ]
[15:01:41]   Checking for file '/dev/.lib/lib/lib/ps'        [ Not found ]
[15:01:41]   Checking for file '/dev/.lib/lib/lib/t0rnp'     [ Not found ]
[15:01:41]   Checking for file '/dev/.lib/lib/lib/find'      [ Not found ]
[15:01:41]   Checking for file '/dev/.lib/lib/lib/ifconfig'  [ Not found ]
[15:01:41]   Checking for file '/dev/.lib/lib/lib/pg'        [ Not found ]
[15:01:41]   Checking for file '/dev/.lib/lib/lib/ssh.tgz'   [ Not found ]
[15:01:41]   Checking for file '/dev/.lib/lib/lib/top'       [ Not found ]
[15:01:41]   Checking for file '/dev/.lib/lib/lib/sz'        [ Not found ]
[15:01:41]   Checking for file '/dev/.lib/lib/lib/login'     [ Not found ]
[15:01:41]   Checking for file '/dev/.lib/lib/lib/in.fingerd' [ Not found ]
[15:01:41]   Checking for file '/dev/.lib/lib/lib/1i0n.sh'   [ Not found ]
[15:01:41]   Checking for file '/dev/.lib/lib/lib/pstree'    [ Not found ]
[15:01:41]   Checking for file '/dev/.lib/lib/lib/in.telnetd' [ Not found ]
[15:01:41]   Checking for file '/dev/.lib/lib/lib/mjy'       [ Not found ]
[15:01:41]   Checking for file '/dev/.lib/lib/lib/sush'      [ Not found ]
[15:01:41]   Checking for file '/dev/.lib/lib/lib/tfn'       [ Not found ]
[15:01:41]   Checking for file '/dev/.lib/lib/lib/name'      [ Not found ]
[15:01:41]   Checking for file '/dev/.lib/lib/lib/getip.sh'  [ Not found ]
[15:01:41]   Checking for file '/usr/info/.torn/sh*'         [ Not found ]
[15:01:41]   Checking for file '/usr/src/.****/.1addr'       [ Not found ]
[15:01:41]   Checking for file '/usr/src/.****/.1file'       [ Not found ]
[15:01:41]   Checking for file '/usr/src/.****/.1proc'       [ Not found ]
[15:01:41]   Checking for file '/usr/src/.****/.1logz'       [ Not found ]
[15:01:42]   Checking for file '/usr/info/.t0rn'             [ Not found ]
[15:01:42]   Checking for directory '/dev/.lib'              [ Not found ]
[15:01:42]   Checking for directory '/dev/.lib/lib'          [ Not found ]
[15:01:42]   Checking for directory '/dev/.lib/lib/lib'      [ Not found ]
[15:01:42]   Checking for directory '/dev/.lib/lib/lib/dev'  [ Not found ]
[15:01:42]   Checking for directory '/dev/.lib/lib/scan'     [ Not found ]
[15:01:42]   Checking for directory '/usr/src/.****'         [ Not found ]
[15:01:42]   Checking for directory '/usr/man/man1/man1'     [ Not found ]
[15:01:42]   Checking for directory '/usr/man/man1/man1/lib' [ Not found ]
[15:01:42]   Checking for directory '/usr/man/man1/man1/lib/.lib' [ Not found ]
[15:01:42]   Checking for directory '/usr/man/man1/man1/lib/.lib/.backup' [ Not found ]
[15:01:42] T0rn Rootkit                                      [ Not found ]
[15:01:42]
[15:01:42] Checking for Trojanit Kit...
[15:01:42]   Checking for file '/bin/.ls'                    [ Not found ]
[15:01:42]   Checking for file '/bin/.ps'                    [ Not found ]
[15:01:42]   Checking for file '/bin/.netstat'               [ Not found ]
[15:01:42]   Checking for file '/usr/bin/.nop'               [ Not found ]
[15:01:42]   Checking for file '/usr/bin/.who'               [ Not found ]
[15:01:42] Trojanit Kit                                      [ Not found ]
[15:01:42]
[15:01:42] Checking for Tuxtendo Rootkit...
[15:01:42]   Checking for file '/dev/tux/.addr'              [ Not found ]
[15:01:42]   Checking for file '/dev/tux/.cron'              [ Not found ]
[15:01:42]   Checking for file '/dev/tux/.file'              [ Not found ]
[15:01:42]   Checking for file '/dev/tux/.log'               [ Not found ]
[15:01:42]   Checking for file '/dev/tux/.proc'              [ Not found ]
[15:01:42]   Checking for file '/dev/tux/backup/crontab'     [ Not found ]
[15:01:42]   Checking for file '/dev/tux/backup/df'          [ Not found ]
[15:01:42]   Checking for file '/dev/tux/backup/dir'         [ Not found ]
[15:01:42]   Checking for file '/dev/tux/backup/find'        [ Not found ]
[15:01:42]   Checking for file '/dev/tux/backup/ifconfig'    [ Not found ]
[15:01:42]   Checking for file '/dev/tux/backup/locate'      [ Not found ]
[15:01:42]   Checking for file '/dev/tux/backup/netstat'     [ Not found ]
[15:01:42]   Checking for file '/dev/tux/backup/ps'          [ Not found ]
[15:01:42]   Checking for file '/dev/tux/backup/pstree'      [ Not found ]
[15:01:42]   Checking for file '/dev/tux/backup/syslogd'     [ Not found ]
[15:01:42]   Checking for file '/dev/tux/backup/tcpd'        [ Not found ]
[15:01:42]   Checking for file '/dev/tux/backup/top'         [ Not found ]
[15:01:42]   Checking for file '/dev/tux/backup/updatedb'    [ Not found ]
[15:01:42]   Checking for file '/dev/tux/backup/vdir'        [ Not found ]
[15:01:42]   Checking for directory '/dev/tux'               [ Not found ]
[15:01:42]   Checking for directory '/dev/tux/ssh2'          [ Not found ]
[15:01:42]   Checking for directory '/dev/tux/backup'        [ Not found ]
[15:01:42] Tuxtendo Rootkit                                  [ Not found ]
[15:01:42]
[15:01:42] Checking for URK Rootkit...
[15:01:43]   Checking for file '/usr/man/man1/xxxxxxbin/find' [ Not found ]
[15:01:43]   Checking for file '/usr/man/man1/xxxxxxbin/du'  [ Not found ]
[15:01:43]   Checking for file '/usr/man/man1/xxxxxxbin/ps'  [ Not found ]
[15:01:43]   Checking for file '/tmp/conf.inf'               [ Not found ]
[15:01:43]   Checking for directory '/usr/man/man1/xxxxxxbin' [ Not found ]
[15:01:43] URK Rootkit                                       [ Not found ]
[15:01:43]
[15:01:43] Checking for VcKit Rootkit...
[15:01:43]   Checking for directory '/usr/include/linux/modules/lib.so' [ Not found ]
[15:01:43]   Checking for directory '/usr/include/linux/modules/lib.so/bin' [ Not found ]
[15:01:43] VcKit Rootkit                                     [ Not found ]
[15:01:43]
[15:01:43] Checking for Volc Rootkit...
[15:01:43]   Checking for directory '/var/spool/.recent'     [ Not found ]
[15:01:43]   Checking for directory '/var/spool/.recent/.files' [ Not found ]
[15:01:43]   Checking for directory '/usr/lib/volc'          [ Not found ]
[15:01:43]   Checking for directory '/usr/lib/volc/backup'   [ Not found ]
[15:01:43] Volc Rootkit                                      [ Not found ]
[15:01:43]
[15:01:43] Checking for X-Org SunOS Rootkit...
[15:01:43]   Checking for file '/usr/lib/libX.a/bin/tmpfl'   [ Not found ]
[15:01:43]   Checking for file '/usr/lib/libX.a/bin/rps'     [ Not found ]
[15:01:43]   Checking for file '/usr/bin/srload'             [ Not found ]
[15:01:43]   Checking for file '/usr/lib/libX.a/bin/sparcv7/rps' [ Not found ]
[15:01:43]   Checking for file '/usr/sbin/modcheck'          [ Not found ]
[15:01:43]   Checking for directory '/usr/lib/libX.a'        [ Not found ]
[15:01:43]   Checking for directory '/usr/lib/libX.a/bin'    [ Not found ]
[15:01:43]   Checking for directory '/usr/lib/libX.a/bin/sparcv7' [ Not found ]
[15:01:43]   Checking for directory '/usr/share/man...'      [ Not found ]
[15:01:43] X-Org SunOS Rootkit                               [ Not found ]
[15:01:43]
[15:01:43] Checking for zaRwT.KiT Rootkit...
[15:01:43]   Checking for file '/dev/rd/s/sendmeil'          [ Not found ]
[15:01:43]   Checking for file '/dev/ttyf'                   [ Not found ]
[15:01:43]   Checking for file '/dev/ttyp'                   [ Not found ]
[15:01:43]   Checking for file '/dev/ttyn'                   [ Not found ]
[15:01:43]   Checking for file '/rk/tulz'                    [ Not found ]
[15:01:43]   Checking for directory '/rk'                    [ Not found ]
[15:01:43]   Checking for directory '/dev/rd/s'              [ Not found ]
[15:01:43] zaRwT.KiT Rootkit                                 [ Not found ]
[15:01:43]
[15:01:43] Performing additional rootkit checks
[15:01:43] Info: Starting test name 'additional_rkts'
[15:01:43]
[15:01:43]   Performing Suckit Rookit additional checks
[15:01:43]     Checking /sbin/init link count                [ OK ]
[15:01:43]     Checking for hidden file extensions           [ None found ]
[15:01:43]     Running skdet command                         [ Skipped ]
[15:01:44] Info: Unable to find the 'skdet' command
[15:01:44]   Suckit Rookit additional checks                 [ OK ]
[15:01:44]
[15:01:44]   Performing check of possible rootkit files and directories
[15:01:44] Info: Starting test name 'possible_rkt_files'
[15:01:44]     Checking for file '/dev/sdr0'                 [ Not found ]
[15:01:44]     Checking for file '/tmp/.syshackfile'         [ Not found ]
[15:01:44]     Checking for file '/tmp/.bash_history'        [ Not found ]
[15:01:44]     Checking for file '/usr/info/.clib'           [ Not found ]
[15:01:44]     Checking for file '/usr/sbin/tcp.log'         [ Not found ]
[15:01:44]     Checking for file '/usr/bin/take/pid'         [ Not found ]
[15:01:44]     Checking for file '/sbin/create'              [ Not found ]
[15:01:44]     Checking for file '/dev/ttypz'                [ Not found ]
[15:01:44]     Checking for directory '/usr/bin/take'        [ Not found ]
[15:01:44]     Checking for directory '/usr/src/.lib'        [ Not found ]
[15:01:44]     Checking for directory '/usr/share/man/man1/.1c' [ Not found ]
[15:01:44]     Checking for directory '/lib/lblip.tk'        [ Not found ]
[15:01:44]     Checking for directory '/usr/sbin/...'        [ Not found ]
[15:01:44]     Checking for directory '/usr/share/.gun'      [ Not found ]
[15:01:44]   Checking for possible rootkit files and directories [ None found ]
[15:01:44]
[15:01:44]   Performing check for possible rootkit strings
[15:01:44] Info: Starting test name 'possible_rkt_strings'
[15:01:44] Info: Found local startup file: /etc/rc.local
[15:01:44]     Checking for string '/dev/proc/fuckit'        [ Not found ]
[15:01:44]     Checking for string '****'                    [ Not found ]
[15:01:44]     Checking for string 'backdoor'                [ Not found ]
[15:01:44]     Checking for string 'vt200'                   [ Not found ]
[15:01:44]     Checking for string '/usr/bin/xstat'          [ Not found ]
[15:01:44]     Checking for string '/bin/envpc'              [ Not found ]
[15:01:44]     Checking for string 'L4m3r0x'                 [ Not found ]
[15:01:44]     Checking for string '/usr/lib/.tbd'           [ Not found ]
[15:01:44]     Checking for string '/dev/ptyxx/.file'        [ Not found ]
[15:01:44]     Checking for string '/dev/sgk'                [ Not found ]
[15:01:44]     Checking for string '/var/lock/subsys/...datafile...' [ Not found ]
[15:01:44]     Checking for string '/usr/lib/.tbd'           [ Not found ]
[15:01:44]     Checking for string '/dev/proc/fuckit'        [ Not found ]
[15:01:45]     Checking for string '/lib/.sso'               [ Not found ]
[15:01:45]     Checking for string '/var/lock/subsys/...datafile...' [ Not found ]
[15:01:45]     Checking for string '/dev/caca'               [ Not found ]
[15:01:45]     Checking for string '/dev/ttyoa'              [ Not found ]
[15:01:45]     Checking for string 'syg'                     [ Not found ]
[15:01:45]     Checking for string '/dev/pts/01'             [ Not found ]
[15:01:45]     Checking for string 'tw33dl3'                 [ Not found ]
[15:01:45]     Checking for string 'psniff'                  [ Not found ]
[15:01:45]     Checking for string '/var/lock/subsys/...datafile...' [ Not found ]
[15:01:45]     Checking for string 'promiscuous'             [ Not found ]
[15:01:45]     Checking for string '/usr/lib/.tbd'           [ Not found ]
[15:01:45]     Checking for string '/dev/xdta'               [ Not found ]
[15:01:45]     Checking for string '/usr/lib/.tbd'           [ Not found ]
[15:01:45]     Checking for string 'in.inetd'                [ Not found ]
[15:01:45]     Checking for string '#<HIDE_.*>'              [ Not found ]
[15:01:45]     Checking for string 'bin/xchk'                [ Not found ]
[15:01:45]     Checking for string 'bin/xsf'                 [ Not found ]
[15:01:45]   Checking for possible rootkit strings           [ None found ]
[15:01:45]
[15:01:45] Performing malware checks
[15:01:45] Info: Starting test name 'malware'
[15:01:45]
[15:01:45] Info: Test 'deleted_files' disabled at users request.
[15:01:45] Info: Starting test name 'running_procs'
[15:01:45]   Checking running processes for suspicious files [ None found ]
[15:01:45]
[15:01:45] Info: Test 'hidden_procs' disabled at users request.
[15:01:46]
[15:01:46] Info: Test 'suspscan' disabled at users request.
[15:01:46]
[15:01:46]   Performing check for login backdoors
[15:01:46] Info: Starting test name 'other_malware'
[15:01:46]     Checking for '/bin/.login'                    [ Not found ]
[15:01:46]     Checking for '/sbin/.login'                   [ Not found ]
[15:01:46]   Checking for login backdoors                    [ None found ]
[15:01:46]
[15:01:46]   Performing check for suspicious directories
[15:01:46]     Checking for directory '/usr/X11R6/bin/.,/copy' [ Not found ]
[15:01:46]     Checking for directory '/dev/rd/cdb'          [ Not found ]
[15:01:46]   Checking for suspicious directories             [ None found ]
[15:01:46]
[15:01:46]   Checking for software intrusions                [ Skipped ]
[15:01:46] Info: Check skipped - tripwire not installed
[15:01:46]
[15:01:46]   Performing check for sniffer log files
[15:01:46]     Checking for file '/usr/lib/libice.log'       [ Not found ]
[15:01:46]   Checking for sniffer log files                  [ None found ]
[15:01:46]
[15:01:46] Performing trojan specific checks
[15:01:46] Info: Starting test name 'trojans'
[15:01:46] Info: Using inetd configuration file '/etc/inetd.conf'
[15:01:46]   Checking for enabled inetd services             [ OK ]
[15:01:46]
[15:01:46]   Performing check for enabled xinetd services
[15:01:46]   Checking for enabled xinetd services            [ Skipped ]
[15:01:46] Info: Check skipped - file '/etc/xinetd.conf' does not exist.
[15:01:46] Info: Apache backdoor check skipped: Apache modules and configuration directories not found.
[15:01:46]
[15:01:46] Performing Linux specific checks
[15:01:46] Info: Starting test name 'os_specific'
[15:01:46]   Checking kernel module commands                 [ OK ]
[15:01:46] Info: Using modules pathname of '/lib/modules/2.6.28-14-generic'
[15:01:46]   Checking kernel module names                    [ OK ]
[15:01:49]
[15:01:49] Checking the network...
[15:01:49] Info: Starting test name 'network'
[15:01:49] Info: Starting test name 'ports'
[15:01:49]
[15:01:49] Performing check for backdoor ports
[15:01:49]   Checking for UDP port 2001                      [ Not found ]
[15:01:49]   Checking for TCP port 2006                      [ Not found ]
[15:01:49]   Checking for TCP port 2128                      [ Not found ]
[15:01:49]   Checking for TCP port 14856                     [ Not found ]
[15:01:49]   Checking for TCP port 47107                     [ Not found ]
[15:01:49]   Checking for TCP port 60922                     [ Not found ]
[15:01:49]
[15:01:49] Performing checks on the network interfaces
[15:01:49] Info: Starting test name 'promisc'
[15:01:49]   Checking for promiscuous interfaces             [ None found ]
[15:01:49]
[15:01:49] Info: Test 'packet_cap_apps' disabled at users request.
[15:01:55]
[15:01:55] Checking the local host...
[15:01:55] Info: Starting test name 'local_host'
[15:01:55]
[15:01:55] Performing system boot checks
[15:01:55] Info: Starting test name 'startup_files'
[15:01:55]   Checking for local host name                    [ Found ]
[15:01:55] Info: Starting test name 'startup_malware'
[15:01:55] Info: Found local startup file: /etc/rc.local
[15:01:55]   Checking for local startup files                [ Found ]
[15:01:55]   Checking local startup files for malware        [ None found ]
[15:01:55] Info: Found system startup directory: /etc/init.d
[15:01:56]   Checking system startup files for malware       [ None found ]
[15:01:56]
[15:01:56] Performing group and account checks
[15:01:56] Info: Starting test name 'group_accounts'
[15:01:56]   Checking for passwd file                        [ Found ]
[15:01:56] Info: Found password file: /etc/passwd
[15:01:56]   Checking for root equivalent (UID 0) accounts   [ None found ]
[15:01:56] Info: Found shadow file: /etc/shadow
[15:01:56]   Checking for passwordless accounts              [ None found ]
[15:01:56] Info: Starting test name 'passwd_changes'
[15:01:56]   Checking for passwd file changes                [ None found ]
[15:01:56] Info: Starting test name 'group_changes'
[15:01:56]   Checking for group file changes                 [ None found ]
[15:01:56]   Checking root account shell history files       [ None found ]
[15:01:56]
[15:01:56] Performing system configuration file checks
[15:01:56] Info: Starting test name 'system_configs'
[15:01:56]   Checking for SSH configuration file             [ Not found ]
[15:01:56]   Checking for running syslog daemon              [ Found ]
[15:01:56]   Checking for syslog configuration file          [ Found ]
[15:01:56] Info: Found syslog configuration file: /etc/syslog.conf
[15:01:56]   Checking if syslog remote logging is allowed    [ Not allowed ]
[15:01:56]
[15:01:56] Performing filesystem checks
[15:01:56] Info: Starting test name 'filesystem'
[15:01:56] Info: SCAN_MODE_DEV set to 'THOROUGH'
[15:01:56]   Checking /dev for suspicious file types         [ Warning ]
[15:01:56] Warning: Suspicious file types found in /dev:
[15:01:56]          /dev/shm/pulse-shm-2424456577: data
[15:01:57]   Checking for hidden files and directories       [ None found ]
[15:02:02]
[15:02:02] Checking application versions...
[15:02:03] Info: Starting test name 'apps'
[15:02:03]   Checking version of Exim MTA                    [ OK ]
[15:02:03] Info: Application 'exim' version '4.69' found.
[15:02:03]   Checking version of GnuPG                       [ OK ]
[15:02:03] Info: Application 'gpg' version '1.4.9' found.
[15:02:03] Info: Application 'httpd' not found.
[15:02:03] Info: Application 'named' not found.
[15:02:03]   Checking version of OpenSSL                     [ OK ]
[15:02:03] Info: Application 'openssl' version '0.9.8g' found.
[15:02:03] Info: Application 'php' not found.
[15:02:03] Info: Application 'procmail' not found.
[15:02:03] Info: Application 'proftpd' not found.
[15:02:03] Info: Application 'sshd' not found.
[15:02:03] Info: Applications checked: 3 out of 9
[15:02:03]
[15:02:03] System checks summary
[15:02:03] =====================
[15:02:03]
[15:02:03] File properties checks...
[15:02:03] Files checked: 127
[15:02:03] Suspect files: 0
[15:02:03]
[15:02:03] Rootkit checks...
[15:02:03] Rootkits checked : 109
[15:02:03] Possible rootkits: 0
[15:02:03]
[15:02:03] Applications checks...
[15:02:03] Applications checked: 3
[15:02:03] Suspect applications: 0
[15:02:03]
[15:02:03] The system checks took: 51 seconds
[15:02:04]
[15:02:04] Info: End date is Sun Aug  2 15:02:04 BST 2009

Thanks
 rumo59

---

