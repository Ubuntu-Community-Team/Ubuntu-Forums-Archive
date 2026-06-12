---
title: "Wifi card inactive when waking the computer from sleep"
date: 2018-08-08
forum: Networking &amp; Wireless
---

### Post by dewdrop_world on 2018-08-08
Periodically, I have a problem with the wifi card being dead after waking the computer from sleep.

I'm not sure of the card's model number, but it's using the ath10k_pci driver. Ubuntu Studio 16.04 (with xfce 4.something).

Wifi always works after booting up. It usually works after waking the computer from sleep.

Today, the network manager said, under wireless, "device not ready." Sometimes the network manager gets confused, so I tried ```
sudo systemctl restart NetworkManager.service
``` -- no change. I tried the keyboard's wireless on/off switch -- turn it off, turn it on again -- no change. I also tried reloading the kernel module (sudo modprobe -r ath10k_pci then sudo modprobe ath10k) -- again, no change.

I finally had to reboot, and then the card worked again (else I couldn't post this).

I don't like to reboot, not for this. So, what else can I do to investigate this the next time it happens?

hjh

---

### Post by ajgreeny on 2018-08-08
I am not sure if this will work any better than what you have already tried as it basically runs the same command.
However in this script the command is run by root automatically after return from suspension so it might be the thing that makes all the difference.

Here's the script which has all the detail needed about where to put it etc, etc.

Give it a try; it worked for me when using an old netbook running either Xubuntu or Lubuntu 16.04.
```
#!/bin/bash
# Created by Hans Deragon (hans@deragon.biz), 2015-05-14 07:31:11 EDT

# INSTALLATION
#
#   - Move this script to /lib/systemd/system-sleep/NetworkManagerRestartWorkaroundForBug1380480.sh
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

