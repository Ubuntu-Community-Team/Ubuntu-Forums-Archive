---
title: "Scan results of RKHUNTER..."
date: 2010-03-13
forum: New to Ubuntu
---

### Post by karthick87 on 2010-03-13
I have scanned my system for rootkits using **rkhunter **and this is my output..Could you pls tel me whether my system is safe or not..

```

karthick@Learners-desktop:~$ sudo rkhunter --check 
[ Rootkit Hunter version 1.3.2 ]

Checking system commands...

  Performing 'strings' command checks
    Checking 'strings' command                               [ OK ]

  Performing 'shared libraries' checks
    Checking for preloading variables                        [ None found ]
    Checking for preload file                                [ Not found ]
    Checking LD_LIBRARY_PATH variable                        [ Not found ]

  Performing file properties checks
    Checking for prerequisites                               [ OK ]
    /bin/bash                                                [ OK ]
    /bin/cat                                                 [ OK ]
    /bin/chmod                                               [ OK ]
    /bin/chown                                               [ OK ]
    /bin/cp                                                  [ OK ]
    /bin/date                                                [ OK ]
    /bin/df                                                  [ OK ]
    /bin/dmesg                                               [ OK ]
    /bin/echo                                                [ OK ]
    /bin/ed                                                  [ OK ]
    /bin/egrep                                               [ OK ]
    /bin/fgrep                                               [ OK ]
    /bin/fuser                                               [ OK ]
    /bin/grep                                                [ OK ]
    /bin/ip                                                  [ OK ]
    /bin/kill                                                [ OK ]
    /bin/login                                               [ OK ]
    /bin/ls                                                  [ OK ]
    /bin/lsmod                                               [ OK ]
    /bin/mktemp                                              [ OK ]
    /bin/more                                                [ OK ]
    /bin/mount                                               [ OK ]
    /bin/mv                                                  [ OK ]
    /bin/netstat                                             [ OK ]
    /bin/ps                                                  [ OK ]
    /bin/pwd                                                 [ OK ]
    /bin/readlink                                            [ OK ]
    /bin/sed                                                 [ OK ]
    /bin/sh                                                  [ OK ]
    /bin/su                                                  [ Warning ]
    /bin/touch                                               [ OK ]
    /bin/uname                                               [ OK ]
    /bin/which                                               [ OK ]
    /bin/dash                                                [ OK ]
    /usr/bin/awk                                             [ OK ]
    /usr/bin/basename                                        [ OK ]
    /usr/bin/chattr                                          [ OK ]
    /usr/bin/cut                                             [ OK ]
    /usr/bin/diff                                            [ OK ]
    /usr/bin/dirname                                         [ OK ]
    /usr/bin/dpkg                                            [ OK ]
    /usr/bin/dpkg-query                                      [ OK ]
    /usr/bin/du                                              [ OK ]
    /usr/bin/env                                             [ OK ]
    /usr/bin/file                                            [ OK ]
    /usr/bin/find                                            [ OK ]
    /usr/bin/GET                                             [ OK ]
    /usr/bin/groups                                          [ OK ]
    /usr/bin/head                                            [ OK ]
    /usr/bin/id                                              [ OK ]
    /usr/bin/killall                                         [ OK ]
    /usr/bin/last                                            [ OK ]
    /usr/bin/lastlog                                         [ OK ]
    /usr/bin/ldd                                             [ OK ]
    /usr/bin/less                                            [ OK ]
    /usr/bin/locate                                          [ OK ]
    /usr/bin/logger                                          [ OK ]
    /usr/bin/lsattr                                          [ OK ]
    /usr/bin/lsof                                            [ OK ]
    /usr/bin/md5sum                                          [ OK ]
    /usr/bin/mlocate                                         [ OK ]
    /usr/bin/newgrp                                          [ OK ]
    /usr/bin/passwd                                          [ OK ]
    /usr/bin/perl                                            [ OK ]
    /usr/bin/pstree                                          [ OK ]
    /usr/bin/rkhunter                                        [ OK ]
    /usr/bin/runcon                                          [ OK ]
    /usr/bin/sha1sum                                         [ OK ]
    /usr/bin/size                                            [ OK ]
    /usr/bin/sort                                            [ OK ]
    /usr/bin/stat                                            [ OK ]
    /usr/bin/strace                                          [ OK ]
    /usr/bin/strings                                         [ OK ]
    /usr/bin/sudo                                            [ OK ]
    /usr/bin/tail                                            [ OK ]
    /usr/bin/test                                            [ OK ]
    /usr/bin/top                                             [ OK ]
    /usr/bin/touch                                           [ OK ]
    /usr/bin/tr                                              [ OK ]
    /usr/bin/uniq                                            [ OK ]
    /usr/bin/users                                           [ OK ]
    /usr/bin/vmstat                                          [ OK ]
    /usr/bin/w                                               [ OK ]
    /usr/bin/watch                                           [ OK ]
    /usr/bin/wc                                              [ OK ]
    /usr/bin/wget                                            [ OK ]
    /usr/bin/whatis                                          [ OK ]
    /usr/bin/whereis                                         [ OK ]
    /usr/bin/which                                           [ OK ]
    /usr/bin/who                                             [ OK ]
    /usr/bin/whoami                                          [ OK ]
    /usr/bin/mawk                                            [ OK ]
    /usr/bin/lwp-request                                     [ OK ]
    /usr/bin/w.procps                                        [ OK ]
    /sbin/depmod                                             [ OK ]
    /sbin/ifconfig                                           [ OK ]
    /sbin/ifdown                                             [ OK ]
    /sbin/ifup                                               [ OK ]
    /sbin/init                                               [ OK ]
    /sbin/insmod                                             [ OK ]
    /sbin/ip                                                 [ OK ]
    /sbin/lsmod                                              [ OK ]
    /sbin/modinfo                                            [ OK ]
    /sbin/modprobe                                           [ OK ]
    /sbin/rmmod                                              [ OK ]
    /sbin/runlevel                                           [ OK ]
    /sbin/sulogin                                            [ OK ]
    /sbin/sysctl                                             [ OK ]
    /sbin/syslogd                                            [ OK ]
    /usr/sbin/adduser                                        [ OK ]
    /usr/sbin/chroot                                         [ OK ]
    /usr/sbin/cron                                           [ OK ]
    /usr/sbin/groupadd                                       [ OK ]
    /usr/sbin/groupdel                                       [ OK ]
    /usr/sbin/groupmod                                       [ OK ]
    /usr/sbin/grpck                                          [ OK ]
    /usr/sbin/inetd                                          [ Warning ]
    /usr/sbin/nologin                                        [ OK ]
    /usr/sbin/pwck                                           [ OK ]
    /usr/sbin/tcpd                                           [ OK ]
    /usr/sbin/useradd                                        [ OK ]
    /usr/sbin/userdel                                        [ OK ]
    /usr/sbin/usermod                                        [ OK ]
    /usr/sbin/vipw                                           [ OK ]

[Press <ENTER> to continue]

Checking for rootkits...

  Performing check of known rootkit files and directories
    55808 Trojan - Variant A                                 [ Not found ]
    ADM Worm                                                 [ Not found ]
    AjaKit Rootkit                                           [ Not found ]
    aPa Kit                                                  [ Not found ]
    Apache Worm                                              [ Not found ]
    Ambient (ark) Rootkit                                    [ Not found ]
    Balaur Rootkit                                           [ Not found ]
    BeastKit Rootkit                                         [ Not found ]
    beX2 Rootkit                                             [ Not found ]
    BOBKit Rootkit                                           [ Not found ]
    CiNIK Worm (Slapper.B variant)                           [ Not found ]
    Danny-Boy's Abuse Kit                                    [ Not found ]
    Devil RootKit                                            [ Not found ]
    Dica-Kit Rootkit                                         [ Not found ]
    Dreams Rootkit                                           [ Not found ]
    Duarawkz Rootkit                                         [ Not found ]
    Enye LKM                                                 [ Not found ]
    Flea Linux Rootkit                                       [ Not found ]
    FreeBSD Rootkit                                          [ Not found ]
    ****`it Rootkit                                          [ Not found ]
    GasKit Rootkit                                           [ Not found ]
    Heroin LKM                                               [ Not found ]
    HjC Kit                                                  [ Not found ]
    ignoKit Rootkit                                          [ Not found ]
    ImperalsS-FBRK Rootkit                                   [ Not found ]
    Irix Rootkit                                             [ Not found ]
    Kitko Rootkit                                            [ Not found ]
    Knark Rootkit                                            [ Not found ]
    Li0n Worm                                                [ Not found ]
    Lockit / LJK2 Rootkit                                    [ Not found ]
    Mood-NT Rootkit                                          [ Not found ]
    MRK Rootkit                                              [ Not found ]
    Ni0 Rootkit                                              [ Not found ]
    Ohhara Rootkit                                           [ Not found ]
    Optic Kit (Tux) Worm                                     [ Not found ]
    Oz Rootkit                                               [ Not found ]
    Phalanx Rootkit                                          [ Not found ]
    Phalanx Rootkit (strings)                                [ Not found ]
    Portacelo Rootkit                                        [ Not found ]
    R3dstorm Toolkit                                         [ Not found ]
    RH-Sharpe's Rootkit                                      [ Not found ]
    RSHA's Rootkit                                           [ Not found ]
    Scalper Worm                                             [ Not found ]
    Sebek LKM                                                [ Not found ]
    Shutdown Rootkit                                         [ Not found ]
    SHV4 Rootkit                                             [ Not found ]
    SHV5 Rootkit                                             [ Not found ]
    Sin Rootkit                                              [ Not found ]
    Slapper Worm                                             [ Not found ]
    Sneakin Rootkit                                          [ Not found ]
    Suckit Rootkit                                           [ Not found ]
    SunOS Rootkit                                            [ Not found ]
    SunOS / NSDAP Rootkit                                    [ Not found ]
    Superkit Rootkit                                         [ Not found ]
    TBD (Telnet BackDoor)                                    [ Not found ]
    TeLeKiT Rootkit                                          [ Not found ]
    T0rn Rootkit                                             [ Not found ]
    Trojanit Kit                                             [ Not found ]
    Tuxtendo Rootkit                                         [ Not found ]
    URK Rootkit                                              [ Not found ]
    VcKit Rootkit                                            [ Not found ]
    Volc Rootkit                                             [ Not found ]
    X-Org SunOS Rootkit                                      [ Not found ]
    zaRwT.KiT Rootkit                                        [ Not found ]

  Performing additional rootkit checks
    Suckit Rookit additional checks                          [ OK ]
    Checking for possible rootkit files and directories      [ None found ]
    Checking for possible rootkit strings                    [ None found ]

  Performing malware checks
    Checking running processes for suspicious files          [ None found ]
    Checking for login backdoors                             [ None found ]
    Checking for suspicious directories                      [ None found ]
    Checking for sniffer log files                           [ None found ]

  Performing trojan specific checks
    Checking for enabled inetd services                      [ Warning ]

  Performing Linux specific checks
    Checking kernel module commands                          [ OK ]
    Checking kernel module names                             [ OK ]

[Press <ENTER> to continue]

Checking the network...

  Performing check for backdoor ports
    Checking for TCP port 1524                               [ Not found ]
    Checking for TCP port 1984                               [ Not found ]
    Checking for UDP port 2001                               [ Not found ]
    Checking for TCP port 2006                               [ Not found ]
    Checking for TCP port 2128                               [ Not found ]
    Checking for TCP port 6666                               [ Not found ]
    Checking for TCP port 6667                               [ Not found ]
    Checking for TCP port 6668                               [ Not found ]
    Checking for TCP port 6669                               [ Not found ]
    Checking for TCP port 7000                               [ Not found ]
    Checking for TCP port 13000                              [ Not found ]
    Checking for TCP port 14856                              [ Not found ]
    Checking for TCP port 25000                              [ Not found ]
    Checking for TCP port 29812                              [ Not found ]
    Checking for TCP port 31337                              [ Not found ]
    Checking for TCP port 33369                              [ Not found ]
    Checking for TCP port 47107                              [ Not found ]
    Checking for TCP port 47018                              [ Not found ]
    Checking for TCP port 60922                              [ Not found ]
    Checking for TCP port 62883                              [ Not found ]
    Checking for TCP port 65535                              [ Not found ]

  Performing checks on the network interfaces
    Checking for promiscuous interfaces                      [ None found ]

[Press <ENTER> to continue]

Checking the local host...

  Performing system boot checks
    Checking for local host name                             [ Found ]
    Checking for local startup files                         [ Found ]
    Checking local startup files for malware                 [ None found ]
    Checking system startup files for malware                [ None found ]

  Performing group and account checks
    Checking for passwd file                                 [ Found ]
    Checking for root equivalent (UID 0) accounts            [ None found ]
    Checking for passwordless accounts                       [ None found ]
    Checking for passwd file changes                         [ None found ]
    Checking for group file changes                          [ None found ]
    Checking root account shell history files                [ OK ]

  Performing system configuration file checks
    Checking for SSH configuration file                      [ Not found ]
    Checking for running syslog daemon                       [ Found ]
    Checking for syslog configuration file                   [ Found ]
    Checking if syslog remote logging is allowed             [ Not allowed ]

  Performing filesystem checks
    Checking /dev for suspicious file types                  [ None found ]
    Checking for hidden files and directories                [ Warning ]

[Press <ENTER> to continue]

Checking application versions...

    Checking version of GnuPG                                [ Warning ]
    Checking version of OpenSSL                              [ Warning ]


System checks summary
=====================

File properties checks...
    Files checked: 124
    Suspect files: 2

Rootkit checks...
    Rootkits checked : 109
    Possible rootkits: 0

Applications checks...
    Applications checked: 2
    Suspect applications: 2

The system checks took: 2 minutes and 35 seconds

All results have been written to the logfile (/var/log/rkhunter.log)

One or more warnings have been found while checking the system.
Please check the log file (/var/log/rkhunter.log)
```


[B]
Log File
[/B]```

[20:50:16] Running Rootkit Hunter version 1.3.2 on Learners-desktop
[20:50:16]
[20:50:16] Info: Start date is Sat Mar 13 20:50:16 IST 2010
[20:50:16]
[20:50:16] Checking configuration file and command-line options...
[20:50:16] Info: Detected operating system is 'Linux'
[20:50:16] Info: Found O/S name: Ubuntu 9.04
[20:50:16] Info: Command line is /usr/bin/rkhunter --check
[20:50:16] Info: Environment shell is /bin/bash; rkhunter is using dash
[20:50:16] Info: Using configuration file '/etc/rkhunter.conf'
[20:50:16] Info: Installation directory is '/usr'
[20:50:16] Info: Using language 'en'
[20:50:16] Info: Using '/var/lib/rkhunter/db' as the database directory
[20:50:16] Info: Using '/usr/share/rkhunter/scripts' as the support script directory
[20:50:16] Info: Using '/usr/local/sbin /usr/local/bin /usr/sbin /usr/bin /sbin /bin /usr/X11R6/bin /bin /usr/bin /sbin /usr/sbin /usr/local/bin /usr/local/sbin /usr/libexec /usr/local/libexec' as the command directories
[20:50:16] Info: Using '/' as the root directory
[20:50:16] Info: Using '/var/lib/rkhunter/tmp' as the temporary directory
[20:50:16] Info: No mail-on-warning address configured
[20:50:16] Info: X will be automatically detected
[20:50:16] Info: Using second color set
[20:50:16] Info: Found the 'diff' command: /usr/bin/diff
[20:50:16] Info: Found the 'file' command: /usr/bin/file
[20:50:16] Info: Found the 'find' command: /usr/bin/find
[20:50:16] Info: Found the 'ifconfig' command: /sbin/ifconfig
[20:50:16] Info: Found the 'ip' command: /sbin/ip
[20:50:16] Info: Found the 'ldd' command: /usr/bin/ldd
[20:50:16] Info: Found the 'lsattr' command: /usr/bin/lsattr
[20:50:16] Info: Found the 'lsmod' command: /sbin/lsmod
[20:50:16] Info: Found the 'lsof' command: /usr/bin/lsof
[20:50:16] Info: Found the 'mktemp' command: /bin/mktemp
[20:50:16] Info: Found the 'netstat' command: /bin/netstat
[20:50:16] Info: Found the 'perl' command: /usr/bin/perl
[20:50:16] Info: Found the 'ps' command: /bin/ps
[20:50:16] Info: Found the 'pwd' command: /bin/pwd
[20:50:16] Info: Found the 'readlink' command: /bin/readlink
[20:50:16] Info: Found the 'sort' command: /usr/bin/sort
[20:50:16] Info: Found the 'stat' command: /usr/bin/stat
[20:50:16] Info: Found the 'strings' command: /usr/bin/strings
[20:50:16] Info: Found the 'uniq' command: /usr/bin/uniq
[20:50:16] Info: System is not using prelinking
[20:50:16] Info: Using the '/usr/bin/sha1sum' command for the file hash checks
[20:50:16] Info: Stored hash values used hash function '/usr/bin/sha1sum'
[20:50:16] Info: Stored hash values did not use a package manager
[20:50:16] Info: The hash function field index is set to 1
[20:50:16] Info: No package manager specified: using hash function '/usr/bin/sha1sum'
[20:50:16] Info: Previous file attributes were stored
[20:50:16] Info: Enabled tests are: all
[20:50:16] Info: Disabled tests are: suspscan hidden_procs deleted_files packet_cap_apps
[20:50:16] Info: Found ksym file '/proc/kallsyms'
[20:50:16]
[20:50:16] Checking if the O/S has changed since last time...
[20:50:16] Info: Nothing seems to have changed
[20:50:16]
[20:50:16] Starting system checks...
[20:50:16]
[20:50:16] Checking system commands...
[20:50:16] Info: Starting test name 'system_commands'
[20:50:16]
[20:50:16] Performing 'strings' command checks
[20:50:16] Info: Starting test name 'strings'
[20:50:16] Scanning for string /usr/sbin/ntpsx               [ OK ]
[20:50:16] Scanning for string /usr/lib/.../ls               [ OK ]
[20:50:16] Scanning for string /usr/lib/.../netstat          [ OK ]
[20:50:16] Scanning for string /usr/lib/.../lsof             [ OK ]
[20:50:16] Scanning for string /usr/lib/.../bkit-ssh/bkit-shdcfg [ OK ]
[20:50:17] Scanning for string /usr/lib/.../bkit-ssh/bkit-shhk [ OK ]
[20:50:17] Scanning for string /usr/lib/.../bkit-ssh/bkit-pw [ OK ]
[20:50:17] Scanning for string /usr/lib/.../bkit-ssh/bkit-shrs [ OK ]
[20:50:17] Scanning for string /usr/lib/.../uconf.inv        [ OK ]
[20:50:17] Scanning for string /usr/lib/.../psr              [ OK ]
[20:50:17] Scanning for string /usr/lib/.../find             [ OK ]
[20:50:17] Scanning for string /usr/lib/.../pstree           [ OK ]
[20:50:17] Scanning for string /usr/lib/.../slocate          [ OK ]
[20:50:17] Scanning for string /usr/lib/.../du               [ OK ]
[20:50:17] Scanning for string /usr/lib/.../top              [ OK ]
[20:50:17] Scanning for string /usr/lib/...                  [ OK ]
[20:50:17] Scanning for string /usr/lib/.../bkit-ssh         [ OK ]
[20:50:17] Scanning for string /usr/lib/.bkit-               [ OK ]
[20:50:17] Scanning for string /tmp/.bkp                     [ OK ]
[20:50:17] Scanning for string /tmp/.cinik                   [ OK ]
[20:50:17] Scanning for string /tmp/.font-unix/.cinik        [ OK ]
[20:50:17] Scanning for string /lib/.sso                     [ OK ]
[20:50:17] Scanning for string /lib/.so                      [ OK ]
[20:50:17] Scanning for string /var/run/...dica/clean        [ OK ]
[20:50:17] Scanning for string /var/run/...dica/xl           [ OK ]
[20:50:17] Scanning for string /var/run/...dica/xdr          [ OK ]
[20:50:17] Scanning for string /var/run/...dica/psg          [ OK ]
[20:50:17] Scanning for string /var/run/...dica/secure       [ OK ]
[20:50:17] Scanning for string /var/run/...dica/rdx          [ OK ]
[20:50:17] Scanning for string /var/run/...dica/va           [ OK ]
[20:50:17] Scanning for string /var/run/...dica/cl.sh        [ OK ]
[20:50:17] Scanning for string /usr/bin/.etc                 [ OK ]
[20:50:17] Scanning for string /usr/lib/.fx/sched_host.2     [ OK ]
[20:50:17] Scanning for string /usr/lib/.fx/random_d.2       [ OK ]
[20:50:17] Scanning for string /usr/lib/.fx/set_pid.2        [ OK ]
[20:50:17] Scanning for string /usr/lib/.fx/cons.saver       [ OK ]
[20:50:17] Scanning for string /usr/lib/.fx/adore/adore/adore.ko [ OK ]
[20:50:17] Scanning for string /bin/sysback                  [ OK ]
[20:50:17] Scanning for string /usr/local/bin/sysback        [ OK ]
[20:50:17] Scanning for string /usr/lib/.tbd                 [ OK ]
[20:50:17] Scanning for string /dev/.lib/lib/lib/t0rns       [ OK ]
[20:50:17] Scanning for string /dev/.lib/lib/lib/du          [ OK ]
[20:50:17] Scanning for string /dev/.lib/lib/lib/ls          [ OK ]
[20:50:17] Scanning for string /dev/.lib/lib/lib/t0rnsb      [ OK ]
[20:50:17] Scanning for string /dev/.lib/lib/lib/ps          [ OK ]
[20:50:17] Scanning for string /dev/.lib/lib/lib/t0rnp       [ OK ]
[20:50:17] Scanning for string /dev/.lib/lib/lib/find        [ OK ]
[20:50:17] Scanning for string /dev/.lib/lib/lib/ifconfig    [ OK ]
[20:50:17] Scanning for string /dev/.lib/lib/lib/pg          [ OK ]
[20:50:17] Scanning for string /dev/.lib/lib/lib/ssh.tgz     [ OK ]
[20:50:17] Scanning for string /dev/.lib/lib/lib/top         [ OK ]
[20:50:17] Scanning for string /dev/.lib/lib/lib/sz          [ OK ]
[20:50:18] Scanning for string /dev/.lib/lib/lib/login       [ OK ]
[20:50:18] Scanning for string /dev/.lib/lib/lib/in.fingerd  [ OK ]
[20:50:18] Scanning for string /dev/.lib/lib/lib/1i0n.sh     [ OK ]
[20:50:18] Scanning for string /dev/.lib/lib/lib/pstree      [ OK ]
[20:50:18] Scanning for string /dev/.lib/lib/lib/in.telnetd  [ OK ]
[20:50:18] Scanning for string /dev/.lib/lib/lib/mjy         [ OK ]
[20:50:18] Scanning for string /dev/.lib/lib/lib/sush        [ OK ]
[20:50:18] Scanning for string /dev/.lib/lib/lib/tfn         [ OK ]
[20:50:18] Scanning for string /dev/.lib/lib/lib/name        [ OK ]
[20:50:18] Scanning for string /dev/.lib/lib/lib/getip.sh    [ OK ]
[20:50:18] Scanning for string /usr/info/.torn/sh*           [ OK ]
[20:50:18] Scanning for string /usr/src/.****/.1addr         [ OK ]
[20:50:18] Scanning for string /usr/src/.****/.1file         [ OK ]
[20:50:18] Scanning for string /usr/src/.****/.1proc         [ OK ]
[20:50:18] Scanning for string /usr/src/.****/.1logz         [ OK ]
[20:50:18] Scanning for string /usr/info/.t0rn               [ OK ]
[20:50:18] Scanning for string /dev/.lib                     [ OK ]
[20:50:18] Scanning for string /dev/.lib/lib                 [ OK ]
[20:50:18] Scanning for string /dev/.lib/lib/lib             [ OK ]
[20:50:18] Scanning for string /dev/.lib/lib/lib/dev         [ OK ]
[20:50:18] Scanning for string /dev/.lib/lib/scan            [ OK ]
[20:50:18] Scanning for string /usr/src/.****                [ OK ]
[20:50:18] Scanning for string /usr/man/man1/man1            [ OK ]
[20:50:18] Scanning for string /usr/man/man1/man1/lib        [ OK ]
[20:50:18] Scanning for string /usr/man/man1/man1/lib/.lib   [ OK ]
[20:50:18] Scanning for string /usr/man/man1/man1/lib/.lib/.backup [ OK ]
[20:50:18]
[20:50:18] Performing 'shared libraries' checks
[20:50:18] Info: Starting test name 'shared_libs'
[20:50:18] Checking for preloading variables                 [ None found ]
[20:50:18] Checking for preload file                         [ Not found ]
[20:50:18] Info: Starting test name 'shared_libs_path'
[20:50:18] Checking LD_LIBRARY_PATH variable                 [ Not found ]
[20:50:18]
[20:50:18] Performing file properties checks
[20:50:18] Info: Starting test name 'properties'
[20:50:18] Checking for prerequisites                        [ OK ]
[20:50:18] /bin/bash                                         [ OK ]
[20:50:18] /bin/cat                                          [ OK ]
[20:50:18] /bin/chmod                                        [ OK ]
[20:50:19] /bin/chown                                        [ OK ]
[20:50:19] /bin/cp                                           [ OK ]
[20:50:19] /bin/date                                         [ OK ]
[20:50:19] /bin/df                                           [ OK ]
[20:50:19] /bin/dmesg                                        [ OK ]
[20:50:19] /bin/echo                                         [ OK ]
[20:50:19] /bin/ed                                           [ OK ]
[20:50:19] /bin/egrep                                        [ OK ]
[20:50:19] Info: Found file '/bin/egrep': it is whitelisted for the 'script replacement' check.
[20:50:19] /bin/fgrep                                        [ OK ]
[20:50:19] Info: Found file '/bin/fgrep': it is whitelisted for the 'script replacement' check.
[20:50:19] /bin/fuser                                        [ OK ]
[20:50:19] /bin/grep                                         [ OK ]
[20:50:19] /bin/ip                                           [ OK ]
[20:50:19] /bin/kill                                         [ OK ]
[20:50:20] /bin/login                                        [ OK ]
[20:50:20] /bin/ls                                           [ OK ]
[20:50:20] /bin/lsmod                                        [ OK ]
[20:50:20] /bin/mktemp                                       [ OK ]
[20:50:20] /bin/more                                         [ OK ]
[20:50:20] /bin/mount                                        [ OK ]
[20:50:20] /bin/mv                                           [ OK ]
[20:50:20] /bin/netstat                                      [ OK ]
[20:50:20] /bin/ps                                           [ OK ]
[20:50:20] /bin/pwd                                          [ OK ]
[20:50:20] /bin/readlink                                     [ OK ]
[20:50:20] /bin/sed                                          [ OK ]
[20:50:20] /bin/sh                                           [ OK ]
[20:50:20] /bin/su                                           [ Warning ]
[20:50:20] Warning: The file properties have changed:
[20:50:20]          File: /bin/su
[20:50:21]          Current permissions: 04750    Stored permissions: 04755
[20:50:21]          Current gid: 121    Stored gid: 0
[20:50:21] /bin/touch                                        [ OK ]
[20:50:21] /bin/uname                                        [ OK ]
[20:50:21] /bin/which                                        [ OK ]
[20:50:21] Info: Found file '/bin/which': it is whitelisted for the 'script replacement' check.
[20:50:21] /bin/dash                                         [ OK ]
[20:50:21] /usr/bin/awk                                      [ OK ]
[20:50:21] /usr/bin/basename                                 [ OK ]
[20:50:21] /usr/bin/chattr                                   [ OK ]
[20:50:21] /usr/bin/cut                                      [ OK ]
[20:50:21] /usr/bin/diff                                     [ OK ]
[20:50:21] /usr/bin/dirname                                  [ OK ]
[20:50:21] /usr/bin/dpkg                                     [ OK ]
[20:50:21] /usr/bin/dpkg-query                               [ OK ]
[20:50:22] /usr/bin/du                                       [ OK ]
[20:50:22] /usr/bin/env                                      [ OK ]
[20:50:22] /usr/bin/file                                     [ OK ]
[20:50:22] /usr/bin/find                                     [ OK ]
[20:50:22] /usr/bin/GET                                      [ OK ]
[20:50:22] /usr/bin/groups                                   [ OK ]
[20:50:22] Info: Found file '/usr/bin/groups': it is whitelisted for the 'script replacement' check.
[20:50:22] /usr/bin/head                                     [ OK ]
[20:50:22] /usr/bin/id                                       [ OK ]
[20:50:22] /usr/bin/killall                                  [ OK ]
[20:50:22] /usr/bin/last                                     [ OK ]
[20:50:22] /usr/bin/lastlog                                  [ OK ]
[20:50:22] /usr/bin/ldd                                      [ OK ]
[20:50:22] Info: Found file '/usr/bin/ldd': it is whitelisted for the 'script replacement' check.
[20:50:22] /usr/bin/less                                     [ OK ]
[20:50:22] /usr/bin/locate                                   [ OK ]
[20:50:22] /usr/bin/logger                                   [ OK ]
[20:50:23] /usr/bin/lsattr                                   [ OK ]
[20:50:23] /usr/bin/lsof                                     [ OK ]
[20:50:23] /usr/bin/md5sum                                   [ OK ]
[20:50:23] /usr/bin/mlocate                                  [ OK ]
[20:50:23] /usr/bin/newgrp                                   [ OK ]
[20:50:23] /usr/bin/passwd                                   [ OK ]
[20:50:23] /usr/bin/perl                                     [ OK ]
[20:50:23] /usr/bin/pstree                                   [ OK ]
[20:50:23] /usr/bin/rkhunter                                 [ OK ]
[20:50:23] /usr/bin/runcon                                   [ OK ]
[20:50:23] /usr/bin/sha1sum                                  [ OK ]
[20:50:23] /usr/bin/size                                     [ OK ]
[20:50:23] /usr/bin/sort                                     [ OK ]
[20:50:23] /usr/bin/stat                                     [ OK ]
[20:50:24] /usr/bin/strace                                   [ OK ]
[20:50:24] /usr/bin/strings                                  [ OK ]
[20:50:24] /usr/bin/sudo                                     [ OK ]
[20:50:24] /usr/bin/tail                                     [ OK ]
[20:50:24] /usr/bin/test                                     [ OK ]
[20:50:24] /usr/bin/top                                      [ OK ]
[20:50:24] /usr/bin/touch                                    [ OK ]
[20:50:24] /usr/bin/tr                                       [ OK ]
[20:50:24] /usr/bin/uniq                                     [ OK ]
[20:50:24] /usr/bin/users                                    [ OK ]
[20:50:24] /usr/bin/vmstat                                   [ OK ]
[20:50:24] /usr/bin/w                                        [ OK ]
[20:50:24] /usr/bin/watch                                    [ OK ]
[20:50:24] /usr/bin/wc                                       [ OK ]
[20:50:24] /usr/bin/wget                                     [ OK ]
[20:50:25] /usr/bin/whatis                                   [ OK ]
[20:50:25] /usr/bin/whereis                                  [ OK ]
[20:50:25] /usr/bin/which                                    [ OK ]
[20:50:25] /usr/bin/who                                      [ OK ]
[20:50:25] /usr/bin/whoami                                   [ OK ]
[20:50:25] /usr/bin/mawk                                     [ OK ]
[20:50:25] /usr/bin/lwp-request                              [ OK ]
[20:50:25] Info: Found file '/usr/bin/lwp-request': it is whitelisted for the 'script replacement' check.
[20:50:25] /usr/bin/w.procps                                 [ OK ]
[20:50:25] /sbin/depmod                                      [ OK ]
[20:50:25] /sbin/ifconfig                                    [ OK ]
[20:50:25] /sbin/ifdown                                      [ OK ]
[20:50:25] /sbin/ifup                                        [ OK ]
[20:50:25] /sbin/init                                        [ OK ]
[20:50:26] /sbin/insmod                                      [ OK ]
[20:50:26] /sbin/ip                                          [ OK ]
[20:50:26] /sbin/lsmod                                       [ OK ]
[20:50:26] /sbin/modinfo                                     [ OK ]
[20:50:26] /sbin/modprobe                                    [ OK ]
[20:50:26] /sbin/rmmod                                       [ OK ]
[20:50:26] /sbin/runlevel                                    [ OK ]
[20:50:26] /sbin/sulogin                                     [ OK ]
[20:50:26] /sbin/sysctl                                      [ OK ]
[20:50:26] /sbin/syslogd                                     [ OK ]
[20:50:26] /usr/sbin/adduser                                 [ OK ]
[20:50:26] Info: Found file '/usr/sbin/adduser': it is whitelisted for the 'script replacement' check.
[20:50:27] /usr/sbin/chroot                                  [ OK ]
[20:50:27] /usr/sbin/cron                                    [ OK ]
[20:50:27] /usr/sbin/groupadd                                [ OK ]
[20:50:27] /usr/sbin/groupdel                                [ OK ]
[20:50:27] /usr/sbin/groupmod                                [ OK ]
[20:50:27] /usr/sbin/grpck                                   [ OK ]
[20:50:27] /usr/sbin/inetd                                   [ Warning ]
[20:50:27] Warning: The file '/usr/sbin/inetd' exists on the system, but it is not present in the rkhunter.dat file.
[20:50:27] /usr/sbin/nologin                                 [ OK ]
[20:50:27] /usr/sbin/pwck                                    [ OK ]
[20:50:27] /usr/sbin/tcpd                                    [ OK ]
[20:50:27] /usr/sbin/useradd                                 [ OK ]
[20:50:28] /usr/sbin/userdel                                 [ OK ]
[20:50:28] /usr/sbin/usermod                                 [ OK ]
[20:50:28] /usr/sbin/vipw                                    [ OK ]
[20:51:04]
[20:51:04] Checking for rootkits...
[20:51:04] Info: Starting test name 'rootkits'
[20:51:04]
[20:51:04] Performing check of known rootkit files and directories
[20:51:04] Info: Starting test name 'known_rkts'
[20:51:04]
[20:51:04] Checking for 55808 Trojan - Variant A...
[20:51:04]   Checking for file '/tmp/.../r'                  [ Not found ]
[20:51:04]   Checking for file '/tmp/.../a'                  [ Not found ]
[20:51:04] 55808 Trojan - Variant A                          [ Not found ]
[20:51:04]
[20:51:04] Checking for ADM Worm...
[20:51:04]   Checking for string 'w0rm'                      [ Not found ]
[20:51:04] ADM Worm                                          [ Not found ]
[20:51:04]
[20:51:04] Checking for AjaKit Rootkit...
[20:51:04]   Checking for file '/dev/tux/.addr'              [ Not found ]
[20:51:04]   Checking for file '/dev/tux/.proc'              [ Not found ]
[20:51:04]   Checking for file '/dev/tux/.file'              [ Not found ]
[20:51:04]   Checking for file '/lib/.libgh-gh/cleaner'      [ Not found ]
[20:51:04]   Checking for file '/lib/.libgh-gh/Patch/patch'  [ Not found ]
[20:51:04]   Checking for file '/lib/.libgh-gh/sb0k'         [ Not found ]
[20:51:04]   Checking for directory '/dev/tux'               [ Not found ]
[20:51:04]   Checking for directory '/lib/.libgh-gh'         [ Not found ]
[20:51:04] AjaKit Rootkit                                    [ Not found ]
[20:51:04]
[20:51:04] Checking for aPa Kit...
[20:51:04]   Checking for file '/usr/share/.aPa'             [ Not found ]
[20:51:04] aPa Kit                                           [ Not found ]
[20:51:04]
[20:51:04] Checking for Apache Worm...
[20:51:04]   Checking for file '/bin/.log'                   [ Not found ]
[20:51:04] Apache Worm                                       [ Not found ]
[20:51:04]
[20:51:04] Checking for Ambient (ark) Rootkit...
[20:51:04]   Checking for file '/usr/lib/.ark?'              [ Not found ]
[20:51:04]   Checking for file '/dev/ptyxx/.log'             [ Not found ]
[20:51:04]   Checking for file '/dev/ptyxx/.file'            [ Not found ]
[20:51:04]   Checking for directory '/dev/ptyxx'             [ Not found ]
[20:51:04] Ambient (ark) Rootkit                             [ Not found ]
[20:51:04]
[20:51:04] Checking for Balaur Rootkit...
[20:51:04]   Checking for file '/usr/lib/liblog.o'           [ Not found ]
[20:51:04]   Checking for directory '/usr/lib/.kinetic'      [ Not found ]
[20:51:04]   Checking for directory '/usr/lib/.egcs'         [ Not found ]
[20:51:04]   Checking for directory '/usr/lib/.wormie'       [ Not found ]
[20:51:04] Balaur Rootkit                                    [ Not found ]
[20:51:04]
[20:51:04] Checking for BeastKit Rootkit...
[20:51:04]   Checking for file '/usr/sbin/arobia'            [ Not found ]
[20:51:04]   Checking for file '/usr/sbin/idrun'             [ Not found ]
[20:51:04]   Checking for file '/usr/lib/elm/arobia/elm'     [ Not found ]
[20:51:04]   Checking for file '/usr/lib/elm/arobia/elm/hk'  [ Not found ]
[20:51:04]   Checking for file '/usr/lib/elm/arobia/elm/hk.pub' [ Not found ]
[20:51:04]   Checking for file '/usr/lib/elm/arobia/elm/sc'  [ Not found ]
[20:51:04]   Checking for file '/usr/lib/elm/arobia/elm/sd.pp' [ Not found ]
[20:51:04]   Checking for file '/usr/lib/elm/arobia/elm/sdco' [ Not found ]
[20:51:04]   Checking for file '/usr/lib/elm/arobia/elm/srsd' [ Not found ]
[20:51:05]   Checking for directory '/lib/ldd.so/bktools'    [ Not found ]
[20:51:05] BeastKit Rootkit                                  [ Not found ]
[20:51:05]
[20:51:05] Checking for beX2 Rootkit...
[20:51:05]   Checking for directory '/usr/include/bex'       [ Not found ]
[20:51:05] beX2 Rootkit                                      [ Not found ]
[20:51:05]
[20:51:05] Checking for BOBKit Rootkit...
[20:51:05]   Checking for file '/usr/sbin/ntpsx'             [ Not found ]
[20:51:05]   Checking for file '/usr/lib/.../ls'             [ Not found ]
[20:51:05]   Checking for file '/usr/lib/.../netstat'        [ Not found ]
[20:51:05]   Checking for file '/usr/lib/.../lsof'           [ Not found ]
[20:51:05]   Checking for file '/usr/lib/.../bkit-ssh/bkit-shdcfg' [ Not found ]
[20:51:05]   Checking for file '/usr/lib/.../bkit-ssh/bkit-shhk' [ Not found ]
[20:51:05]   Checking for file '/usr/lib/.../bkit-ssh/bkit-pw' [ Not found ]
[20:51:05]   Checking for file '/usr/lib/.../bkit-ssh/bkit-shrs' [ Not found ]
[20:51:05]   Checking for file '/usr/lib/.../uconf.inv'      [ Not found ]
[20:51:05]   Checking for file '/usr/lib/.../psr'            [ Not found ]
[20:51:05]   Checking for file '/usr/lib/.../find'           [ Not found ]
[20:51:05]   Checking for file '/usr/lib/.../pstree'         [ Not found ]
[20:51:05]   Checking for file '/usr/lib/.../slocate'        [ Not found ]
[20:51:05]   Checking for file '/usr/lib/.../du'             [ Not found ]
[20:51:05]   Checking for file '/usr/lib/.../top'            [ Not found ]
[20:51:05]   Checking for directory '/usr/lib/...'           [ Not found ]
[20:51:05]   Checking for directory '/usr/lib/.../bkit-ssh'  [ Not found ]
[20:51:05]   Checking for directory '/usr/lib/.bkit-'        [ Not found ]
[20:51:05]   Checking for directory '/tmp/.bkp'              [ Not found ]
[20:51:05] BOBKit Rootkit                                    [ Not found ]
[20:51:05]
[20:51:05] Checking for CiNIK Worm (Slapper.B variant)...
[20:51:05]   Checking for file '/tmp/.cinik'                 [ Not found ]
[20:51:05]   Checking for directory '/tmp/.font-unix/.cinik' [ Not found ]
[20:51:05] CiNIK Worm (Slapper.B variant)                    [ Not found ]
[20:51:05]
[20:51:05] Checking for Danny-Boy's Abuse Kit...
[20:51:05]   Checking for file '/dev/mdev'                   [ Not found ]
[20:51:05]   Checking for file '/usr/lib/libX.a'             [ Not found ]
[20:51:05] Danny-Boy's Abuse Kit                             [ Not found ]
[20:51:05]
[20:51:05] Checking for Devil RootKit...
[20:51:05]   Checking for file '/var/lib/games/.src'         [ Not found ]
[20:51:05]   Checking for file '/dev/dsx'                    [ Not found ]
[20:51:05]   Checking for file '/dev/caca'                   [ Not found ]
[20:51:05] Devil RootKit                                     [ Not found ]
[20:51:05]
[20:51:05] Checking for Dica-Kit Rootkit...
[20:51:05]   Checking for file '/lib/.sso'                   [ Not found ]
[20:51:05]   Checking for file '/lib/.so'                    [ Not found ]
[20:51:05]   Checking for file '/var/run/...dica/clean'      [ Not found ]
[20:51:05]   Checking for file '/var/run/...dica/xl'         [ Not found ]
[20:51:05]   Checking for file '/var/run/...dica/xdr'        [ Not found ]
[20:51:05]   Checking for file '/var/run/...dica/psg'        [ Not found ]
[20:51:05]   Checking for file '/var/run/...dica/secure'     [ Not found ]
[20:51:05]   Checking for file '/var/run/...dica/rdx'        [ Not found ]
[20:51:05]   Checking for file '/var/run/...dica/va'         [ Not found ]
[20:51:05]   Checking for file '/var/run/...dica/cl.sh'      [ Not found ]
[20:51:06]   Checking for file '/usr/bin/.etc'               [ Not found ]
[20:51:06]   Checking for directory '/var/run/...dica'       [ Not found ]
[20:51:06]   Checking for directory '/var/run/...dica/mh'    [ Not found ]
[20:51:06]   Checking for directory '/var/run/...dica/scan'  [ Not found ]
[20:51:06] Dica-Kit Rootkit                                  [ Not found ]
[20:51:06]
[20:51:06] Checking for Dreams Rootkit...
[20:51:06]   Checking for file '/dev/ttyoa'                  [ Not found ]
[20:51:06]   Checking for file '/dev/ttyof'                  [ Not found ]
[20:51:06]   Checking for file '/dev/ttyop'                  [ Not found ]
[20:51:06]   Checking for file '/usr/bin/sense'              [ Not found ]
[20:51:06]   Checking for file '/usr/bin/sl2'                [ Not found ]
[20:51:06]   Checking for file '/usr/bin/logclear'           [ Not found ]
[20:51:06]   Checking for file '/usr/bin/(swapd)'            [ Not found ]
[20:51:06]   Checking for file '/usr/bin/snfs'               [ Not found ]
[20:51:06]   Checking for file '/usr/lib/libsss'             [ Not found ]
[20:51:06]   Checking for directory '/dev/ida/.hpd'          [ Not found ]
[20:51:06] Dreams Rootkit                                    [ Not found ]
[20:51:06]
[20:51:06] Checking for Duarawkz Rootkit...
[20:51:06]   Checking for file '/usr/bin/duarawkz/loginpass' [ Not found ]
[20:51:06]   Checking for directory '/usr/bin/duarawkz'      [ Not found ]
[20:51:06] Duarawkz Rootkit                                  [ Not found ]
[20:51:06]
[20:51:06] Checking for Enye LKM...
[20:51:06]   Checking for file '/etc/.enyelkmHIDE^IT.ko'     [ Not found ]
[20:51:06] Enye LKM                                          [ Not found ]
[20:51:06]
[20:51:06] Checking for Flea Linux Rootkit...
[20:51:06]   Checking for file '/etc/ld.so.hash'             [ Not found ]
[20:51:06]   Checking for file '/lib/security/.config/ssh/ssh_host_key' [ Not found ]
[20:51:06]   Checking for file '/lib/security/.config/ssh/ssh_host_key.pub' [ Not found ]
[20:51:06]   Checking for file '/lib/security/.config/ssh/ssh_random_seed' [ Not found ]
[20:51:06]   Checking for file '/usr/bin/ssh2d'              [ Not found ]
[20:51:06]   Checking for file '/usr/lib/ldlibns.so'         [ Not found ]
[20:51:06]   Checking for file '/usr/lib/ldlibpst.so'        [ Not found ]
[20:51:06]   Checking for file '/usr/lib/ldlibdu.so'         [ Not found ]
[20:51:06]   Checking for file '/usr/lib/ldlibct.so'         [ Not found ]
[20:51:06]   Checking for directory '/lib/security/.config/ssh' [ Not found ]
[20:51:06]   Checking for directory '/dev/..0'               [ Not found ]
[20:51:06]   Checking for directory '/dev/..0/backup'        [ Not found ]
[20:51:06] Flea Linux Rootkit                                [ Not found ]
[20:51:06]
[20:51:06] Checking for FreeBSD Rootkit...
[20:51:06]   Checking for file '/usr/lib/.fx/sched_host.2'   [ Not found ]
[20:51:06]   Checking for file '/usr/lib/.fx/random_d.2'     [ Not found ]
[20:51:06]   Checking for file '/usr/lib/.fx/set_pid.2'      [ Not found ]
[20:51:06]   Checking for file '/usr/lib/.fx/cons.saver'     [ Not found ]
[20:51:06]   Checking for file '/usr/lib/.fx/adore/adore/adore.ko' [ Not found ]
[20:51:06]   Checking for file '/bin/sysback'                [ Not found ]
[20:51:06]   Checking for file '/usr/local/bin/sysback'      [ Not found ]
[20:51:06]   Checking for directory '/usr/lib/.fx'           [ Not found ]
[20:51:06]   Checking for directory '/usr/lib/.fx/adore'     [ Not found ]
[20:51:06] FreeBSD Rootkit                                   [ Not found ]
[20:51:06]
[20:51:06] Checking for ****`it Rootkit...
[20:51:06]   Checking for file '/dev/proc/fuckit/hax0r'      [ Not found ]
[20:51:07]   Checking for file '/dev/proc/fuckit/hax0rshell' [ Not found ]
[20:51:07]   Checking for file '/dev/proc/fuckit/config/lports' [ Not found ]
[20:51:07]   Checking for file '/dev/proc/fuckit/config/rports' [ Not found ]
[20:51:07]   Checking for file '/dev/proc/fuckit/config/rkconf' [ Not found ]
[20:51:07]   Checking for file '/dev/proc/fuckit/config/password' [ Not found ]
[20:51:07]   Checking for file '/dev/proc/fuckit/config/progs' [ Not found ]
[20:51:07]   Checking for file '/dev/proc/system-bins/init'  [ Not found ]
[20:51:07] ****`it Rootkit                                   [ Not found ]
[20:51:07]
[20:51:07] Checking for GasKit Rootkit...
[20:51:07]   Checking for file '/dev/dev/gaskit/sshd/sshdd'  [ Not found ]
[20:51:07]   Checking for directory '/dev/dev'               [ Not found ]
[20:51:07]   Checking for directory '/dev/dev/gaskit'        [ Not found ]
[20:51:07]   Checking for directory '/dev/dev/gaskit/sshd'   [ Not found ]
[20:51:07] GasKit Rootkit                                    [ Not found ]
[20:51:07]
[20:51:07] Checking for Heroin LKM...
[20:51:07]   Checking for kernel symbol 'heroin'             [ Not found ]
[20:51:07] Heroin LKM                                        [ Not found ]
[20:51:07]
[20:51:07] Checking for HjC Kit...
[20:51:07]   Checking for directory '/dev/.hijackerz'        [ Not found ]
[20:51:07] HjC Kit                                           [ Not found ]
[20:51:07]
[20:51:07] Checking for ignoKit Rootkit...
[20:51:07]   Checking for file '/lib/defs/p'                 [ Not found ]
[20:51:07]   Checking for file '/lib/defs/q'                 [ Not found ]
[20:51:07]   Checking for file '/lib/defs/r'                 [ Not found ]
[20:51:07]   Checking for file '/lib/defs/s'                 [ Not found ]
[20:51:07]   Checking for file '/lib/defs/t'                 [ Not found ]
[20:51:07]   Checking for file '/usr/lib/defs/p'             [ Not found ]
[20:51:07]   Checking for file '/usr/lib/defs/q'             [ Not found ]
[20:51:07]   Checking for file '/usr/lib/defs/r'             [ Not found ]
[20:51:07]   Checking for file '/usr/lib/defs/s'             [ Not found ]
[20:51:07]   Checking for file '/usr/lib/defs/t'             [ Not found ]
[20:51:07]   Checking for file '/usr/lib/.libigno/pkunsec'   [ Not found ]
[20:51:07]   Checking for file '/usr/lib/.libigno/.igno/psybnc/psybnc' [ Not found ]
[20:51:07]   Checking for directory '/usr/lib/.libigno'      [ Not found ]
[20:51:07]   Checking for directory '/usr/lib/.libigno/.igno' [ Not found ]
[20:51:07] ignoKit Rootkit                                   [ Not found ]
[20:51:07]
[20:51:07] Checking for ImperalsS-FBRK Rootkit...
[20:51:07]   Checking for directory '/dev/fd/.88'            [ Not found ]
[20:51:07]   Checking for directory '/dev/fd/.99'            [ Not found ]
[20:51:07] ImperalsS-FBRK Rootkit                            [ Not found ]
[20:51:07]
[20:51:07] Checking for Irix Rootkit...
[20:51:07]   Checking for directory '/dev/pts/01'            [ Not found ]
[20:51:07]   Checking for directory '/dev/pts/01/backup'     [ Not found ]
[20:51:07]   Checking for directory '/dev/pts/01/etc'        [ Not found ]
[20:51:07]   Checking for directory '/dev/pts/01/tmp'        [ Not found ]
[20:51:07] Irix Rootkit                                      [ Not found ]
[20:51:07]
[20:51:07] Checking for Kitko Rootkit...
[20:51:07]   Checking for directory '/usr/src/redhat/SRPMS/...' [ Not found ]
[20:51:07] Kitko Rootkit                                     [ Not found ]
[20:51:07]
[20:51:07] Checking for Knark Rootkit...
[20:51:07]   Checking for file '/proc/knark/pids'            [ Not found ]
[20:51:07]   Checking for directory '/proc/knark'            [ Not found ]
[20:51:08] Knark Rootkit                                     [ Not found ]
[20:51:08]
[20:51:08] Checking for Li0n Worm...
[20:51:08]   Checking for file '/bin/in.telnetd'             [ Not found ]
[20:51:08]   Checking for file '/bin/mjy'                    [ Not found ]
[20:51:08]   Checking for file '/usr/man/man1/man1/lib/.lib/mjy' [ Not found ]
[20:51:08]   Checking for file '/usr/man/man1/man1/lib/.lib/in.telnetd' [ Not found ]
[20:51:08]   Checking for file '/usr/man/man1/man1/lib/.lib/.x' [ Not found ]
[20:51:08]   Checking for file '/dev/.lib/lib/scan/1i0n.sh'  [ Not found ]
[20:51:08]   Checking for file '/dev/.lib/lib/scan/hack.sh'  [ Not found ]
[20:51:08]   Checking for file '/dev/.lib/lib/scan/bind'     [ Not found ]
[20:51:08]   Checking for file '/dev/.lib/lib/scan/randb'    [ Not found ]
[20:51:08]   Checking for file '/dev/.lib/lib/scan/scan.sh'  [ Not found ]
[20:51:08]   Checking for file '/dev/.lib/lib/scan/pscan'    [ Not found ]
[20:51:08]   Checking for file '/dev/.lib/lib/scan/star.sh'  [ Not found ]
[20:51:08]   Checking for file '/dev/.lib/lib/scan/bindx.sh' [ Not found ]
[20:51:08]   Checking for file '/dev/.lib/lib/scan/bindname.log' [ Not found ]
[20:51:08]   Checking for file '/dev/.lib/lib/1i0n.sh'       [ Not found ]
[20:51:08]   Checking for file '/dev/.lib/lib/lib/netstat'   [ Not found ]
[20:51:08]   Checking for file '/dev/.lib/lib/lib/dev/.1addr' [ Not found ]
[20:51:08]   Checking for file '/dev/.lib/lib/lib/dev/.1logz' [ Not found ]
[20:51:08]   Checking for file '/dev/.lib/lib/lib/dev/.1proc' [ Not found ]
[20:51:08]   Checking for file '/dev/.lib/lib/lib/dev/.1file' [ Not found ]
[20:51:08] Li0n Worm                                         [ Not found ]
[20:51:08]
[20:51:08] Checking for Lockit / LJK2 Rootkit...
[20:51:08]   Checking for file '/usr/lib/libmen.oo/.LJK2/ssh_config' [ Not found ]
[20:51:08]   Checking for file '/usr/lib/libmen.oo/.LJK2/ssh_host_key' [ Not found ]
[20:51:08]   Checking for file '/usr/lib/libmen.oo/.LJK2/ssh_host_key.pub' [ Not found ]
[20:51:08]   Checking for file '/usr/lib/libmen.oo/.LJK2/ssh_random_seed*' [ Not found ]
[20:51:08]   Checking for file '/usr/lib/libmen.oo/.LJK2/sshd_config' [ Not found ]
[20:51:08]   Checking for file '/usr/lib/libmen.oo/.LJK2/backdoor/RK1bd' [ Not found ]
[20:51:08]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/du' [ Not found ]
[20:51:08]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/ifconfig' [ Not found ]
[20:51:08]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/inetd.conf' [ Not found ]
[20:51:08]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/locate' [ Not found ]
[20:51:08]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/login' [ Not found ]
[20:51:08]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/ls' [ Not found ]
[20:51:08]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/netstat' [ Not found ]
[20:51:08]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/ps' [ Not found ]
[20:51:08]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/pstree' [ Not found ]
[20:51:08]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/rc.sysinit' [ Not found ]
[20:51:08]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/syslogd' [ Not found ]
[20:51:08]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/tcpd' [ Not found ]
[20:51:08]   Checking for file '/usr/lib/libmen.oo/.LJK2/backup/top' [ Not found ]
[20:51:08]   Checking for file '/usr/lib/libmen.oo/.LJK2/clean/RK1sauber' [ Not found ]
[20:51:08]   Checking for file '/usr/lib/libmen.oo/.LJK2/clean/RK1wted' [ Not found ]
[20:51:08]   Checking for file '/usr/lib/libmen.oo/.LJK2/hack/RK1parser' [ Not found ]
[20:51:08]   Checking for file '/usr/lib/libmen.oo/.LJK2/hack/RK1sniff' [ Not found ]
[20:51:08]   Checking for file '/usr/lib/libmen.oo/.LJK2/hide/.RK1addr' [ Not found ]
[20:51:08]   Checking for file '/usr/lib/libmen.oo/.LJK2/hide/.RK1dir' [ Not found ]
[20:51:08]   Checking for file '/usr/lib/libmen.oo/.LJK2/hide/.RK1log' [ Not found ]
[20:51:09]   Checking for file '/usr/lib/libmen.oo/.LJK2/hide/.RK1proc' [ Not found ]
[20:51:09]   Checking for file '/usr/lib/libmen.oo/.LJK2/hide/RK1phidemod.c' [ Not found ]
[20:51:09]   Checking for file '/usr/lib/libmen.oo/.LJK2/modules/README.modules' [ Not found ]
[20:51:09]   Checking for file '/usr/lib/libmen.oo/.LJK2/modules/RK1hidem.c' [ Not found ]
[20:51:09]   Checking for file '/usr/lib/libmen.oo/.LJK2/modules/RK1phide' [ Not found ]
[20:51:09]   Checking for file '/usr/lib/libmen.oo/.LJK2/sshconfig/RK1ssh' [ Not found ]
[20:51:09]   Checking for directory '/usr/lib/libmen.oo/.LJK2' [ Not found ]
[20:51:09] Lockit / LJK2 Rootkit                             [ Not found ]
[20:51:09]
[20:51:09] Checking for Mood-NT Rootkit...
[20:51:09]   Checking for file '/sbin/init__mood-nt-_-_cthulhu' [ Not found ]
[20:51:09]   Checking for file '/_cthulhu/mood-nt.init'      [ Not found ]
[20:51:09]   Checking for file '/_cthulhu/mood-nt.conf'      [ Not found ]
[20:51:09]   Checking for file '/_cthulhu/mood-nt.sniff'     [ Not found ]
[20:51:09]   Checking for directory '/_cthulhu'              [ Not found ]
[20:51:09] Mood-NT Rootkit                                   [ Not found ]
[20:51:09]
[20:51:09] Checking for MRK Rootkit...
[20:51:09]   Checking for file '/dev/ida/.inet/pid'          [ Not found ]
[20:51:09]   Checking for file '/dev/ida/.inet/ssh_host_key' [ Not found ]
[20:51:09]   Checking for file '/dev/ida/.inet/ssh_random_seed' [ Not found ]
[20:51:09]   Checking for file '/dev/ida/.inet/tcp.log'      [ Not found ]
[20:51:09]   Checking for directory '/dev/ida/.inet'         [ Not found ]
[20:51:09]   Checking for directory '/var/spool/cron/.sh'    [ Not found ]
[20:51:09] MRK Rootkit                                       [ Not found ]
[20:51:09]
[20:51:09] Checking for Ni0 Rootkit...
[20:51:09]   Checking for file '/var/lock/subsys/...datafile.../...net...' [ Not found ]
[20:51:09]   Checking for file '/var/lock/subsys/...datafile.../...port...' [ Not found ]
[20:51:09]   Checking for file '/var/lock/subsys/...datafile.../...ps...' [ Not found ]
[20:51:09]   Checking for file '/var/lock/subsys/...datafile.../...file...' [ Not found ]
[20:51:09]   Checking for directory '/tmp/waza'              [ Not found ]
[20:51:09]   Checking for directory '/var/lock/subsys/...datafile...' [ Not found ]
[20:51:09]   Checking for directory '/usr/sbin/es'           [ Not found ]
[20:51:09] Ni0 Rootkit                                       [ Not found ]
[20:51:09]
[20:51:09] Checking for Ohhara Rootkit...
[20:51:09]   Checking for file '/var/lock/subsys/...datafile.../...datafile.../in.smbd.log' [ Not found ]
[20:51:09]   Checking for directory '/var/lock/subsys/...datafile...' [ Not found ]
[20:51:09]   Checking for directory '/var/lock/subsys/...datafile.../...datafile...' [ Not found ]
[20:51:09]   Checking for directory '/var/lock/subsys/...datafile.../...datafile.../bin' [ Not found ]
[20:51:09]   Checking for directory '/var/lock/subsys/...datafile.../...datafile.../usr/bin' [ Not found ]
[20:51:09]   Checking for directory '/var/lock/subsys/...datafile.../...datafile.../usr/sbin' [ Not found ]
[20:51:09]   Checking for directory '/var/lock/subsys/...datafile.../...datafile.../lib/security' [ Not found ]
[20:51:09] Ohhara Rootkit                                    [ Not found ]
[20:51:09]
[20:51:09] Checking for Optic Kit (Tux) Worm...
[20:51:09]   Checking for directory '/dev/tux'               [ Not found ]
[20:51:09]   Checking for directory '/usr/bin/xchk'          [ Not found ]
[20:51:09]   Checking for directory '/usr/bin/xsf'           [ Not found ]
[20:51:09]   Checking for directory '/usr/bin/ssh2d'         [ Not found ]
[20:51:09] Optic Kit (Tux) Worm                              [ Not found ]
[20:51:09]
[20:51:09] Checking for Oz Rootkit...
[20:51:09]   Checking for file '/dev/.oz/.nap/rkit/terror'   [ Not found ]
[20:51:09]   Checking for directory '/dev/.oz'               [ Not found ]
[20:51:09] Oz Rootkit                                        [ Not found ]
[20:51:09]
[20:51:09] Checking for Phalanx Rootkit...
[20:51:09]   Checking for file '/usr/share/.home.ph1/cb'     [ Not found ]
[20:51:10]   Checking for file '/etc/host.ph1'               [ Not found ]
[20:51:10]   Checking for file '/bin/host.ph1'               [ Not found ]
[20:51:10]   Checking for file '/usr/share/.home.ph1/phalanx' [ Not found ]
[20:51:10]   Checking for directory '/usr/share/.home.ph1'   [ Not found ]
[20:51:10] Phalanx Rootkit                                   [ Not found ]
[20:51:10]
[20:51:10] Checking for Phalanx Rootkit (strings)...
[20:51:10]   Checking for string 'phalanx'                   [ Not found ]
[20:51:10] Phalanx Rootkit (strings)                         [ Not found ]
[20:51:10]
[20:51:10] Checking for Portacelo Rootkit...
[20:51:10]   Checking for file '/var/lib/.../.ak'            [ Not found ]
[20:51:10]   Checking for file '/var/lib/.../.hk'            [ Not found ]
[20:51:10]   Checking for file '/var/lib/.../.rs'            [ Not found ]
[20:51:10]   Checking for file '/var/lib/.../.p'             [ Not found ]
[20:51:10]   Checking for file '/var/lib/.../getty'          [ Not found ]
[20:51:10]   Checking for file '/var/lib/.../lkt.o'          [ Not found ]
[20:51:10]   Checking for file '/var/lib/.../show'           [ Not found ]
[20:51:10]   Checking for file '/var/lib/.../nlkt.o'         [ Not found ]
[20:51:10]   Checking for file '/var/lib/.../ssshrc'         [ Not found ]
[20:51:10]   Checking for file '/var/lib/.../sssh_equiv'     [ Not found ]
[20:51:10]   Checking for file '/var/lib/.../sssh_known_hosts' [ Not found ]
[20:51:10]   Checking for file '/var/lib/.../sssh_pid'       [ Not found ]
[20:51:10]   Checking for file '~/.sssh/known_hosts'         [ Not found ]
[20:51:10] Portacelo Rootkit                                 [ Not found ]
[20:51:10]
[20:51:10] Checking for R3dstorm Toolkit...
[20:51:10]   Checking for file '/var/log/tk02/see_all'       [ Not found ]
[20:51:10]   Checking for file '/bin/.../sshd/sbin/sshd1'    [ Not found ]
[20:51:10]   Checking for file '/bin/.../hate/sk'            [ Not found ]
[20:51:10]   Checking for file '/bin/.../see_all'            [ Not found ]
[20:51:10]   Checking for directory '/var/log/tk02'          [ Not found ]
[20:51:10]   Checking for directory '/var/log/tk02/old'      [ Not found ]
[20:51:10]   Checking for directory '/bin/...'               [ Not found ]
[20:51:10] R3dstorm Toolkit                                  [ Not found ]
[20:51:10]
[20:51:10] Checking for RH-Sharpe's Rootkit...
[20:51:10]   Checking for file '/bin/lps'                    [ Not found ]
[20:51:10]   Checking for file '/usr/bin/lpstree'            [ Not found ]
[20:51:10]   Checking for file '/usr/bin/ltop'               [ Not found ]
[20:51:10]   Checking for file '/usr/bin/lkillall'           [ Not found ]
[20:51:10]   Checking for file '/usr/bin/ldu'                [ Not found ]
[20:51:10]   Checking for file '/usr/bin/lnetstat'           [ Not found ]
[20:51:10]   Checking for file '/usr/bin/wp'                 [ Not found ]
[20:51:10]   Checking for file '/usr/bin/shad'               [ Not found ]
[20:51:10]   Checking for file '/usr/bin/vadim'              [ Not found ]
[20:51:10]   Checking for file '/usr/bin/slice'              [ Not found ]
[20:51:10]   Checking for file '/usr/bin/cleaner'            [ Not found ]
[20:51:10]   Checking for file '/usr/include/rpcsvc/du'      [ Not found ]
[20:51:10] RH-Sharpe's Rootkit                               [ Not found ]
[20:51:10]
[20:51:10] Checking for RSHA's Rootkit...
[20:51:10]   Checking for file '/bin/kr4p'                   [ Not found ]
[20:51:10]   Checking for file '/usr/bin/n3tstat'            [ Not found ]
[20:51:10]   Checking for file '/usr/bin/chsh2'              [ Not found ]
[20:51:10]   Checking for file '/usr/bin/slice2'             [ Not found ]
[20:51:10]   Checking for file '/usr/src/linux/arch/alpha/lib/.lib/.1proc' [ Not found ]
[20:51:11]   Checking for file '/etc/rc.d/arch/alpha/lib/.lib/.1addr' [ Not found ]
[20:51:11]   Checking for directory '/etc/rc.d/rsha'         [ Not found ]
[20:51:11]   Checking for directory '/etc/rc.d/arch/alpha/lib/.lib' [ Not found ]
[20:51:11] RSHA's Rootkit                                    [ Not found ]
[20:51:11]
[20:51:11] Checking for Scalper Worm...
[20:51:11]   Checking for file '/tmp/.a'                     [ Not found ]
[20:51:11]   Checking for file '/tmp/.uua'                   [ Not found ]
[20:51:11] Scalper Worm                                      [ Not found ]
[20:51:11]
[20:51:11] Checking for Sebek LKM...
[20:51:11]   Checking for kernel symbol 'adore or sebek'     [ Not found ]
[20:51:11] Sebek LKM                                         [ Not found ]
[20:51:11]
[20:51:11] Checking for Shutdown Rootkit...
[20:51:11]   Checking for file '/usr/man/man5/.. /.dir/scannah/asus' [ Not found ]
[20:51:11]   Checking for file '/usr/man/man5/.. /.dir/see'  [ Not found ]
[20:51:11]   Checking for file '/usr/man/man5/.. /.dir/nscd' [ Not found ]
[20:51:11]   Checking for file '/usr/man/man5/.. /.dir/alpd' [ Not found ]
[20:51:11]   Checking for file '/etc/rc.d/rc.local '         [ Not found ]
[20:51:11]   Checking for directory '/usr/man/man5/.. /.dir' [ Not found ]
[20:51:11]   Checking for directory '/usr/man/man5/.. /.dir/scannah' [ Not found ]
[20:51:11]   Checking for directory '/etc/rc.d/rc0.d/.. /.dir' [ Not found ]
[20:51:11] Shutdown Rootkit                                  [ Not found ]
[20:51:11]
[20:51:11] Checking for SHV4 Rootkit...
[20:51:11]   Checking for file '/etc/ld.so.hash'             [ Not found ]
[20:51:11]   Checking for file '/lib/libext-2.so.7'          [ Not found ]
[20:51:11]   Checking for file '/lib/lidps1.so'              [ Not found ]
[20:51:11]   Checking for file '/usr/sbin/xntps'             [ Not found ]
[20:51:11]   Checking for directory '/lib/security/.config'  [ Not found ]
[20:51:11]   Checking for directory '/lib/security/.config/ssh' [ Not found ]
[20:51:11] SHV4 Rootkit                                      [ Not found ]
[20:51:11]
[20:51:11] Checking for SHV5 Rootkit...
[20:51:11]   Checking for file '/etc/sh.conf'                [ Not found ]
[20:51:11]   Checking for file '/dev/srd0'                   [ Not found ]
[20:51:11]   Checking for directory '/usr/lib/libsh'         [ Not found ]
[20:51:11] SHV5 Rootkit                                      [ Not found ]
[20:51:11]
[20:51:11] Checking for Sin Rootkit...
[20:51:11]   Checking for file '/dev/.haos/haos1/.f/Denyed'  [ Not found ]
[20:51:11]   Checking for file '/dev/ttyoa'                  [ Not found ]
[20:51:11]   Checking for file '/dev/ttyof'                  [ Not found ]
[20:51:11]   Checking for file '/dev/ttyop'                  [ Not found ]
[20:51:12]   Checking for file '/dev/ttyos'                  [ Not found ]
[20:51:12]   Checking for file '/usr/lib/.lib'               [ Not found ]
[20:51:12]   Checking for file '/usr/lib/sn/.X'              [ Not found ]
[20:51:12]   Checking for file '/usr/lib/sn/.sys'            [ Not found ]
[20:51:12]   Checking for file '/usr/lib/ld/.X'              [ Not found ]
[20:51:12]   Checking for file '/usr/man/man1/...'           [ Not found ]
[20:51:12]   Checking for file '/usr/man/man1/.../.m'        [ Not found ]
[20:51:12]   Checking for file '/usr/man/man1/.../.w'        [ Not found ]
[20:51:12]   Checking for directory '/usr/lib/sn'            [ Not found ]
[20:51:12]   Checking for directory '/usr/lib/man1/...'      [ Not found ]
[20:51:12]   Checking for directory '/dev/.haos'             [ Not found ]
[20:51:12] Sin Rootkit                                       [ Not found ]
[20:51:12]
[20:51:12] Checking for Slapper Worm...
[20:51:12]   Checking for file '/tmp/.bugtraq'               [ Not found ]
[20:51:12]   Checking for file '/tmp/.uubugtraq'             [ Not found ]
[20:51:12]   Checking for file '/tmp/.bugtraq.c'             [ Not found ]
[20:51:12]   Checking for file '/tmp/httpd'                  [ Not found ]
[20:51:12]   Checking for file '/tmp/.unlock'                [ Not found ]
[20:51:12]   Checking for file '/tmp/update'                 [ Not found ]
[20:51:12]   Checking for file '/tmp/.cinik'                 [ Not found ]
[20:51:12]   Checking for file '/tmp/.b'                     [ Not found ]
[20:51:12] Slapper Worm                                      [ Not found ]
[20:51:12]
[20:51:12] Checking for Sneakin Rootkit...
[20:51:12]   Checking for directory '/tmp/.X11-unix/.../rk'  [ Not found ]
[20:51:12] Sneakin Rootkit                                   [ Not found ]
[20:51:12]
[20:51:12] Checking for Suckit Rootkit...
[20:51:12]   Checking for file '/sbin/initsk12'              [ Not found ]
[20:51:12]   Checking for file '/sbin/initxrk'               [ Not found ]
[20:51:12]   Checking for file '/usr/bin/null'               [ Not found ]
[20:51:12]   Checking for file '/usr/share/locale/sk/.sk12/sk' [ Not found ]
[20:51:12]   Checking for file '/etc/rc.d/rc0.d/S23kmdac'    [ Not found ]
[20:51:12]   Checking for file '/etc/rc.d/rc1.d/S23kmdac'    [ Not found ]
[20:51:12]   Checking for file '/etc/rc.d/rc2.d/S23kmdac'    [ Not found ]
[20:51:12]   Checking for file '/etc/rc.d/rc3.d/S23kmdac'    [ Not found ]
[20:51:12]   Checking for file '/etc/rc.d/rc4.d/S23kmdac'    [ Not found ]
[20:51:12]   Checking for file '/etc/rc.d/rc5.d/S23kmdac'    [ Not found ]
[20:51:12]   Checking for file '/etc/rc.d/rc6.d/S23kmdac'    [ Not found ]
[20:51:12]   Checking for directory '/dev/sdhu0/tehdrakg'    [ Not found ]
[20:51:12]   Checking for directory '/etc/.MG'               [ Not found ]
[20:51:12]   Checking for directory '/usr/share/locale/sk/.sk12' [ Not found ]
[20:51:12]   Checking for directory '/usr/lib/perl5/site_perl/i386-linux/auto/TimeDate/.packlist' [ Not found ]
[20:51:12] Suckit Rootkit                                    [ Not found ]
[20:51:12]
[20:51:12] Checking for SunOS Rootkit...
[20:51:12]   Checking for file '/etc/ld.so.hash'             [ Not found ]
[20:51:12]   Checking for file '/lib/libext-2.so.7'          [ Not found ]
[20:51:12]   Checking for file '/usr/bin/ssh2d'              [ Not found ]
[20:51:12]   Checking for file '/bin/xlogin'                 [ Not found ]
[20:51:12]   Checking for file '/usr/lib/crth.o'             [ Not found ]
[20:51:12]   Checking for file '/usr/lib/crtz.o'             [ Not found ]
[20:51:12]   Checking for file '/sbin/login'                 [ Not found ]
[20:51:13]   Checking for file '/lib/security/.config/sn'    [ Not found ]
[20:51:13]   Checking for file '/lib/security/.config/lpsched' [ Not found ]
[20:51:13]   Checking for file '/dev/kmod'                   [ Not found ]
[20:51:13]   Checking for file '/dev/dos'                    [ Not found ]
[20:51:13] SunOS Rootkit                                     [ Not found ]
[20:51:13]
[20:51:13] Checking for SunOS / NSDAP Rootkit...
[20:51:13]   Checking for file '/usr/lib/vold/nsdap/.kit'    [ Not found ]
[20:51:13]   Checking for file '/usr/lib/vold/nsdap/defines' [ Not found ]
[20:51:13]   Checking for file '/usr/lib/vold/nsdap/patcher' [ Not found ]
[20:51:13]   Checking for file '/usr/lib/vold/nsdap/pg'      [ Not found ]
[20:51:13]   Checking for file '/usr/lib/vold/nsdap/cleaner' [ Not found ]
[20:51:13]   Checking for file '/usr/lib/vold/nsdap/utime'   [ Not found ]
[20:51:13]   Checking for file '/usr/lib/vold/nsdap/crypt'   [ Not found ]
[20:51:13]   Checking for file '/usr/lib/vold/nsdap/findkit' [ Not found ]
[20:51:13]   Checking for file '/usr/lib/vold/nsdap/sn2'     [ Not found ]
[20:51:13]   Checking for file '/usr/lib/vold/nsdap/sniffload' [ Not found ]
[20:51:13]   Checking for file '/usr/lib/vold/nsdap/runsniff' [ Not found ]
[20:51:13]   Checking for file '/usr/lib/lpset'              [ Not found ]
[20:51:13]   Checking for directory '/usr/lib/vold/nsdap'    [ Not found ]
[20:51:13] SunOS / NSDAP Rootkit                             [ Not found ]
[20:51:13]
[20:51:13] Checking for Superkit Rootkit...
[20:51:13]   Checking for file '/usr/man/.sman/sk'           [ Not found ]
[20:51:13] Superkit Rootkit                                  [ Not found ]
[20:51:13]
[20:51:13] Checking for TBD (Telnet BackDoor)...
[20:51:13]   Checking for file '/usr/lib/.tbd'               [ Not found ]
[20:51:13] TBD (Telnet BackDoor)                             [ Not found ]
[20:51:13]
[20:51:13] Checking for TeLeKiT Rootkit...
[20:51:13]   Checking for file '/usr/man/man3/.../TeLeKiT/bin/sniff' [ Not found ]
[20:51:13]   Checking for file '/usr/man/man3/.../TeLeKiT/bin/telnetd' [ Not found ]
[20:51:13]   Checking for file '/usr/man/man3/.../TeLeKiT/bin/teleulo' [ Not found ]
[20:51:13]   Checking for file '/usr/man/man3/.../cl'        [ Not found ]
[20:51:13]   Checking for file '/dev/ptyr'                   [ Not found ]
[20:51:13]   Checking for file '/dev/ptyp'                   [ Not found ]
[20:51:13]   Checking for file '/dev/ptyq'                   [ Not found ]
[20:51:13]   Checking for file '/dev/hda06'                  [ Not found ]
[20:51:13]   Checking for file '/usr/info/libc1.so'          [ Not found ]
[20:51:13]   Checking for directory '/usr/man/man3/...'      [ Not found ]
[20:51:13]   Checking for directory '/usr/man/man3/.../lsniff' [ Not found ]
[20:51:13]   Checking for directory '/usr/man/man3/.../TeLeKiT' [ Not found ]
[20:51:13] TeLeKiT Rootkit                                   [ Not found ]
[20:51:13]
[20:51:13] Checking for T0rn Rootkit...
[20:51:13]   Checking for file '/dev/.lib/lib/lib/t0rns'     [ Not found ]
[20:51:13]   Checking for file '/dev/.lib/lib/lib/du'        [ Not found ]
[20:51:13]   Checking for file '/dev/.lib/lib/lib/ls'        [ Not found ]
[20:51:13]   Checking for file '/dev/.lib/lib/lib/t0rnsb'    [ Not found ]
[20:51:13]   Checking for file '/dev/.lib/lib/lib/ps'        [ Not found ]
[20:51:13]   Checking for file '/dev/.lib/lib/lib/t0rnp'     [ Not found ]
[20:51:13]   Checking for file '/dev/.lib/lib/lib/find'      [ Not found ]
[20:51:13]   Checking for file '/dev/.lib/lib/lib/ifconfig'  [ Not found ]
[20:51:13]   Checking for file '/dev/.lib/lib/lib/pg'        [ Not found ]
[20:51:13]   Checking for file '/dev/.lib/lib/lib/ssh.tgz'   [ Not found ]
[20:51:14]   Checking for file '/dev/.lib/lib/lib/top'       [ Not found ]
[20:51:14]   Checking for file '/dev/.lib/lib/lib/sz'        [ Not found ]
[20:51:14]   Checking for file '/dev/.lib/lib/lib/login'     [ Not found ]
[20:51:14]   Checking for file '/dev/.lib/lib/lib/in.fingerd' [ Not found ]
[20:51:14]   Checking for file '/dev/.lib/lib/lib/1i0n.sh'   [ Not found ]
[20:51:14]   Checking for file '/dev/.lib/lib/lib/pstree'    [ Not found ]
[20:51:14]   Checking for file '/dev/.lib/lib/lib/in.telnetd' [ Not found ]
[20:51:14]   Checking for file '/dev/.lib/lib/lib/mjy'       [ Not found ]
[20:51:14]   Checking for file '/dev/.lib/lib/lib/sush'      [ Not found ]
[20:51:14]   Checking for file '/dev/.lib/lib/lib/tfn'       [ Not found ]
[20:51:14]   Checking for file '/dev/.lib/lib/lib/name'      [ Not found ]
[20:51:14]   Checking for file '/dev/.lib/lib/lib/getip.sh'  [ Not found ]
[20:51:14]   Checking for file '/usr/info/.torn/sh*'         [ Not found ]
[20:51:14]   Checking for file '/usr/src/.****/.1addr'       [ Not found ]
[20:51:14]   Checking for file '/usr/src/.****/.1file'       [ Not found ]
[20:51:14]   Checking for file '/usr/src/.****/.1proc'       [ Not found ]
[20:51:14]   Checking for file '/usr/src/.****/.1logz'       [ Not found ]
[20:51:14]   Checking for file '/usr/info/.t0rn'             [ Not found ]
[20:51:14]   Checking for directory '/dev/.lib'              [ Not found ]
[20:51:14]   Checking for directory '/dev/.lib/lib'          [ Not found ]
[20:51:14]   Checking for directory '/dev/.lib/lib/lib'      [ Not found ]
[20:51:14]   Checking for directory '/dev/.lib/lib/lib/dev'  [ Not found ]
[20:51:14]   Checking for directory '/dev/.lib/lib/scan'     [ Not found ]
[20:51:14]   Checking for directory '/usr/src/.****'         [ Not found ]
[20:51:14]   Checking for directory '/usr/man/man1/man1'     [ Not found ]
[20:51:14]   Checking for directory '/usr/man/man1/man1/lib' [ Not found ]
[20:51:14]   Checking for directory '/usr/man/man1/man1/lib/.lib' [ Not found ]
[20:51:14]   Checking for directory '/usr/man/man1/man1/lib/.lib/.backup' [ Not found ]
[20:51:14] T0rn Rootkit                                      [ Not found ]
[20:51:14]
[20:51:14] Checking for Trojanit Kit...
[20:51:14]   Checking for file '/bin/.ls'                    [ Not found ]
[20:51:14]   Checking for file '/bin/.ps'                    [ Not found ]
[20:51:14]   Checking for file '/bin/.netstat'               [ Not found ]
[20:51:14]   Checking for file '/usr/bin/.nop'               [ Not found ]
[20:51:14]   Checking for file '/usr/bin/.who'               [ Not found ]
[20:51:14] Trojanit Kit                                      [ Not found ]
[20:51:14]
[20:51:14] Checking for Tuxtendo Rootkit...
[20:51:14]   Checking for file '/dev/tux/.addr'              [ Not found ]
[20:51:14]   Checking for file '/dev/tux/.cron'              [ Not found ]
[20:51:14]   Checking for file '/dev/tux/.file'              [ Not found ]
[20:51:14]   Checking for file '/dev/tux/.log'               [ Not found ]
[20:51:14]   Checking for file '/dev/tux/.proc'              [ Not found ]
[20:51:14]   Checking for file '/dev/tux/backup/crontab'     [ Not found ]
[20:51:14]   Checking for file '/dev/tux/backup/df'          [ Not found ]
[20:51:14]   Checking for file '/dev/tux/backup/dir'         [ Not found ]
[20:51:14]   Checking for file '/dev/tux/backup/find'        [ Not found ]
[20:51:14]   Checking for file '/dev/tux/backup/ifconfig'    [ Not found ]
[20:51:14]   Checking for file '/dev/tux/backup/locate'      [ Not found ]
[20:51:14]   Checking for file '/dev/tux/backup/netstat'     [ Not found ]
[20:51:14]   Checking for file '/dev/tux/backup/ps'          [ Not found ]
[20:51:14]   Checking for file '/dev/tux/backup/pstree'      [ Not found ]
[20:51:15]   Checking for file '/dev/tux/backup/syslogd'     [ Not found ]
[20:51:15]   Checking for file '/dev/tux/backup/tcpd'        [ Not found ]
[20:51:15]   Checking for file '/dev/tux/backup/top'         [ Not found ]
[20:51:15]   Checking for file '/dev/tux/backup/updatedb'    [ Not found ]
[20:51:15]   Checking for file '/dev/tux/backup/vdir'        [ Not found ]
[20:51:15]   Checking for directory '/dev/tux'               [ Not found ]
[20:51:15]   Checking for directory '/dev/tux/ssh2'          [ Not found ]
[20:51:15]   Checking for directory '/dev/tux/backup'        [ Not found ]
[20:51:15] Tuxtendo Rootkit                                  [ Not found ]
[20:51:15]
[20:51:15] Checking for URK Rootkit...
[20:51:15]   Checking for file '/usr/man/man1/xxxxxxbin/find' [ Not found ]
[20:51:15]   Checking for file '/usr/man/man1/xxxxxxbin/du'  [ Not found ]
[20:51:15]   Checking for file '/usr/man/man1/xxxxxxbin/ps'  [ Not found ]
[20:51:15]   Checking for file '/tmp/conf.inf'               [ Not found ]
[20:51:15]   Checking for directory '/usr/man/man1/xxxxxxbin' [ Not found ]
[20:51:15] URK Rootkit                                       [ Not found ]
[20:51:15]
[20:51:15] Checking for VcKit Rootkit...
[20:51:15]   Checking for directory '/usr/include/linux/modules/lib.so' [ Not found ]
[20:51:15]   Checking for directory '/usr/include/linux/modules/lib.so/bin' [ Not found ]
[20:51:15] VcKit Rootkit                                     [ Not found ]
[20:51:15]
[20:51:15] Checking for Volc Rootkit...
[20:51:15]   Checking for directory '/var/spool/.recent'     [ Not found ]
[20:51:15]   Checking for directory '/var/spool/.recent/.files' [ Not found ]
[20:51:15]   Checking for directory '/usr/lib/volc'          [ Not found ]
[20:51:15]   Checking for directory '/usr/lib/volc/backup'   [ Not found ]
[20:51:15] Volc Rootkit                                      [ Not found ]
[20:51:15]
[20:51:15] Checking for X-Org SunOS Rootkit...
[20:51:15]   Checking for file '/usr/lib/libX.a/bin/tmpfl'   [ Not found ]
[20:51:15]   Checking for file '/usr/lib/libX.a/bin/rps'     [ Not found ]
[20:51:15]   Checking for file '/usr/bin/srload'             [ Not found ]
[20:51:15]   Checking for file '/usr/lib/libX.a/bin/sparcv7/rps' [ Not found ]
[20:51:15]   Checking for file '/usr/sbin/modcheck'          [ Not found ]
[20:51:15]   Checking for directory '/usr/lib/libX.a'        [ Not found ]
[20:51:15]   Checking for directory '/usr/lib/libX.a/bin'    [ Not found ]
[20:51:15]   Checking for directory '/usr/lib/libX.a/bin/sparcv7' [ Not found ]
[20:51:15]   Checking for directory '/usr/share/man...'      [ Not found ]
[20:51:15] X-Org SunOS Rootkit                               [ Not found ]
[20:51:15]
[20:51:15] Checking for zaRwT.KiT Rootkit...
[20:51:15]   Checking for file '/dev/rd/s/sendmeil'          [ Not found ]
[20:51:15]   Checking for file '/dev/ttyf'                   [ Not found ]
[20:51:15]   Checking for file '/dev/ttyp'                   [ Not found ]
[20:51:15]   Checking for file '/dev/ttyn'                   [ Not found ]
[20:51:15]   Checking for file '/rk/tulz'                    [ Not found ]
[20:51:15]   Checking for directory '/rk'                    [ Not found ]
[20:51:15]   Checking for directory '/dev/rd/s'              [ Not found ]
[20:51:15] zaRwT.KiT Rootkit                                 [ Not found ]
[20:51:15]
[20:51:15] Performing additional rootkit checks
[20:51:15] Info: Starting test name 'additional_rkts'
[20:51:15]
[20:51:15]   Performing Suckit Rookit additional checks
[20:51:15]     Checking /sbin/init link count                [ OK ]
[20:51:16]     Checking for hidden file extensions           [ None found ]
[20:51:16]     Running skdet command                         [ Skipped ]
[20:51:16] Info: Unable to find the 'skdet' command
[20:51:16]   Suckit Rookit additional checks                 [ OK ]
[20:51:16]
[20:51:16]   Performing check of possible rootkit files and directories
[20:51:16] Info: Starting test name 'possible_rkt_files'
[20:51:16]     Checking for file '/dev/sdr0'                 [ Not found ]
[20:51:16]     Checking for file '/tmp/.syshackfile'         [ Not found ]
[20:51:16]     Checking for file '/tmp/.bash_history'        [ Not found ]
[20:51:16]     Checking for file '/usr/info/.clib'           [ Not found ]
[20:51:16]     Checking for file '/usr/sbin/tcp.log'         [ Not found ]
[20:51:16]     Checking for file '/usr/bin/take/pid'         [ Not found ]
[20:51:16]     Checking for file '/sbin/create'              [ Not found ]
[20:51:16]     Checking for file '/dev/ttypz'                [ Not found ]
[20:51:16]     Checking for directory '/usr/bin/take'        [ Not found ]
[20:51:16]     Checking for directory '/usr/src/.lib'        [ Not found ]
[20:51:16]     Checking for directory '/usr/share/man/man1/.1c' [ Not found ]
[20:51:16]     Checking for directory '/lib/lblip.tk'        [ Not found ]
[20:51:16]     Checking for directory '/usr/sbin/...'        [ Not found ]
[20:51:16]     Checking for directory '/usr/share/.gun'      [ Not found ]
[20:51:16]   Checking for possible rootkit files and directories [ None found ]
[20:51:16]
[20:51:16]   Performing check for possible rootkit strings
[20:51:16] Info: Starting test name 'possible_rkt_strings'
[20:51:16] Info: Found local startup file: /etc/rc.local
[20:51:16]     Checking for string '/dev/proc/fuckit'        [ Not found ]
[20:51:16]     Checking for string '****'                    [ Not found ]
[20:51:16]     Checking for string 'backdoor'                [ Not found ]
[20:51:16]     Checking for string 'vt200'                   [ Not found ]
[20:51:16]     Checking for string '/usr/bin/xstat'          [ Not found ]
[20:51:16]     Checking for string '/bin/envpc'              [ Not found ]
[20:51:16]     Checking for string 'L4m3r0x'                 [ Not found ]
[20:51:16]     Checking for string '/usr/lib/.tbd'           [ Not found ]
[20:51:16]     Checking for string '/dev/ptyxx/.file'        [ Not found ]
[20:51:16]     Checking for string '/dev/sgk'                [ Not found ]
[20:51:16]     Checking for string '/var/lock/subsys/...datafile...' [ Not found ]
[20:51:16]     Checking for string '/usr/lib/.tbd'           [ Not found ]
[20:51:17]     Checking for string '/dev/proc/fuckit'        [ Not found ]
[20:51:17]     Checking for string '/lib/.sso'               [ Not found ]
[20:51:17]     Checking for string '/var/lock/subsys/...datafile...' [ Not found ]
[20:51:17]     Checking for string '/dev/caca'               [ Not found ]
[20:51:17]     Checking for string '/dev/ttyoa'              [ Not found ]
[20:51:17]     Checking for string 'syg'                     [ Not found ]
[20:51:17]     Checking for string '/dev/pts/01'             [ Not found ]
[20:51:17]     Checking for string 'tw33dl3'                 [ Not found ]
[20:51:17]     Checking for string 'psniff'                  [ Not found ]
[20:51:17]     Checking for string '/var/lock/subsys/...datafile...' [ Not found ]
[20:51:17]     Checking for string 'promiscuous'             [ Not found ]
[20:51:17]     Checking for string '/usr/lib/.tbd'           [ Not found ]
[20:51:17]     Checking for string '/dev/xdta'               [ Not found ]
[20:51:17]     Checking for string '/usr/lib/.tbd'           [ Not found ]
[20:51:17]     Checking for string 'in.inetd'                [ Not found ]
[20:51:17]     Checking for string '#<HIDE_.*>'              [ Not found ]
[20:51:17]     Checking for string 'bin/xchk'                [ Not found ]
[20:51:17]     Checking for string 'bin/xsf'                 [ Not found ]
[20:51:17]   Checking for possible rootkit strings           [ None found ]
[20:51:17]
[20:51:17] Performing malware checks
[20:51:17] Info: Starting test name 'malware'
[20:51:17]
[20:51:17] Info: Test 'deleted_files' disabled at users request.
[20:51:17] Info: Starting test name 'running_procs'
[20:51:17]   Checking running processes for suspicious files [ None found ]
[20:51:17]
[20:51:17] Info: Test 'hidden_procs' disabled at users request.
[20:51:17]
[20:51:17] Info: Test 'suspscan' disabled at users request.
[20:51:17]
[20:51:17]   Performing check for login backdoors
[20:51:17] Info: Starting test name 'other_malware'
[20:51:17]     Checking for '/bin/.login'                    [ Not found ]
[20:51:17]     Checking for '/sbin/.login'                   [ Not found ]
[20:51:17]   Checking for login backdoors                    [ None found ]
[20:51:17]
[20:51:17]   Performing check for suspicious directories
[20:51:17]     Checking for directory '/usr/X11R6/bin/.,/copy' [ Not found ]
[20:51:17]     Checking for directory '/dev/rd/cdb'          [ Not found ]
[20:51:18]   Checking for suspicious directories             [ None found ]
[20:51:18]
[20:51:18]   Checking for software intrusions                [ Skipped ]
[20:51:18] Info: Check skipped - tripwire not installed
[20:51:18]
[20:51:18]   Performing check for sniffer log files
[20:51:18]     Checking for file '/usr/lib/libice.log'       [ Not found ]
[20:51:18]   Checking for sniffer log files                  [ None found ]
[20:51:18]
[20:51:18] Performing trojan specific checks
[20:51:18] Info: Starting test name 'trojans'
[20:51:18] Info: Using inetd configuration file '/etc/inetd.conf'
[20:51:18]   Checking for enabled inetd services             [ Warning ]
[20:51:18] Warning: Found enabled inetd service: telnet
[20:51:18]
[20:51:18]   Performing check for enabled xinetd services
[20:51:18]   Checking for enabled xinetd services            [ Skipped ]
[20:51:18] Info: Check skipped - file '/etc/xinetd.conf' does not exist.
[20:51:18] Info: Apache backdoor check skipped: Apache modules and configuration directories not found.
[20:51:18]
[20:51:18] Performing Linux specific checks
[20:51:18] Info: Starting test name 'os_specific'
[20:51:18]   Checking kernel module commands                 [ OK ]
[20:51:18] Info: Using modules pathname of '/lib/modules/2.6.28-11-generic'
[20:51:18]   Checking kernel module names                    [ OK ]
[20:51:42]
[20:51:42] Checking the network...
[20:51:42] Info: Starting test name 'network'
[20:51:42] Info: Starting test name 'ports'
[20:51:42]
[20:51:42] Performing check for backdoor ports
[20:51:42]   Checking for TCP port 1524                      [ Not found ]
[20:51:42]   Checking for TCP port 1984                      [ Not found ]
[20:51:42]   Checking for UDP port 2001                      [ Not found ]
[20:51:42]   Checking for TCP port 2006                      [ Not found ]
[20:51:42]   Checking for TCP port 2128                      [ Not found ]
[20:51:42]   Checking for TCP port 6666                      [ Not found ]
[20:51:42]   Checking for TCP port 6667                      [ Not found ]
[20:51:42]   Checking for TCP port 6668                      [ Not found ]
[20:51:42]   Checking for TCP port 6669                      [ Not found ]
[20:51:42]   Checking for TCP port 7000                      [ Not found ]
[20:51:42]   Checking for TCP port 13000                     [ Not found ]
[20:51:42]   Checking for TCP port 14856                     [ Not found ]
[20:51:42]   Checking for TCP port 25000                     [ Not found ]
[20:51:42]   Checking for TCP port 29812                     [ Not found ]
[20:51:42]   Checking for TCP port 31337                     [ Not found ]
[20:51:42]   Checking for TCP port 33369                     [ Not found ]
[20:51:43]   Checking for TCP port 47107                     [ Not found ]
[20:51:43]   Checking for TCP port 47018                     [ Not found ]
[20:51:43]   Checking for TCP port 60922                     [ Not found ]
[20:51:43]   Checking for TCP port 62883                     [ Not found ]
[20:51:43]   Checking for TCP port 65535                     [ Not found ]
[20:51:43]
[20:51:43] Performing checks on the network interfaces
[20:51:43] Info: Starting test name 'promisc'
[20:51:43]   Checking for promiscuous interfaces             [ None found ]
[20:51:43]
[20:51:43] Info: Test 'packet_cap_apps' disabled at users request.
[20:51:58]
[20:51:58] Checking the local host...
[20:51:58] Info: Starting test name 'local_host'
[20:51:58]
[20:51:58] Performing system boot checks
[20:51:59] Info: Starting test name 'startup_files'
[20:51:59]   Checking for local host name                    [ Found ]
[20:51:59] Info: Starting test name 'startup_malware'
[20:51:59] Info: Found local startup file: /etc/rc.local
[20:51:59]   Checking for local startup files                [ Found ]
[20:51:59]   Checking local startup files for malware        [ None found ]
[20:51:59] Info: Found system startup directory: /etc/init.d
[20:51:59]   Checking system startup files for malware       [ None found ]
[20:51:59]
[20:51:59] Performing group and account checks
[20:51:59] Info: Starting test name 'group_accounts'
[20:51:59]   Checking for passwd file                        [ Found ]
[20:51:59] Info: Found password file: /etc/passwd
[20:51:59]   Checking for root equivalent (UID 0) accounts   [ None found ]
[20:52:00] Info: Found shadow file: /etc/shadow
[20:52:00]   Checking for passwordless accounts              [ None found ]
[20:52:00] Info: Starting test name 'passwd_changes'
[20:52:00]   Checking for passwd file changes                [ None found ]
[20:52:00] Info: Starting test name 'group_changes'
[20:52:00]   Checking for group file changes                 [ None found ]
[20:52:00]   Checking root account shell history files       [ OK ]
[20:52:00]
[20:52:00] Performing system configuration file checks
[20:52:00] Info: Starting test name 'system_configs'
[20:52:00]   Checking for SSH configuration file             [ Not found ]
[20:52:00]   Checking for running syslog daemon              [ Found ]
[20:52:00]   Checking for syslog configuration file          [ Found ]
[20:52:00] Info: Found syslog configuration file: /etc/syslog.conf
[20:52:00]   Checking if syslog remote logging is allowed    [ Not allowed ]
[20:52:00]
[20:52:00] Performing filesystem checks
[20:52:00] Info: Starting test name 'filesystem'
[20:52:00] Info: SCAN_MODE_DEV set to 'THOROUGH'
[20:52:00]   Checking /dev for suspicious file types         [ None found ]
[20:52:00]   Checking for hidden files and directories       [ Warning ]
[20:52:00] Warning: Hidden file found: /etc/.sudoers.swn: Vim swap file, version 7.2
[20:52:00] Warning: Hidden file found: /etc/.sudoers.swo: Vim swap file, version 7.2
[20:52:00] Warning: Hidden file found: /etc/.sudoers.swp: Vim swap file, version 7.2
[20:52:50]
[20:52:50] Checking application versions...
[20:52:50] Info: Starting test name 'apps'
[20:52:50] Info: Application 'exim' not found.
[20:52:50]   Checking version of GnuPG                       [ Warning ]
[20:52:50] Warning: Application 'gpg', version '1.4.9', is out of date, and possibly a security risk.
[20:52:50] Info: Application 'httpd' not found.
[20:52:50] Info: Application 'named' not found.
[20:52:50]   Checking version of OpenSSL                     [ Warning ]
[20:52:50] Warning: Application 'openssl', version '0.9.8g', is out of date, and possibly a security risk.
[20:52:50] Info: Application 'php' not found.
[20:52:51] Info: Application 'procmail' not found.
[20:52:51] Info: Application 'proftpd' not found.
[20:52:51] Info: Application 'sshd' not found.
[20:52:51] Info: Applications checked: 2 out of 9
[20:52:51]
[20:52:51] System checks summary
[20:52:51] =====================
[20:52:51]
[20:52:51] File properties checks...
[20:52:51] Files checked: 124
[20:52:51] Suspect files: 2
[20:52:51]
[20:52:51] Rootkit checks...
[20:52:51] Rootkits checked : 109
[20:52:51] Possible rootkits: 0
[20:52:51]
[20:52:51] Applications checks...
[20:52:51] Applications checked: 2
[20:52:51] Suspect applications: 2
[20:52:51]
[20:52:51] The system checks took: 2 minutes and 35 seconds
[20:52:51]
[20:52:51] Info: End date is Sat Mar 13 20:52:51 IST 2010
```

---

### Post by gnupipe on 2010-03-13
Looks safe. Have you noticed anything suspicious?

---

### Post by karthick87 on 2010-03-13
My scan reports shows [COLOR=Red]warning[/COLOR] in some fields what it mean?

---

### Post by shabs on 2010-03-13
I'm no security expert but it looks clean. The warnings are about the inetd, a daemon that listens on particular ports to provide services, /bin/su provides the root shell to the user, the other warnings are about the OpenSSL and GnuPG. So nothing to worry about. You can upgrade OpenSSL and GnuPG and that would fix those warnings.

Shabs.

---

### Post by karthick87 on 2010-03-13
Fine :) Thanks a lot..

---

