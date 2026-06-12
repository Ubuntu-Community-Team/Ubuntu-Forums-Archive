---
title: "A start job is running for Raise network interfaces (5min 2s) in Ubuntu 18.04"
date: 2019-06-02
forum: Networking &amp; Wireless
---

### Post by imagerodeo on 2019-06-02
Problem: 5 minute delay on startup

Device: UP board, running 18.04, with a Panda PAU05 wireless USB adapter, connected via HDMI to a keyboard

Network configuration: using netplan and systemd-networkd. NetworkManager is not installed.

When the Ethernet is connected, the device boots up quickly. I can unplug the Ethernet and rely on wifi. SSH works, etc.

When the Ethernet is not connected, there's a 5 minute delay. The console says "A start job is running for Raise network interfaces (Xmin Ys / 5min 2s)" and slowly counts up to 5min 2s. I can ping the device, but ssh is refused: "ssh: connect to host rodeobot.local port 22: Connection refused". After 5 minutes the boot completes fine.

I tinkered with my netplan to make both ethernet and wifi interfaces optional, but this doesn't help. I also tried removing the ethernet interface, but that didn't help. Here's "/etc/netplan/config.yaml":

```
network:
  version: 2
  renderer: networkd
  #ethernets:
  enp1s0:
    optional: true  # Don't wait for Ethernet
    dhcp4: true
  wifis:
    wlx9cefd5fcb328:
      optional: true  # Don't wait for Wifi
      dhcp4: true
      access-points:
        "xxx":
          password: "yyy"

```

Any ideas?

---

### Post by Xian on 2019-06-02
See if this information is helpful: 

[https://ubuntuforums.org/showthread.php?t=2323253](https://ubuntuforums.org/showthread.php?t=2323253)

---

### Post by imagerodeo on 2019-06-03
Ah, that was helpful. A quick edit to /etc/network/interfaces did the trick:

Old:
auto enp1s0

New:
allow-hotplug enp1s0

Shouldn't "sudo netplan apply" have done that? I'm a bit confused. But my boot times are now quick.

---

### Post by imagerodeo on 2019-06-04
Ah, now that I understand Ubuntu 18.04 networking a tad better, I see that the root cause was the fact that enp1s0 wasn't managed by networkd -- it was managed by ifupdown. The fix was to "sudo apt remove ifupdown". I also renamed the /etc/network directory to avoid confusion.

---

