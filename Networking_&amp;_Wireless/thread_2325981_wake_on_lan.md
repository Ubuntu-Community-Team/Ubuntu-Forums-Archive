---
title: "wake on lan"
date: 2016-05-27
forum: Networking &amp; Wireless
---

### Post by bolvan on 2016-05-27
My PC was running 12.04 for years and wol worked without a problem.
Now I'm on 16.04 and noticed that wol is not working. Neither for internal realtek or external intel gbit nic.
What I tried :

ethtool -s eth1 wol g
status changes from "d" to "g"
then I shutdown PC. wol does not work

I also could not succeed in autoturning on "g" settings. post-up, up in /etc/network/interfaces does not seem to work. command output no error,  looks like something turns back the setting to "d".  Tried systemd service with the same command - also see "d". Anyway even if set to "g" manually it does not help.

Bios settings did not change. Wake up on PCI device is enabled.
Network manager is removed. Auto interface naming disabled by kernel parameter.

---

### Post by nial2 on 2016-08-06
Same issue here... any luck?

---

