---
title: "(Asus PCE-AC68) wifi not work after pm-suspend"
date: 2017-11-06
forum: Networking &amp; Wireless
---

### Post by huangyingw on 2017-11-06
I use the desktop network manager to connect to my wifi router, everything is ok. But after pm-suspend, looks like my wireless NIC dosen't work correctly, but after rebooting would work.
I use ```
iw phy0 wowlan enable magic-packet disconnect && pm-suspend 
``` to enable wol on wifi before sleep. Actually my final goal is to wol my ubuntu server over wifi(maybe I would open a new thread to discuss this).
Here is my iw dev command output, my wireless NIC is wlp3s0
```
iw dev
phy#0
        Interface wlp3s0
                ifindex 4
                wdev 0x1
                addr de:bd:85:71:ab:89
                type managed
                txpower 200.00 dBm
```
After manually wake it up, looks like wlp3s0 is down, so I use 
```
ip link set wlp3s0 up
``` to bring it up, use ```
ip link show wlp3s0
4: wlp3s0: <NO-CARRIER,BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state DORMANT mode DORMANT group default qlen 1000
    link/ether 22:6e:07:c0:f2:73 brd ff:ff:ff:ff:ff:ff
``` to check that it is up.
and it is not connected: ```
iw wlp3s0 link
Not connected.
```
But the iw scan return null:
```
root@movie:~# iw wlp3s0 scan
root@movie:~#
```
From the desktop UI , I could see no wifi ssid in the drop down list

---

### Post by ajgreeny on 2017-11-06
Which version of Ubuntu do you have?

I did have a similar problem with an old small netbook running Lubuntu 16.04 which I solved by using this script, shown below.
All the info about where to put it is in the text of the script so copy it and save it as it shows as /lib/systemd/system-sleep/NetworkManagerRestartWorkaroundForBug1380480.sh

I increased the sleep time to 4 (seconds) in my system as 3 was occasionally not long enough but you may not need to do so.

Give it a try; if it works for you that's great, if not you can simply remove that shell script and no harm done.

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

### Post by huangyingw on 2017-11-07
It's ubuntu 17.04
After resuming, I log in from another wired NIC, and manually run
```
systemctl restart NetworkManager.service
```, and then from desktop windows, re-connect to my wifi id, 
it works, but only the first time, the second time I pm-suspend, and resume, could not get wifi working again.


> **ajgreeny said:**
> Which version of Ubuntu do you have?

I did have a similar problem with an old small netbook running Lubuntu 16.04 which I solved by using this script, shown below.
All the info about where to put it is in the text of the script so copy it and save it as it shows as /lib/systemd/system-sleep/NetworkManagerRestartWorkaroundForBug1380480.sh

I increased the sleep time to 4 (seconds) in my system as 3 was occasionally not long enough but you may not need to do so.

Give it a try; if it works for you that's great, if not you can simply remove that shell script and no harm done.

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

