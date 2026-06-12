---
title: "Ubuntu 18.04.1 wsdd service failing on reboot, ok after restart"
date: 2019-02-19
forum: Networking &amp; Wireless
---

### Post by glubbish on 2019-02-19
WSDD works fine, but I am having to manually start it.
After reboot the service status is:
&#9679; wsdd.service - Web Services Dynamic Discovery host daemon
   Loaded: loaded (/etc/systemd/system/wsdd.service; enabled; vendor preset: enabled)
   Active: inactive (dead) since Wed 2019-02-20 13:11:52 AEDT; 3min 5s ago
  Process: 811 ExecStart=/usr/bin/wsdd (code=exited, status=0/SUCCESS)
 Main PID: 811 (code=exited, status=0/SUCCESS)

Feb 20 13:11:52 kodi systemd[1]: Started Web Services Dynamic Discovery host daemon.
Feb 20 13:11:52 kodi wsdd[811]: 2019-02-20 13:11:52,592:wsdd WARNING(pid 811): no interface given, using all interfaces
Feb 20 13:11:52 kodi wsdd[811]: 2019-02-20 13:11:52,602:wsdd ERROR(pid 811): No multicast addresses available. Exiting.

doing a service restart fixes it, but cannot find a way to get it to start automatically after reboot
Running 18.04.1

---

### Post by QIII on 2019-02-19
Moved to its own post from [here]("https://ubuntuforums.org/showthread.php?t=2409183").

Posting in a solved thread is unlikely to draw attention to your issue.  Further, we do not allow hijacking of the threads of other users.  While your symptoms may appear to be the same, the underlying cause(s) may be entirely different.

Barging in on another user's thread causes confusion for the OP, for those trying to help -- and for *you*.

---

### Post by glubbish on 2019-02-20
Thanks QIII
Could you also change the title to something that matches the problem with wsdd?

---

### Post by QIII on 2019-02-20
You may edit the title by going to "Edit Post" and then "Go Advanced".

---

### Post by glubbish on 2019-02-20
For anyone else with this problem (needing ws-discovery for windows machines on the network), the following worked for me:

[Unit]
Description=Web Services Dynamic Discovery host daemon
Requires=network-online.target
After=network.target network-online.target multi-user.target

[Service]
Type=simple
ExecStart=/usr/bin/wsdd

[Install]
WantedBy=multi-user.target

I believe its the addition of multi-user.target that is important, but the above wsdd.service works on reboot

---

