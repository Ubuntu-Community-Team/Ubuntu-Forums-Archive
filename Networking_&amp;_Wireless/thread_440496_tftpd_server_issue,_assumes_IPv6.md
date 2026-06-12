---
title: "tftpd server issue, assumes IPv6"
date: 2007-05-11
forum: Networking &amp; Wireless
---

### Post by crashtestyyz on 2007-05-11
So this problem pops up whether you're running tftpd, atftpd, whatever, and as a daemon or from inetd.conf.

May 11 16:40:42 nmc01 tftpd[6800]: unknown option -?
May 11 16:40:42 nmc01 inetd[5261]: /usr/sbin/tcpd: exit status 0x100
May 11 16:40:42 nmc01 in.tftpd[6801]: connect from ::ffff:10.1.10.18 

this is an AMD64 box upgraded to feisty.

Problems such as this I see via google have dated back to at least August of last year, and I'm wondering why this is still an issue.  Even a fresh install with Dapper saw the same problems.  No amount of configuration seems to fix this at all, including turning off ipv6 at the kernel level via modprobe.d.

On debian boxes the same procedure (apt-get install tftpd, edit the inetd.conf file for the directory to use, restart inetd) produces a working tftp server as fast as you can cycle through those steps.

Anybody have a fix for this?

---

### Post by davewantsmoore on 2008-07-11
Erm, I'm having this issue on a fresh hardy install?!  Is it still not fixed?... or have I done something wrong :-/

---

### Post by davewantsmoore on 2008-07-11
fixed by installing openbsd-inetd   :-)

---

