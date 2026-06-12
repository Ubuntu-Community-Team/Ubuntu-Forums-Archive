---
title: "PPTP Error"
date: 2009-06-26
forum: New to Ubuntu
---

### Post by I[AM]SMRT on 2009-06-26
Hi, to connect to my school's wireless I need to setup a pptp connection. I followed the tutorial here:

[http://dotcommie.net/lugsb/PPTP/](http://dotcommie.net/lugsb/PPTP/)

But it's not actually making the connection, here's the pon debug:

```
brian@brian-laptop:~$ pon sunysb debug dump logfd 2 nodetach
pppd options in effect:
debug		# (from command line)
nodetach		# (from command line)
persist		# (from /etc/ppp/peers/sunysb)
logfd 2		# (from command line)
dump		# (from command line)
noauth		# (from /etc/ppp/options.pptp)
name brlin		# (from /etc/ppp/peers/sunysb)
remotename PPTP		# (from /etc/ppp/peers/sunysb)
10		# (from /etc/ppp/peers/sunysb)
		# (from /etc/ppp/options.pptp)
pty pptp pptp.airnet.stonybrook.edu --nolaunchpppd		# (from /etc/ppp/peers/sunysb)
crtscts		# (from /etc/ppp/options)
		# (from /etc/ppp/options)
asyncmap 0		# (from /etc/ppp/options)
lcp-echo-failure 4		# (from /etc/ppp/options)
lcp-echo-interval 30		# (from /etc/ppp/options)
hide-password		# (from /etc/ppp/options)
ipparam tunnel		# (from /etc/ppp/peers/sunysb)
proxyarp		# (from /etc/ppp/options)
nobsdcomp		# (from /etc/ppp/options.pptp)
nodeflate		# (from /etc/ppp/options.pptp)
require-mppe-128		# (from /etc/ppp/peers/sunysb)
noipx		# (from /etc/ppp/options)
speed 10 not supported
using channel 21
Using interface ppp0
Connect: ppp0 <--> /dev/pts/5
anon warn[pptp_gre_bind:pptp_gre.c:87]: socket: Operation not permitted
anon fatal[main:pptp.c:322]: Cannot bind GRE socket, aborting.
Script pptp pptp.airnet.stonybrook.edu --nolaunchpppd finished (pid 25217), status = 0x1
Modem hangup
Connection terminated.
speed 10 not supported
using channel 22
Using interface ppp0
anon warn[pptp_gre_bind:pptp_gre.c:87]: socket: Operation not permitted
anon fatal[main:pptp.c:322]: Cannot bind GRE socket, aborting.
Connect: ppp0 <--> /dev/pts/5
Script pptp pptp.airnet.stonybrook.edu --nolaunchpppd finished (pid 25227), status = 0x1
Modem hangup
Connection terminated.
speed 10 not supported
using channel 23
Using interface ppp0
Connect: ppp0 <--> /dev/pts/5
anon warn[pptp_gre_bind:pptp_gre.c:87]: socket: Operation not permitted
anon fatal[main:pptp.c:322]: Cannot bind GRE socket, aborting.
Script pptp pptp.airnet.stonybrook.edu --nolaunchpppd finished (pid 25237), status = 0x1
Modem hangup
Connection terminated.
speed 10 not supported
using channel 24
Using interface ppp0
Connect: ppp0 <--> /dev/pts/5
anon warn[pptp_gre_bind:pptp_gre.c:87]: socket: Operation not permitted
anon fatal[main:pptp.c:322]: Cannot bind GRE socket, aborting.
Script pptp pptp.airnet.stonybrook.edu --nolaunchpppd finished (pid 25245), status = 0x1
Modem hangup
Connection terminated.
speed 10 not supported
using channel 25
Using interface ppp0
Connect: ppp0 <--> /dev/pts/5
anon warn[pptp_gre_bind:pptp_gre.c:87]: socket: Operation not permitted
anon fatal[main:pptp.c:322]: Cannot bind GRE socket, aborting.
Script pptp pptp.airnet.stonybrook.edu --nolaunchpppd finished (pid 25257), status = 0x1
Modem hangup
Connection terminated.
speed 10 not supported
using channel 26
Using interface ppp0
Connect: ppp0 <--> /dev/pts/5
anon warn[pptp_gre_bind:pptp_gre.c:87]: socket: Operation not permitted
anon fatal[main:pptp.c:322]: Cannot bind GRE socket, aborting.
Script pptp pptp.airnet.stonybrook.edu --nolaunchpppd finished (pid 25267), status = 0x1
Modem hangup
Connection terminated.
speed 10 not supported
using channel 27
Using interface ppp0
Connect: ppp0 <--> /dev/pts/5
anon warn[pptp_gre_bind:pptp_gre.c:87]: socket: Operation not permitted
anon fatal[main:pptp.c:322]: Cannot bind GRE socket, aborting.
Script pptp pptp.airnet.stonybrook.edu --nolaunchpppd finished (pid 25277), status = 0x1
Modem hangup
Connection terminated.
speed 10 not supported
anon warn[pptp_gre_bind:pptp_gre.c:87]: socket: Operation not permitted
anon fatal[main:pptp.c:322]: Cannot bind GRE socket, aborting.
using channel 28
Failed to set PPP kernel option flags: Inappropriate ioctl for device
Using interface ppp0
Connect: ppp0 <--> /dev/pts/5
Script pptp pptp.airnet.stonybrook.edu --nolaunchpppd finished (pid 25287), status = 0x1
Modem hangup
Connection terminated.
speed 10 not supported
using channel 29
Using interface ppp0
Connect: ppp0 <--> /dev/pts/5
anon warn[pptp_gre_bind:pptp_gre.c:87]: socket: Operation not permitted
anon fatal[main:pptp.c:322]: Cannot bind GRE socket, aborting.
Script pptp pptp.airnet.stonybrook.edu --nolaunchpppd finished (pid 25297), status = 0x1
Modem hangup
Connection terminated.
speed 10 not supported
using channel 30
Using interface ppp0
Connect: ppp0 <--> /dev/pts/5
anon warn[pptp_gre_bind:pptp_gre.c:87]: socket: Operation not permitted
anon fatal[main:pptp.c:322]: Cannot bind GRE socket, aborting.
Script pptp pptp.airnet.stonybrook.edu --nolaunchpppd finished (pid 25307), status = 0x1
Modem hangup
Connection terminated.
```

---

### Post by dlazerka on 2010-04-03
Try through sudo.

I know it's weird, looking for good solution.

---

