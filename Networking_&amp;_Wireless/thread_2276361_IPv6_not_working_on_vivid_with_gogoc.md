---
title: "IPv6 not working on vivid with gogoc"
date: 2015-05-02
forum: Networking &amp; Wireless
---

### Post by jdogzilla on 2015-05-02
Hi all, prior to upgrading to vivid, IPv6 with gogoc was working perfectly on my laptop.  But post upgrade to vivid, it has stopped working.  I purged gogoc and reinstalled it and followed the instructions at their website, but that still didn't work.  Any suggestions on what may be the problem here?

---

### Post by EnkiduinNZ on 2015-05-20
How are you starting gogoc? I found that I was able to start it from a terminal, but it doesn't work if I use the init.d script. This points at a problem with the start process

> prompt# /etc/init.d/gogoc start # No errors from the above, but IPV6 is not working.

prompt# gogoc                        # Works!

Cheers,

Cliff

---

### Post by EnkiduinNZ on 2015-05-21
An update. As above, this is an issue on vivid. Vivid uses systemd by default and previous versions use Upstart. Vivid has both installed, so I booted using Upstart and got the same issue. That is, the sysv type init scripts don't work and neither does 'systemctl' under systemd or 'start' under Upstart.

I've not looked at the init script in depth. Does anyone have any ideas? 

Cheers,

Cliff

---

### Post by snadge on 2015-05-26
I am also finding that gogoc doesn't work unless I manually start it as root.  I have tried turning on the VERBOSE options, but they only seem to work if I start the gogoc process manually from the root shell.  It's probably going to take someone with a better understanding of how systemd works to figure this one out.  The next step may be to log a fault against gogoc, on Launchpad.  There doesn't seem to be any new faults logged against vivid, with this specific issue.

---

