---
title: "Ubuntu 17.10 No Wired internet after Suspend"
date: 2018-02-09
forum: Networking &amp; Wireless
---

### Post by kinasin on 2018-02-09
[FONT=Ubuntu]I recently got a different modem and these past two days my internet's not working after I suspend but it does turn back on after I restart computer. Also it works if I go through the wifi without restarting but the ethernet network stops showing wired connection 1 going to greyed out disconnected, and I'd like my computer to use the main modem. [/FONT][FONT=Ubuntu]I'm now using an Arris TM822r. Kind of a linux newb so forgive me for dumb questions. If you need me to do something else for more info please let me know.[/FONT]

---

### Post by ajgreeny on 2018-02-09
Try running command ```
sudo systemctl restart network-manager.service
``` to see if that restores your network connection.

It it's successful we may be able to do it automatically with a script shown below which includes all instructions, which is normally only needed for wifi, and which I have to use on my old netbook.
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

### Post by kinasin on 2018-02-09
Didn't work.

---

### Post by kinasin on 2018-02-09
this is so weird I don't get why this says ethernet network disconnected and is greyed out until I restart system. What is going on? So annoying.

---

### Post by kinasin on 2018-02-10
Can someone please help me with this?

---

### Post by ronbu on 2018-05-25
I have the same problem with Ubuntu 18.04 Bionic on a wired connection.   If, I can't get it to work I just may switch to install Debian Stretch on my desktop instead while staying with Lubuntu 16.04 Xenial on a laptop.  I was able to get Ubuntu MATE 16.04 to work well on the desktop.

---

