---
title: "how to set an ip addr add  in rc.local ?"
date: 2019-03-14
forum: Networking &amp; Wireless
---

### Post by theoharis on 2019-03-14
hello

On ubuntu bionic cloud image i want to have this line

ip addr add ip/subnet dev br-vlan

set in rc.local so it works after a reboot

do i enter it as is in rc.local or is there a different syntax ? thanks

---

### Post by TheFu on 2019-03-16
Since systemd took over, rc.local isn't enabled by default.  We need to tell systemd to use it.
[https://www.linuxbabe.com/linux-server/how-to-enable-etcrc-local-with-systemd](https://www.linuxbabe.com/linux-server/how-to-enable-etcrc-local-with-systemd)
I have no idea how reputable that link is.

After that is accomplished, all the normal rc.local rules apply.
* use full paths to any commands.
* don't trust the environment
* any failure stops all processing
* the bottom must have exit 0

The more "correct" solution would be to use the existing network configuration methods to add the extra interface.  I've never used netplan, but that is the newer method since 17.10.

---

