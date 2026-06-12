---
title: "Can't re-enable wireless (Network Manager)"
date: 2018-07-02
forum: Networking &amp; Wireless
---

### Post by jsonfn on 2018-07-02
I run Ubuntu 16.04 LTS. Network manager somewhat exhibits weird behaviour. First untick `enable Wi-Fi`, then tick `enable Wi-Fi` again. Within "Wi-Fi networks" section, the NetworkManager is no longer able to see the any networks that provide Wi-Fi connection. `syslog` shows following message when `disable` then `enable` Wi-Fi.

```

// Disable Wi-Fi through NetworkManager sys tray. 
Jul  2 16:45:35 myhost systemd[1]: Starting Load/Save RF Kill Switch Status...
Jul  2 16:45:35 myhost systemd[1]: Started Load/Save RF Kill Switch Status.
Jul  2 16:45:35 myhost kernel: [ 2277.235240] iwlwifi 0000:02:00.0: RF_KILL bit toggled to disable radio.
Jul  2 16:45:35 myhost kernel: [ 2277.235242] iwlwifi 0000:02:00.0: reporting RF_KILL (radio disabled)
Jul  2 16:45:35 myhost NetworkManager[1095]: <info>  [1530542735.6473] manager: WiFi hardware radio set disabled
Jul  2 16:45:35 myhost NetworkManager[1095]: <info>  [1530542735.6475] audit: op="radio-control" arg="wireless-enabled:0" pid=3401 uid=1000 result="success"
Jul  2 16:45:35 myhost NetworkManager[1095]: <info>  [1530542735.6478] manager: WiFi now disabled by radio killswitch

// Enable Wi-Fi through NetworkManager sys tray. 
Jul  2 16:47:27 myhost NetworkManager[1095]: <info>  [1530542847.4987] manager: WiFi hardware radio set enabled
Jul  2 16:47:27 myhost systemd[1]: Starting Load/Save RF Kill Switch Status...
Jul  2 16:47:27 myhost kernel: [ 2389.106909] iwlwifi 0000:02:00.0: RF_KILL bit toggled to enable radio.
Jul  2 16:47:27 myhost kernel: [ 2389.106910] iwlwifi 0000:02:00.0: reporting RF_KILL (radio enabled)
Jul  2 16:47:27 myhost systemd[1]: Started Load/Save RF Kill Switch Status.
Jul  2 16:47:27 myhost NetworkManager[1095]: <info>  [1530542847.7064] audit: op="radio-control" arg="wireless-enabled:1" pid=3401 uid=1000 result="success"
Jul  2 16:47:27 myhost NetworkManager[1095]: <info>  [1530542847.7073] manager: WiFi now enabled by radio killswitch
Jul  2 16:47:27 myhost kernel: [ 2389.314918] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready


```

It looks like my wireless link is not get ready (even after I wait for a while). What might  cause this problem, and how to fix that? Thanks

---

### Post by ajgreeny on 2018-07-02
There was a bug for this problem [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1380480](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1380480) and a workaround script which worked for me, and which I show below.
All the instructions for it and where to put it are shown in the text of the script
Give it a try and it may work for you as it did for me using whenh I was using Lubuntu 16.04
The bug appears to have been squashed in Lubuntu 18.04 so an OS upgrade may be another possible answer if you are prepared to try that.
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


# 3 or 4 seconds delay is necessary apparently.  May be shorter or longer and needs to be
# tested.  But if no delay is implemented, nm-applet crashes.  Seams that we
# need to leave the system resume completely before attempting a restart of
# NetworkManager.
(sleep 4; systemctl restart NetworkManager.service) &
disown

```

---

