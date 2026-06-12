---
title: "daemons, services, etc at startup"
date: 2011-01-01
forum: New to Ubuntu
---

### Post by musendrophilus on 2011-01-01
Hi,

Recently after trying snort and samba my computer has been a little slower when starting up. Is there a way to see if there are any vestigial services or daemons running that may be affecting performance? I checked top in terminal and the only thing that looked out of place were a few k* daemons and I'm pretty sure I removed all the stuff associated with KDE.

Thank you

---

### Post by A_M_S on 2011-01-01
You can use htop. Its on the repositories

---

### Post by musendrophilus on 2011-01-01
Cool, thank you. Would you point me to a command that allows me to see what each daemon does? I ran across this on another forum for Fedora:
----------------------------------------
BASH:~/-> rpm -qf /usr/libexec/rtkit-daemon
rtkit-0.4-1.fc12.i686
BASH:~/-> rpm -qi rtkit
Name        : rtkit                        Relocations: (not relocatable)
Version     : 0.4                               Vendor: Fedora Project
Release     : 1.fc12                        Build Date: Tue 04 Aug 2009 09:53:30 PM EDT
Install Date: Tue 10 Nov 2009 02:39:12 PM EST      Build Host: x86-2.fedora.phx.redhat.com
Group       : System Environment/Base       Source RPM: rtkit-0.4-1.fc12.src.rpm
Size        : 109020                           License: GPLv3+ and BSD
Signature   : RSA/SHA1, Mon 10 Aug 2009 12:00:18 AM EDT, Key ID 9d1cc34857bbccba
Packager    : Fedora Project
URL         : [http://git.0pointer.de/?p=rtkit.git](http://git.0pointer.de/?p=rtkit.git)
Summary     : Realtime Policy and Watchdog Daemon
[B]Description :
RealtimeKit is a D-Bus system service that changes the
scheduling policy of user processes/threads to SCHED_RR (i.e. realtime
scheduling mode) on request. It is intended to be used as a secure
mechanism to allow real-time scheduling to be used by normal user
processes.[/B]
----------------------------------------
It'd be neat to do something like this with Ubuntu.

---

### Post by A_M_S on 2011-01-03
from the terminal, try

```

 dpkg -l | grep name

```

or

```

apropos name

```

or

use google ;)

hope that helps.

---

