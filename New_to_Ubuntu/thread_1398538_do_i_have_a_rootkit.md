---
title: "do i have a rootkit ?"
date: 2010-02-04
forum: New to Ubuntu
---

### Post by skullcandy23 on 2010-02-04
N/a

---

### Post by Rex Bouwense on 2010-02-04
What is your question?

---

### Post by cpplinux on 2010-02-04
Warning doesn't mean you have rootkit. You should check the log file to see why there are warnings.

---

### Post by samantha_ on 2010-02-04
> **skullcandy23 said:**
> [ Rootkit Hunter version 1.3.4 ]

```
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
    /bin/kill                                                [ Warning ]
    /bin/less                                                [ OK ]
    /bin/login                                               [ OK ]
    /bin/ls                                                  [ OK ]
    /bin/lsmod                                               [ Warning ]
    /bin/mktemp                                              [ OK ]
    /bin/more                                                [ OK ]
    /bin/mount                                               [ OK ]
    /bin/mv                                                  [ OK ]
    /bin/netstat                                             [ OK ]
    /bin/ps                                                  [ Warning ]
    /bin/pwd                                                 [ OK ]
    /bin/readlink                                            [ OK ]
    /bin/sed                                                 [ OK ]
    /bin/sh                                                  [ OK ]
    /bin/su                                                  [ OK ]
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
    /usr/bin/mail                                            [ OK ]
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
    /usr/bin/top                                             [ Warning ]
    /usr/bin/touch                                           [ OK ]
    /usr/bin/tr                                              [ OK ]
    /usr/bin/uniq                                            [ OK ]
    /usr/bin/users                                           [ OK ]
    /usr/bin/vmstat                                          [ Warning ]
    /usr/bin/w                                               [ Warning ]
    /usr/bin/watch                                           [ Warning ]
    /usr/bin/wc                                              [ OK ]
    /usr/bin/wget                                            [ OK ]
    /usr/bin/whatis                                          [ OK ]
    /usr/bin/whereis                                         [ OK ]
    /usr/bin/which                                           [ OK ]
    /usr/bin/who                                             [ OK ]
    /usr/bin/whoami                                          [ OK ]
    /usr/bin/mawk                                            [ OK ]
    /usr/bin/lwp-request                                     [ OK ]
    /usr/bin/bsd-mailx                                       [ OK ]
    /usr/bin/w.procps                                        [ Warning ]
    /sbin/depmod                                             [ Warning ]
    /sbin/ifconfig                                           [ OK ]
    /sbin/ifdown                                             [ Warning ]
    /sbin/ifup                                               [ Warning ]
    /sbin/init                                               [ OK ]
    /sbin/insmod                                             [ Warning ]
    /sbin/ip                                                 [ OK ]
    /sbin/lsmod                                              [ Warning ]
    /sbin/modinfo                                            [ Warning ]
    /sbin/modprobe                                           [ Warning ]
    /sbin/rmmod                                              [ Warning ]
    /sbin/runlevel                                           [ OK ]
    /sbin/sulogin                                            [ OK ]
    /sbin/sysctl                                             [ Warning ]
    /sbin/syslogd                                            [ Warning ]
    /usr/sbin/adduser                                        [ OK ]
    /usr/sbin/chroot                                         [ OK ]
    /usr/sbin/cron                                           [ Warning ]
    /usr/sbin/groupadd                                       [ OK ]
    /usr/sbin/groupdel                                       [ OK ]
    /usr/sbin/groupmod                                       [ OK ]
    /usr/sbin/grpck                                          [ OK ]
    /usr/sbin/nologin                                        [ OK ]
    /usr/sbin/pwck                                           [ OK ]
    /usr/sbin/rsyslogd                                       [ Warning ]
    /usr/sbin/tcpd                                           [ OK ]
    /usr/sbin/unhide                                         [ OK ]
    /usr/sbin/useradd                                        [ OK ]
    /usr/sbin/userdel                                        [ OK ]
    /usr/sbin/usermod                                        [ OK ]
    /usr/sbin/vipw                                           [ OK ]
    /usr/sbin/unhide-linux26                                 [ OK ]

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
    IntoXonia-NG Rootkit                                     [ Not found ]
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
    Phalanx2 Rootkit                                         [ Not found ]
    Phalanx2 Rootkit (extended tests)                        [ Not found ]
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
    Vampire Rootkit                                          [ Not found ]
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
    Checking for enabled inetd services                      [ OK ]

  Performing Linux specific checks
    Checking loaded kernel modules                           [ OK ]
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
    Checking for system startup files                        [ Found ]
    Checking system startup files for malware                [ None found ]

  Performing group and account checks
    Checking for passwd file                                 [ Found ]
    Checking for root equivalent (UID 0) accounts            [ None found ]
    Checking for passwordless accounts                       [ None found ]
    Checking for passwd file changes                         [ None found ]
    Checking for group file changes                          [ None found ]
    Checking root account shell history files                [ None found ]

  Performing system configuration file checks
    Checking for SSH configuration file                      [ Not found ]
    Checking for running syslog daemon                       [ Found ]
    Checking for syslog configuration file                   [ Found ]
    Checking if syslog remote logging is allowed             [ Not allowed ]

  Performing filesystem checks
    Checking /dev for suspicious file types                  [ Warning ]
    Checking for hidden files and directories                [ Warning ]

[Press <ENTER> to continue]


Checking application versions...

    Checking version of Exim MTA                             [ Warning ]
    Checking version of GnuPG                                [ Warning ]
    Checking version of OpenSSL                              [ Warning ]


System checks summary
=====================

File properties checks...
    Files checked: 128
    Suspect files: 20

Rootkit checks...
    Rootkits checked : 111
    Possible rootkits: 0

Applications checks...
    Applications checked: 3
    Suspect applications: 3

The system checks took: 8 minutes and 45 seconds

All results have been written to the logfile (/var/log/rkhunter.log)

One or more warnings have been found while checking the system.
Please check the log file (/var/log/rkhunter.log)
bolded them cause i have nothing better to do...
```

---

### Post by ghostborg on 2010-02-04
Try contacting the Author?
[http://www.rootkit.nl/contact/]("http://www.rootkit.nl/contact/")

Try posting your question to Robbie Ferguson of Category5.tv, his show usually answers your emailed questions on Tuesdays at 7pm eastern usa time.

I think AVG has a rootkit tester, might have to boot a Windows cd.

---

### Post by almufadado on 2010-02-04
In the section "Checking for rootkits... ", if there was a message [found] then you certainly had a root kit. 
 
Note the app has a profiling preset, that check for the root kit signature. 

The other warning, can about existence/non-existence of a particular directory or file and binaries (that must be secured).
Also as it does profiling,  it must be updated so it matches new installed/upgraded versions of the files that are checked.

Another section is :
"Checking the network...  
Performing check for backdoor ports"

If an open port of a particular profile is detected, then this also could mean trouble. This ports may and can be used by other "good" apps, thou.

---

### Post by danwosere2007 on 2010-02-04
> **Rex Bouwense said:**
> What is your question?

"What exactly were you asking again?"

Comedy Gold! ;)

---

### Post by panicy on 2010-02-04
if you haven't looked through /var/log/rkhunter.log then post it we can look to see why the warnings are popping up.  Usually in my experience its ok...

---

