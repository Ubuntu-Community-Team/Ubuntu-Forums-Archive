---
title: "wake on lan (WOL) doesn't work anymore"
date: 2013-12-10
forum: Networking &amp; Wireless
---

### Post by geohei on 2013-12-10
Hi.

I have a pretty old machine, which was running WinXP until some days ago. I decided to put Ubuntu 12.04 i386 server on it.

When using it with WinXP, it was always possible to wake it up using WOL from my router (FRITZ!box 7390). But after Ubuntu was installed, this was not possible anymore. The BIOS (Phoenix, 1.7J, motherboard ECS L7VTA) does not show any option related to WOL.

I don't see how an operating system, which is obviously inactive when the machine is powered off, can influence WOL functionality.

Any ideas?

---

### Post by tgalati4 on 2013-12-10
Install *acpitool* and search these forums for ways to use it.  You want to leave power on to the ethernet card, so that it can receive the WoL signal.  Normally this would be done in BIOS, but if you don't see a setting, then you can use *acpitool* to set it.  You can also leave USB ports powered so you can charge your cell phones when the machine is asleep--handy.

---

### Post by geohei on 2013-12-22
I found that this works as well:
```
# ethtool -s eth0 wol g
```
However ... after running the command above, shutting down the computer, it restarts upon receiving the magic packet. After another shutdown, a restart doesn't work!

It _seems_, that Ubuntu deletes some ACPI values upon shutdown. Can someone confirm this?

I'd like to understand how WOL works before changing configurations and compiling tools like acpitool.
[http://manpages.ubuntu.com/manpages/hardy/man1/acpitool.1.html](http://manpages.ubuntu.com/manpages/hardy/man1/acpitool.1.html)

Some interesting pages about this topic:
[http://ubuntuforums.org/showthread.php?t=1380776](http://ubuntuforums.org/showthread.php?t=1380776)
[http://www.cyberciti.biz/tips/linux-send-wake-on-lan-wol-magic-packets.html](http://www.cyberciti.biz/tips/linux-send-wake-on-lan-wol-magic-packets.html)

/etc/network/interfaces
```
...
post-up /sbin/ethtool -s eth0 wol g
post-down /sbin/ethtool -s eth0 wol g
```
This seems to work now, but I'm not sure why I have to enable MagicPackets while starting _and_ stopping eth0?!
Also ... why post-up/post-down and not up/down or pre-up/pre-down?

Thanks,

---

