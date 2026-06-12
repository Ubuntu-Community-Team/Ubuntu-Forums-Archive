---
title: "slmodem configuration"
date: 2008-03-14
forum: Networking &amp; Wireless
---

### Post by Bonanzaman on 2008-03-14
OK, after abandoning attempts to install Gutsy on my old Dell,
I "obtained" a little newer machine, and the install then went pretty cleanly.
Next challenge was to get my dialup modem configured and set up properly.
This has proven to be quite a process...found and installed the correct slamr driver
(I hope ), ran slmodemd scripts, created port with sudo modprobe ungrab-winmodem, then ran
wvdialconf /ect/wvdial.conf

got: found modem on /dev/ttysl0, then wvdialconf /ect/wvdial.conf <warn> can't open
wvdialconf /ect/wvdial.conf for reading : no such file or directory,
and
wvdialconf /ect/wvdial.conf starting blank configuration, modem configuration
written to wvdialconf /ect/wvdial.conf <warn> can't write wvdialconf /ect/wvdial.conf
temp5751,
bad file descriptor.

What step have I missed here?

(Also failed trying to install kppp, got:
E: couldn't find package kppp)

---

