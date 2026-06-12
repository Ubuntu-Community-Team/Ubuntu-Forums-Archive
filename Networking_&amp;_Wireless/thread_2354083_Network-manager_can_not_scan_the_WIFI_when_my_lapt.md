---
title: "Network-manager can not scan the WIFI when my laptop wake up from suspending"
date: 2017-02-28
forum: Networking &amp; Wireless
---

### Post by okcdz on 2017-02-28
The WIFI works normally at the beginning,  but when I suspended my laptop and woke it up, the WIFI cannot scan the WIFI which worked well at the beginning. It can not help even if I close the network at the status bar and start it again.
I have to restart the network-manager manually, and the WIFI works again. It's the only way to solve the problem for the moment. Is this a bug? How to solve it?

System: Ubuntu 16.04 LTS
Laptop: Thinkpad X1 Carbon 2015

[ATTACH]273932[/ATTACH]

---

### Post by wildmanne39 on 2017-02-28
Click on the wireless script in my signature while you can not connnect and follow the directions for running it and posting the file it creates here.

---

### Post by ajgreeny on 2017-02-28
There appears to be a lot of problems with wifi disappearing after suspend, and I had that very problem in 16.04 on an old netbook which was solved following adding the file I attach below.

The instructions about where to put it are shown in the script itself so copy and paste the the file and follow the instructions to make it executable.
```
#!/bin/bash
# Created by Hans Deragon (hans@deragon.biz), 2015-05-14 07:31:11 EDT

# INSTALLATION
#
#   - Move this script into  /lib/systemd/system-sleep
#   - run "sudo chmod +x /lib/systemd/system-sleep/NetworkManagerRestartWorkaroundForBug1380480.sh"

# DESCRIPTION
#
#   Re#!/bin/bash
# Created by Hans Deragon (hans@deragon.biz), 2015-05-14 07:31:11 EDT

# INSTALLATION
#
#   - Move this script into  /lib/systemd/system-sleep
#   - run "sudo chmod +x /lib/systemd/system-sleep/NetworkManagerRestartWorkaroundForBug1380480.sh"

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
starting the NetworkManager as a workaround for the following bug:
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

### Post by okcdz on 2017-02-28
Thanks for helping. I have ran the scripts, the file is here:

[ATTACH]273932[/ATTACH]

---

### Post by okcdz on 2017-02-28
Yep! It seems that your script restart the network-manager automatically after sleep, I think it's a good solution for the moment. But I want to know why it happens.

---

### Post by okcdz on 2017-03-01
> **wildmanne39 said:**
> Click on the wireless script in my signature while you can not connnect and follow the directions for running it and posting the file it creates here.

[ATTACH]273932[/ATTACH]

---

