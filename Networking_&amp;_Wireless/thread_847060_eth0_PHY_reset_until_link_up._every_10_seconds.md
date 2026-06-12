---
title: "eth0: PHY reset until link up. every 10 seconds"
date: 2008-07-02
forum: Networking &amp; Wireless
---

### Post by philstovell on 2008-07-02
I'm getting the message "eth0: PHY reset until link up." repeated every 10 seconds in my log files (/var/log/messages).

eth0 is not in use - I'm connected wirelessly (wlan0). eth0 is a 191 Gigabit Ethernet Adapter.

There's no way to unconfigure the device in the BIOS.

Everything seems to work OK otherwise.

Google doesn't come up with any way to stop this. Does anyone have any ideas?

Cheers.

---

### Post by Iowan on 2008-07-02
Check **/etc/network/interfaces**. If there's a line: "auto eth0", comment it out (or delete it - but make a backup first).

---

### Post by philstovell on 2008-07-03
> **Iowan said:**
> Check **/etc/network/interfaces**. If there's a line: "auto eth0", comment it out (or delete it - but make a backup first).

Thanks for the reply. There is no "auto eth0" in interfaces:

```
auto lo
iface lo inet loopback
# Slow wireless: http://ubuntuforums.org/showpost.php?p=4869076&postcount=25
pre-up iwconfig wlan0 rate 54M
```

I'm now also getting printk messages in /var/log/messages as well:

```
Jul  3 06:04:57 hendrix kernel: [  708.446557] eth0: PHY reset until link up.
Jul  3 06:05:07 hendrix kernel: [  714.614518] eth0: PHY reset until link up.
Jul  3 06:05:15 hendrix kernel: [  720.043755] printk: 1 messages suppressed.
Jul  3 06:05:17 hendrix kernel: [  720.990562] eth0: PHY reset until link up.
Jul  3 06:05:22 hendrix kernel: [  724.142479] printk: 2 messages suppressed.
Jul  3 06:05:27 hendrix kernel: [  726.816852] eth0: PHY reset until link up.
Jul  3 06:05:27 hendrix kernel: [  727.039299] printk: 1 messages suppressed.
Jul  3 06:05:32 hendrix kernel: [  730.208184] printk: 1 messages suppressed.
Jul  3 06:05:36 hendrix kernel: [  732.498383] printk: 2 messages suppressed.
Jul  3 06:05:37 hendrix kernel: [  733.134121] eth0: PHY reset until link up.
```

Everything seems to work OK, it's really just an annoyance!

Cheers.

---

