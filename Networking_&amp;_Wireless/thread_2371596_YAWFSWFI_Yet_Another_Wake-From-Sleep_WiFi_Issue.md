---
title: "YAWFSWFI Yet Another Wake-From-Sleep WiFi Issue"
date: 2017-09-16
forum: Networking &amp; Wireless
---

### Post by dewdrop_world on 2017-09-16
Hi,

I wonder if someone could provide some guidance on which of the umpteen "wifi dead after wake from sleep" Ubuntu bug reports is actually being worked on.

I had found, after installing Ubuntu Studio 16.04, that intermittently (but frequently) after waking the computer from suspend, wifi was inactive and could not be restored by "Enable Wi-Fi" in the network menu or by the hardware switch.

A script to "systemctl restart NetworkManager.service", installed into /lib/systemd/system-sleep/, seemed to alleviate the problem, but just now, after an update and reboot, it didn't work.

I've been on Ubuntu Studio 16.04 for about three months now, and it's disappointing when I thought I had worked around this problem, but it's still happening. And it's quite confusing to report the issue upstream, as there are several related bug reports open, which generally appear to be stalled, e.g.:

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1615164](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1615164)
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1636282](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1636282)
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1653324](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1653324)
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1676810](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1676810)

Anyway, I wonder if anyone has any better ideas.

For completeness: [http://www.dewdrop-world.net/wireless-info.txt](http://www.dewdrop-world.net/wireless-info.txt)

hjh

---

### Post by ajgreeny on 2017-09-16
I have to use this script to restart networking on an old slow netbook that otherwise runs Lubuntu 16.04 very successfully.

The "sleep 3" at the start of the script line seems quite important and you may need to play around with the time delay to get it to work as you want.
My Lubuntu is fully updated and has not (so far) suffered with this problem; if it did I would simply try running the command ```
sudo systemctl restart NetworkManager.service
```manually in terminal to see if it worked that way as I do not believe it should be necessary to reboot, particularly as you say that did not solve the problem for you.

```
#!/bin/bash
# Created by Hans Deragon (hans@deragon.biz), 2015-05-14 07:31:11 EDT

# INSTALLATION
#
#   - Move this script under: /lib/systemd/system-sleep
#   - chmod +x /lib/systemd/system-sleep/NetworkManagerRestartWorkaroundForBug1380480.sh

# DESCRIPTION
#
#   Restarting the NetworkManager as a workaround for the following bug:
# 
#   &#8729; https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1380480


# 3 seconds delay is necessary apparently.  May be shorter; needs to be
# tested.  But if no delay is implemented, nm-applet crashes.  Seams that we
# need to leave the system resume completely before attempting a restart of
# NetworkManager.
(sleep 3; systemctl restart NetworkManager.service) &
disown
```

---

