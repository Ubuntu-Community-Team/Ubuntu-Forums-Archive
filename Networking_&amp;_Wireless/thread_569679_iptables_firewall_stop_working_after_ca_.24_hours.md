---
title: "iptables firewall stop working after ca .24 hours"
date: 2007-10-07
forum: Networking &amp; Wireless
---

### Post by sonicx on 2007-10-07
hello,
on an old dedicated p3 500 i installed a fresh ubuntu server (6.10), to serve me as gateway/firewall between a dsl modem and a small lan. all works fine - for about a day, after which the gateway  is still connected, but wont forward my lan"s packets anymore. if i run my firewall script again, it works again - for another day.  here is my firewall skript, with eth0>ppp0>modem and eth1>lan(192.168.0.0/24):
```

#!/bin/bash
echo "Flushing current firewall..."
iptables -F
iptables -X
iptables -F -t nat
iptables -X -t nat
echo "Setting up firewall..."
iptables -t nat -P PREROUTING ACCEPT
iptables -t nat -P POSTROUTING ACCEPT
iptables -t nat -P OUTPUT ACCEPT
echo "NAT Tables set."

iptables -t nat -A PREROUTING -i ppp0 -p tcp -m tcp --dport 80 -j DNAT 
--to-destination 192.168.0.2
iptables -t nat -A PREROUTING -i ppp0 -p tcp -m tcp --dport 22 -j DNAT 
--to-destination 192.168.0.2:22
iptables -t nat -A PREROUTING -i ppp0 -p tcp -m tcp --dport 6969 -j DNAT 
--to-destination 192.168.0.101
iptables -t nat -A PREROUTING -i ppp0 -p tcp -m tcp --dport 9696 -j DNAT 
--to-destination 192.168.0.101
iptables -t nat -A PREROUTING -i ppp0 -p udp --dport 6969 -j DNAT 
--to-destination 192.168.0.101
iptables -t nat -A PREROUTING -i ppp0 -p tcp -m tcp --dport 6999 -j DNAT 
--to-destination 192.168.0.101
iptables -t nat -A PREROUTING -i ppp0 -p udp --dport 6999 -j DNAT 
--to-destination 192.168.0.101
iptables -t nat -A PREROUTING -i ppp0 -p udp --dport 9696 -j DNAT 
--to-destination 192.168.0.101
iptables -t nat -A PREROUTING -i ppp0 -p udp --dport 4444 -j DNAT 
--to-destination 192.168.0.2
echo "PREROUTING set."
iptables -t nat -A POSTROUTING -s 192.168.0.0/255.255.255.0 -o ppp0 -j 
MASQUERADE
echo "POSTROUTING set."

iptables -P INPUT DROP
iptables -P FORWARD DROP
iptables -P OUTPUT ACCEPT
echo "Filter Tables set."

iptables -N LOGDROP
iptables -N OK
iptables -N OPEN
iptables -N INTERFACES
iptables -N PRE
iptables -N POST
iptables -N FW_PRE
iptables -N FW_POST
iptables -N FW_STANDARD
iptables -N FW_OPEN
iptables -N FW_INTERFACES
echo "Chains created set."

iptables -A FW_OPEN -d 192.168.0.2 -p tcp --dport 80 -j ACCEPT
iptables -A FW_OPEN -d 192.168.0.2 -p tcp --dport 22 -j ACCEPT
iptables -A FW_OPEN -d 192.168.0.101 -p tcp --dport 6969 -j ACCEPT
iptables -A FW_OPEN -d 192.168.0.101 -p tcp --dport 9696 -j ACCEPT
iptables -A FW_OPEN -d 192.168.0.101 -p udp --dport 6969 -j ACCEPT
iptables -A FW_OPEN -d 192.168.0.101 -p tcp --dport 6999 -j ACCEPT
iptables -A FW_OPEN -d 192.168.0.101 -p udp --dport 6999 -j ACCEPT
iptables -A FW_OPEN -d 192.168.0.101 -p udp --dport 9696 -j ACCEPT
iptables -A FW_OPEN -d 192.168.0.101 -p udp --dport 4444 -j ACCEPT
iptables -A FW_INTERFACES -i eth1 -j OK
iptables -A FW_PRE -o ppp0 -p tcp -m tcp --tcp-flags SYN,RST SYN -m 
tcpmss --mss 1400:1536 -j TCPMSS --clamp-mss-to-pmtu
iptables -A FW_PRE -m state --state RELATED,ESTABLISHED -j ACCEPT
iptables -A FW_POST -j REJECT --reject-with icmp-host-unreachable
iptables -A FORWARD -j FW_INTERFACES
iptables -A FORWARD -j FW_PRE
iptables -A FORWARD -j FW_OPEN
iptables -A FORWARD -j FW_POST
echo "FORWARD Table set."

iptables -A INTERFACES -i eth1 -j OK
echo "INTERFACES set up..."
iptables -A PRE -p icmp -j ACCEPT
iptables -A PRE -m state --state RELATED,ESTABLISHED -j ACCEPT
echo "PRE set up..."
iptables -A POST -p tcp -j REJECT --reject-with tcp-reset
iptables -A POST -p udp -j REJECT --reject-with icmp-port-unreachable
echo "POST set up..."
iptables -A OPEN -p tcp -i ppp0 --dport 80 -j OK
iptables -A OPEN -p udp -i ppp0 --dport 6969 -j OK
iptables -A OPEN -p udp -i ppp0 --dport 9696 -j OK
iptables -A OPEN -p udp -i ppp0 --dport 4444 -j OK
echo "OPEN set up..."
iptables -A INPUT -j INTERFACES
iptables -A INPUT -j PRE
iptables -A INPUT -j OPEN
iptables -A INPUT -j POST
echo "INPUT set up..."


iptables -A OK -j ACCEPT
iptables -A LOGDROP -j LOG
iptables -A LOGDROP -j DROP
echo "Standard chains set up..."

echo "Saving new firewall..."
iptables-save > /etc/default/iptables

echo "Done."

```
i cant see any reason why this in itself should be the reason - no time limits in there.  thought it could be a cron job, being daily and all. 
```

find /etc/cron.*

/etc/cron.d
/etc/cron.d/.placeholder
/etc/cron.daily
/etc/cron.daily/find
/etc/cron.daily/aptitude
/etc/cron.daily/sysklogd
/etc/cron.daily/.placeholder
/etc/cron.daily/standard
/etc/cron.daily/apt
/etc/cron.daily/logrotate
/etc/cron.daily/man-db
/etc/cron.daily/ntp-server
/etc/cron.daily/bsdmainutils
/etc/cron.hourly
/etc/cron.hourly/.placeholder
/etc/cron.monthly
/etc/cron.monthly/standard
/etc/cron.monthly/.placeholder
/etc/cron.weekly
/etc/cron.weekly/popularity-contest
/etc/cron.weekly/sysklogd
/etc/cron.weekly/man-db
/etc/cron.weekly/ntp-server
/etc/cron.weekly/.placeholder

```
are the jobs there are.a 
```
for FILE in `find /etc/cron.*`;do cat $FILE|grep iptables;done;
```
however gives me no cronjobs fiddling with iptables.
guess it has to be some software that is installed - but i have no clue what that could be.
any hints are greatly welcome.
jonas

here the list of installed software:
```

dpkg -l
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  adduser        3.80ubuntu2    Add and remove users and groups
ii  alsa-base      1.0.10-4ubuntu ALSA driver configuration files
ii  alsa-utils     1.0.10-1ubuntu ALSA utilities
ii  apt            0.6.43.3ubuntu Advanced front-end for dpkg
ii  apt-utils      0.6.43.3ubuntu APT utility programs
ii  aptitude       0.4.0-5ubuntu3 terminal-based apt frontend
ii  at             3.1.9ubuntu3   Delayed job execution and batch processing
ii  base-files     3.1.9ubuntu7.1 Debian base system miscellaneous files
ii  base-passwd    3.5.11         Debian base system master password and group
ii  bash           3.1-2ubuntu10  The GNU Bourne Again SHell
ii  belocs-locales 2.3.5-5ubuntu7 tools for compiling locale data files
ii  bind9-host     9.3.2-2ubuntu1 Version of 'host' bundled with BIND 9.X
ii  binutils       2.16.1cvs20060 The GNU assembler, linker and binary utiliti
ii  bsdmainutils   6.1.2ubuntu1   collection of more utilities from FreeBSD
ii  bsdutils       2.12r-4ubuntu6 Basic utilities from 4.4BSD-Lite
ii  busybox-initra 1.01-4ubuntu3  Standalone shell setup for initramfs
ii  bzip2          1.0.3-0ubuntu2 high-quality block-sorting file compressor -
ii  console-common 0.7.55         Basic infrastructure for text console config
ii  console-data   2002.12.04dbs- Keymaps, fonts, charset maps, fallback table
ii  console-tools  0.2.3dbs-60ubu Linux console and font utilities
ii  coreutils      5.93-5ubuntu4  The GNU core utilities
ii  cpio           2.6-10ubuntu0. GNU cpio -- a program to manage archives of
ii  cpp            4.0.3-1        The GNU C preprocessor (cpp)
ii  cpp-4.0        4.0.3-1ubuntu5 The GNU C preprocessor
ii  cron           3.0pl1-92ubunt management of regular background processing
ii  debconf        1.4.72ubuntu10 Debian configuration management system
ii  debconf-i18n   1.4.72ubuntu10 full internationalization support for debcon
ii  debianutils    2.15.2         Miscellaneous utilities specific to Debian
ii  dhcp3-client   3.0.3-6ubuntu7 DHCP Client
ii  dhcp3-common   3.0.3-6ubuntu7 Common files used by all the dhcp3* packages
ii  diff           2.8.1-11ubuntu File comparison utilities
ii  dmidecode      2.7-3          Dump Desktop Management Interface data
ii  dmsetup        1.02.05-1ubunt The Linux Kernel Device Mapper userspace lib
ii  dnsutils       9.3.2-2ubuntu1 Clients provided with BIND
ii  dosfstools     2.11-2.1ubuntu Utilities to create and check MS-DOS FAT fil
ii  dpkg           1.13.11ubuntu7 package maintenance system for Debian
ii  dselect        1.13.11ubuntu7 user tool to manage Debian packages
ii  e2fslibs       1.38-2ubuntu2  ext2 filesystem libraries
ii  e2fsprogs      1.38-2ubuntu2  ext2 file system utilities and libraries
ii  ed             0.2-20         The classic unix line editor
ii  eject          2.0.13deb-18ub ejects CDs and operates CD-Changers under Li
ii  elinks         0.10.6-1ubuntu advanced text-mode WWW browser
ii  ethtool        3-1            Display or change ethernet card settings
ii  evms           2.5.4-5ubuntu6 Enterprise Volume Management System (core)
ii  evms-ncurses   2.5.4-5ubuntu6 Enterprise Volume Management System (ncurses
ii  fdutils        5.5-20050303-2 Linux floppy utilities
ii  file           4.16-0ubuntu3. Determines file type using "magic" numbers
ii  findutils      4.2.27-1ubuntu utilities for finding files--find, xargs, an
ii  ftp            0.17-16        The FTP client
ii  gcc            4.0.3-1        The GNU C compiler
ii  gcc-4.0        4.0.3-1ubuntu5 The GNU C compiler
ii  gcc-4.0-base   4.0.3-1ubuntu5 The GNU Compiler Collection (base package)
ii  gettext-base   0.14.5-2ubuntu GNU Internationalization utilities for the b
ii  gnupg          1.4.2.2-1ubunt GNU privacy guard - a free PGP replacement
ii  grep           2.5.1.ds2-4    GNU grep, egrep and fgrep
ii  grepmap        1.1.0-1        Parse module map files produced by depmod
ii  groff-base     1.18.1.1-11    GNU troff text-formatting system (base syste
ii  grub           0.97-1ubuntu9  GRand Unified Bootloader
ii  gzip           1.3.5-12ubuntu The GNU compression utility
ii  hdparm         6.3-3ubuntu1   tune hard disk parameters for high performan
ii  hostname       2.91.0ubuntu1  utility to set/show the host name or domain
ii  hwdata         0.172-1ubuntu1 hardware identification / configuration data
ii  ifupdown       0.6.7ubuntu7   high level tools to configure network interf
ii  info           4.8-4ubuntu0.1 Standalone GNU Info documentation browser
ii  initramfs-tool 0.40ubuntu32   tools for generating an initramfs
ii  initscripts    2.86.ds1-6ubun Standard scripts needed for booting and shut
ii  inputattach    1.23-0ubuntu1  utility to attach serial devices to the inpu
ii  installation-r 2.12ubuntu1    system installation report
ii  iproute        20041019-4ubun Professional tools to control the networking
ii  iptables       1.3.3-2ubuntu4 Linux kernel 2.4+ iptables administration to
ii  iptraf         2.7.0-8ubuntu2 Interactive Colorful IP LAN Monitor
ii  iputils-arping 20020927-3ubun Tool to send ICMP echo requests to an ARP ad
ii  iputils-ping   20020927-3ubun Tools to test the reachability of network ho
ii  iputils-tracep 20020927-3ubun Tools to trace the network path to a remote
ii  jfsutils       1.1.8-1        utilities for managing the JFS filesystem
ii  klibc-utils    1.1.16-1ubuntu small statically-linked utilities built with
ii  klogd          1.4.1-17ubuntu Kernel Logging Daemon
ii  less           394-1          Pager program similar to more
ii  libacl1        2.2.34-1ubuntu Access control list shared library
ii  libasound2     1.0.10-2ubuntu ALSA library
ii  libatm1        2.4.1-17       shared library for ATM (Asynchronous Transfe
ii  libattr1       2.4.25-1       Extended attribute shared library
ii  libbind9-0     9.3.2-2ubuntu1 BIND9 Shared Library used by BIND
ii  libblkid1      1.38-2ubuntu2  block device id library
ii  libbz2-1.0     1.0.3-0ubuntu2 high-quality block-sorting file compressor l
ii  libc6          2.3.6-0ubuntu2 GNU C Library: Shared libraries and Timezone
ii  libc6-dev      2.3.6-0ubuntu2 GNU C Library: Development Libraries and Hea
ii  libc6-i686     2.3.6-0ubuntu2 GNU C Library: Shared libraries [i686 optimi
ii  libcap1        1.10-14        support for getting/setting POSIX.1e capabil
ii  libcomerr2     1.38-2ubuntu2  common error description library
ii  libconsole     0.2.3dbs-60ubu Shared libraries for Linux console and font
ii  libcurses-perl 1.13-1         Curses interface for Perl
ii  libcurses-ui-p 0.95-4         curses-based OO user interface framework for
ii  libdb4.3       4.3.29-5build1 Berkeley v4.3 Database Libraries [runtime]
ii  libdevmapper1. 1.02.05-1ubunt The Linux Kernel Device Mapper userspace lib
ii  libdns21       9.3.2-2ubuntu1 DNS Shared Library used by BIND
ii  libedit2       2.9.cvs.200505 BSD editline and history libraries
ii  libelfg0       0.8.5-1.1      an ELF object file access library
ii  libevent1      1.1a-1         An asynchronous event notification library
ii  libevms-2.5    2.5.4-5ubuntu6 Enterprise Volume Management System (library
ii  libexpat1      1.95.8-3       XML parsing C library - runtime library
ii  libfribidi0    0.10.7-1       Free Implementation of the Unicode BiDi algo
ii  libgc1c2       6.6-2ubuntu1   conservative garbage collector for C and C++
ii  libgcc1        4.0.3-1ubuntu5 GCC support library
ii  libgcrypt11    1.2.2-1        LGPL Crypto library - runtime library
ii  libgdbm3       1.8.3-2        GNU dbm database routines (runtime version)
ii  libgnutls12    1.2.9-2ubuntu1 the GNU TLS library - runtime library
ii  libgpg-error0  1.1-4          library for common error values and messages
ii  libgpmg1       1.19.6-21ubunt General Purpose Mouse - shared library
ii  libisc11       9.3.2-2ubuntu1 ISC Shared Library used by BIND
ii  libisccc0      9.3.2-2ubuntu1 Command Channel Library used by BIND
ii  libisccfg1     9.3.2-2ubuntu1 Config File Handling Library used by BIND
ii  libiw28        27+28pre13-1ub Wireless tools - library
ii  libklibc       1.1.16-1ubuntu minimal libc subset for use with initramfs
ii  libkrb53       1.4.3-5ubuntu0 MIT Kerberos runtime libraries
ii  libldap2       2.1.30-12ubunt OpenLDAP libraries
ii  liblocale-gett 1.05-1         Using libc functions for internationalizatio
ii  liblua50       5.0.2-5ubuntu1 Main interpreter library for the Lua 5.0 pro
ii  liblualib50    5.0.2-5ubuntu1 Extension library for the Lua 5.0 programmin
ii  liblwres9      9.3.2-2ubuntu1 Lightweight Resolver Library used by BIND
ii  liblzo1        1.08-3         data compression library (old version)
ii  libmagic1      4.16-0ubuntu3. File type determination library using "magic
ii  libmudflap0    4.0.3-1ubuntu5 GCC mudflap shared support libraries
ii  libmudflap0-de 4.0.3-1ubuntu5 GCC mudflap support libraries (development f
ii  libncurses5    5.5-1ubuntu3   Shared libraries for terminal handling
ii  libncursesw5   5.5-1ubuntu3   Shared libraries for terminal handling (wide
ii  libnewt0.51    0.51.6-31ubunt Not Erik's Windowing Toolkit - text mode win
ii  libnfsidmap1   0.8-1          An nfs idmapping library
ii  libopencdk8    0.5.7-2        Open Crypto Development Kit (OpenCDK) (runti
ii  libpam-foregro 0.3            create lockfiles describing which users own
ii  libpam-modules 0.79-3ubuntu14 Pluggable Authentication Modules for PAM
ii  libpam-runtime 0.79-3ubuntu14 Runtime support for the PAM library
ii  libpam0g       0.79-3ubuntu14 Pluggable Authentication Modules library
ii  libparted1.6-1 1.6.25.1-1ubun The GNU Parted disk partitioning shared libr
ii  libpcap0.8     0.9.4-1        System interface for user-level packet captu
ii  libpcre3       6.4-1.1ubuntu4 Perl 5 Compatible Regular Expression Library
ii  libperl5.8     5.8.7-10ubuntu Shared Perl library
ii  libpopt0       1.7-5          lib for parsing cmdline parameters
ii  libreadline5   5.1-7build1    GNU readline and history libraries, run-time
ii  libsasl2       2.1.19.dfsg1-0 Authentication abstraction library
ii  libsasl2-modul 2.1.19.dfsg1-0 Pluggable Authentication Modules for SASL
ii  libselinux1    1.28-2ubuntu2  SELinux shared libraries
ii  libsepol1      1.10-1         Security Enhanced Linux policy library for c
ii  libsigc++-2.0- 2.0.16-3       type-safe Signal Framework for C++ - runtime
ii  libslang2      2.0.5-1build2  The S-Lang programming library - runtime ver
ii  libss2         1.38-2ubuntu2  command-line interface parsing library
ii  libssl0.9.8    0.9.8a-7ubuntu SSL shared libraries
ii  libstdc++6     4.0.3-1ubuntu5 The GNU Standard C++ Library v3
ii  libsysfs2      2.0.0-5build1  interface library to sysfs
ii  libtasn1-2     0.2.17-1ubuntu Manage ASN.1 structures (runtime)
ii  libterm-readke 2.30-2         A perl module for simple terminal control
ii  libtext-charwi 0.04-3         get display widths of characters on the term
ii  libtext-iconv- 1.4-2          converts between character sets in Perl
ii  libtext-wrapi1 0.06-4         internationalized substitute of Text::Wrap
ii  libusb-0.1-4   0.1.10a-22ubun userspace USB programming library
ii  libuuid1       1.38-2ubuntu2  universally unique id library
ii  libwrap0       7.6.dbs-8ubunt Wietse Venema's TCP wrappers library
ii  linux-image-2. 2.6.15-26.47   Linux kernel image for version 2.6.15 on Ser
ii  linux-image-2. 2.6.15-29.60   Linux kernel image for version 2.6.15 on Ser
ii  linux-image-se 2.6.15.28      Linux kernel image on Server Equipment.
ii  linux-kernel-h 2.6.11.2-0ubun Linux Kernel Headers for development
ii  linux-server   2.6.15.28      Complete Linux kernel on Server Equipment.
ii  linux-sound-ba 1.0.10-4ubuntu base package for ALSA and OSS sound systems
ii  locales        2.3.18.4       common files for locale support
ii  login          4.0.13-7ubuntu system login tools
ii  logrotate      3.7.1-2        Log rotation utility
ii  lsb-base       3.1-5ubuntu2   Linux Standard Base 3.1 init script function
ii  lsb-release    3.1-5ubuntu2   Linux Standard Base version reporting utilit
ii  lshw           02.06-3        information about hardware configuration
ii  lshw-common    02.06-3        information about hardware configuration
ii  lsof           4.76.dfsg.1-1  List open files.
ii  ltrace         0.3.36-2       Tracks runtime library calls in dynamically
ii  lvm-common     1.5.20ubuntu4  The Logical Volume Manager for Linux (common
ii  lvm2           2.02.02-1ubunt The Linux Logical Volume Manager
ii  make           3.80+3.81.b4-1 The GNU version of the "make" utility.
ii  makedev        2.3.1-79ubuntu creates device files in /dev
ii  man-db         2.4.3-3        The on-line manual pager
ii  manpages       2.17-1         Manual pages about using a GNU/Linux system
ii  mawk           1.3.3-11ubuntu a pattern scanning and text processing langu
ii  mdadm          1.12.0-1ubuntu tool to administer Linux md device arrays (s
ii  memtest86+     1.65-1         thorough real-mode memory tester
ii  mii-diag       2.11-1         A little tool to manipulate network cards
ii  mime-support   3.35-2         MIME files 'mime.types' & 'mailcap', and sup
ii  module-init-to 3.2.2-1ubuntu7 tools for managing Linux kernel modules
ii  mount          2.12r-4ubuntu6 Tools for mounting and manipulating filesyst
ii  mtr-tiny       0.69-2ubuntu1  Full screen ncurses traceroute tool
ii  nano           1.3.10-1       free Pico clone with some new features
ii  ncurses-base   5.5-1ubuntu3   Descriptions of common terminal types
ii  ncurses-bin    5.5-1ubuntu3   Terminal-related programs and man pages
ii  net-tools      1.60-16ubuntu2 The NET-3 networking toolkit
ii  netbase        4.24ubuntu3    Basic TCP/IP networking system
ii  netcat         1.10-29        TCP/IP swiss army knife
ii  nfs-common     1.0.7-3ubuntu2 NFS support files common to client and serve
ii  nfs-kernel-ser 1.0.7-3ubuntu2 Kernel NFS server support
ii  nmap           4.20-1~dapper1 The Network Mapper
ii  ntp            4.2.0a+stable- Network Time Protocol: network utilities
ii  ntp-server     4.2.0a+stable- Network Time Protocol: common server tools
ii  ntp-simple     4.2.0a+stable- Network Time Protocol: daemon for simple sys
ii  ntpdate        4.2.0a+stable- The ntpdate client for setting system time f
ii  openssh-client 4.2p1-7ubuntu3 Secure shell client, an rlogin/rsh/rcp repla
ii  openssh-server 4.2p1-7ubuntu3 Secure shell server, an rshd replacement
ii  parted         1.6.25.1-1ubun The GNU Parted disk partition resizing progr
ii  passwd         4.0.13-7ubuntu change and administer password and group dat
ii  pciutils       2.1.11-15.3ubu Linux PCI Utilities
ii  pcmciautils    012-1ubuntu4   PCMCIA utilities for Linux 2.6
ii  perl           5.8.7-10ubuntu Larry Wall's Practical Extraction and Report
ii  perl-base      5.8.7-10ubuntu The Pathologically Eclectic Rubbish Lister
ii  perl-doc       5.8.7-10ubuntu Perl documentation
ii  perl-modules   5.8.7-10ubuntu Core Perl modules
ii  popularity-con 1.31ubuntu2.1  Vote for your favourite packages automatical
ii  portmap        5-16ubuntu2    The RPC portmapper
ii  ppp            2.4.4b1-1ubunt Point-to-Point Protocol (PPP) daemon
ii  pppconfig      2.3.11ubuntu5  A text menu based utility for configuring pp
ii  pppoe          3.5-4ubuntu1   PPP over Ethernet driver
ii  pppoeconf      1.8ubuntu2     configures PPPoE/ADSL connections
ii  procps         3.2.6-2ubuntu4 /proc file system utilities
ii  psmisc         22.1-1         Utilities that use the proc filesystem
ii  python         2.4.2-0ubuntu3 An interactive high-level object-oriented la
ii  python-minimal 2.4.2-0ubuntu3 A minimal subset of the Python language (def
ii  python2.4      2.4.3-0ubuntu6 An interactive high-level object-oriented la
ii  python2.4-mini 2.4.3-0ubuntu6 A minimal subset of the Python language (ver
ii  readline-commo 5.1-7build1    GNU readline and history libraries, common f
ii  reiser4progs   1.0.5-1        administration utilities for the Reiser4 fil
ii  reiserfsprogs  3.6.19-1       User-level tools for ReiserFS filesystems
ii  reportbug      3.18ubuntu1    reports bugs in the Debian distribution
ii  rsync          2.6.6-1ubuntu2 fast remote file copy program (like rcp)
ii  sed            4.1.4-5        The GNU sed stream editor
ii  strace         4.5.12-1ubuntu A system call tracer
ii  sudo           1.6.8p12-1ubun Provide limited super user privileges to spe
ii  sysklogd       1.4.1-17ubuntu System Logging Daemon
ii  sysv-rc        2.86.ds1-6ubun Standard boot mechanism using symlinks in /e
ii  sysv-rc-conf   0.99-3         SysV init runlevel configuration tool for th
ii  sysvinit       2.86.ds1-6ubun System-V like init
ii  tar            1.15.1-2ubuntu GNU tar
ii  tcpd           7.6.dbs-8ubunt Wietse Venema's TCP wrapper utilities
ii  tcpdump        3.9.4-2ubuntu0 A powerful tool for network monitoring and d
ii  telnet         0.17-32        The telnet client
ii  time           1.7-21         The GNU time program for measuring cpu resou
ii  ubuntu-keyring 2005.01.12.1   GnuPG keys of the Ubuntu archive
ii  ubuntu-minimal 0.120          Minimal core of Ubuntu
ii  ubuntu-standar 0.120          The Ubuntu standard system
ii  udev           079-0ubuntu34  rule-based device node and kernel event mana
ii  usbutils       0.71+cvs200510 USB console utilities
ii  util-linux     2.12r-4ubuntu6 Miscellaneous system utilities
ii  vim            6.4-006+2ubunt Vi IMproved - enhanced vi editor
ii  vim-common     6.4-006+2ubunt Vi IMproved - Common files
ii  vim-runtime    6.4-006+2ubunt Vi IMproved - Runtime files
ii  w3m            0.5.1-4ubuntu2 WWW browsable pager with excellent tables/fr
ii  wget           1.10.2-1ubuntu retrieves files from the web
ii  whiptail       0.51.6-31ubunt Displays user-friendly dialog boxes from she
ii  wireless-tools 27+28pre13-1ub Tools for manipulating Linux Wireless Extens
ii  wpasupplicant  0.4.8-3ubuntu1 Client support for WPA and WPA2 (IEEE 802.11
ii  xfsprogs       2.7.7-1        Utilities for managing the XFS filesystem
ii  zlib1g         1.2.3-6ubuntu4 compression library - runtime

```

---

### Post by sonicx on 2007-10-08
hello again,
i solved my problem myself. looking through tons of logs i found the part of my syslog where pppd has to reconnect to the isp, because of that nasty 24hour connection limit. it hit me - thats the only damn 24 hour limit the machine has anything to do with. so i figured it could be nothing else. right i was - a new pppoe connection somehow confuses iptables - i guess some cache holding that dynamic ip from the isp gets stale. although there might be a more elegant solution to flush iptable caches, the easy way for me was to add a skript to /etc/ppp/ip-up.d/ which just runs my firewall skript again (which flushes the all chains on start first). skripts placed there are executed after a connection was made by pppd. well, ill look for a way to do it "right" anyways.
regards,
jonas

---

