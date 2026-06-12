---
title: "Network manager logs ip6 warnings when I connect to nordvpn"
date: 2024-07-19
forum: Networking &amp; Wireless
---

### Post by lister171254 on 2024-07-19
I have installed norvpn via snap and have found the following issue when I connect
```
Jul 19 17:06:12 LeosGamesLaptop dbus-daemon[2346]: message repeated 11 times: [ apparmor="DENIED" operation="dbus_signal"  bus="session" path="/StatusNotifierItem/menu" interface="org.freedesktop.DBus.Properties" member="PropertiesChanged" mask="send" name="org.freedesktop.DBus" pid=3174 label="snap.nordvpn.nordvpn" peer_pid=2593 peer_label="unconfined"]
Jul 19 17:06:13 LeosGamesLaptop NetworkManager[933]: <warn>  [1721401573.0079] platform-linux: do-add-ip6-address[3: fe80::fcf5:1632:5ed8:2a2]: failure 13 (Permission denied)
Jul 19 17:06:15 LeosGamesLaptop NetworkManager[933]: <warn>  [1721401575.0081] platform-linux: do-add-ip6-address[3: fe80::931:b858:79a8:b4a6]: failure 13 (Permission denied)
Jul 19 17:06:17 LeosGamesLaptop NetworkManager[933]: <warn>  [1721401577.0103] platform-linux: do-add-ip6-address[3: fe80::ad9f:af02:ca97:dd89]: failure 13 (Permission denied)
Jul 19 17:06:19 LeosGamesLaptop NetworkManager[933]: <warn>  [1721401579.0132] platform-linux: do-add-ip6-address[3: fe80::c045:b6e8:46:df8b]: failure 13 (Permission denied)
Jul 19 17:06:20 LeosGamesLaptop systemd[1]: NetworkManager-dispatcher.service: Deactivated successfully.
Jul 19 17:06:21 LeosGamesLaptop NetworkManager[933]: <warn>  [1721401581.0138] ipv6ll[6d8a71e68927d1b3,ifindex=3]: changed: no IPv6 link local address to retry after Duplicate Address Detection failures (back off)
Jul 19 17:06:30 LeosGamesLaptop nordvpn.nordvpnd[1117]: 2024/07/19 17:06:30 [NC] connection lost:  pingresp not received, disconnecting
Jul 19 17:06:30 LeosGamesLaptop nordvpn.nordvpnd[1117]: 2024/07/19 17:06:30 [NC] start connection loop
Jul 19 17:06:30 LeosGamesLaptop nordvpn.nordvpnd[1117]: 2024/07/19 17:06:30 [Info] [NC] Connected
Jul 19 17:06:30 LeosGamesLaptop nordvpn.nordvpnd[1117]: 2024/07/19 17:06:30 [NC] Connected
Jul 19 17:06:31 LeosGamesLaptop NetworkManager[933]: <warn>  [1721401591.0158] platform-linux: do-add-ip6-address[3: fe80::6b7:eacf:c624:f887]: failure 13 (Permission denied)
Jul 19 17:06:33 LeosGamesLaptop NetworkManager[933]: <warn>  [1721401593.0167] platform-linux: do-add-ip6-address[3: fe80::50d6:60d3:cbff:3de7]: failure 13 (Permission denied)
Jul 19 17:06:35 LeosGamesLaptop NetworkManager[933]: <warn>  [1721401595.0196] platform-linux: do-add-ip6-address[3: fe80::fcf5:1632:5ed8:2a2]: failure 13 (Permission denied)
Jul 19 17:06:37 LeosGamesLaptop NetworkManager[933]: <warn>  [1721401597.0223] platform-linux: do-add-ip6-address[3: fe80::931:b858:79a8:b4a6]: failure 13 (Permission denied)
Jul 19 17:06:39 LeosGamesLaptop NetworkManager[933]: <warn>  [1721401599.0232] platform-linux: do-add-ip6-address[3: fe80::ad9f:af02:ca97:dd89]: failure 13 (Permission denied)
Jul 19 17:06:41 LeosGamesLaptop NetworkManager[933]: <warn>  [1721401601.0261] platform-linux: do-add-ip6-address[3: fe80::c045:b6e8:46:df8b]: failure 13 (Permission denied)
Jul 19 17:06:43 LeosGamesLaptop NetworkManager[933]: <warn>  [1721401603.0284] ipv6ll[6d8a71e68927d1b3,ifindex=3]: changed: no IPv6 link local address to retry after Duplicate Address Detection failures (back off)
```

---

### Post by #&amp;thj^% on 2024-07-19
Looks like a bug with apparmor to me. Please see this and the bug report: [https://ubuntuforums.org/showthread.php?t=2493479](https://ubuntuforums.org/showthread.php?t=2493479)
These two are owned By Nord
```
sudo aa-status|grep surfshark
   surfshark
   /opt/Surfshark/surfshark (2884) surfshark
   /opt/Surfshark/surfshark (3015) surfshark
   /opt/Surfshark/surfshark (3017) surfshark
   /opt/Surfshark/surfshark (3022) surfshark
   /opt/Surfshark/chrome_crashpad_handler (3071) surfshark
   /opt/Surfshark/surfshark (3107) surfshark
   /opt/Surfshark/surfshark (3158) surfshark

```

If you want a .deb install I can help.

---

### Post by lister171254 on 2024-07-20
Thanks, i've reported the issue
[https://bugs.launchpad.net/ubuntu/+source/apparmor/+bug/2073661](https://bugs.launchpad.net/ubuntu/+source/apparmor/+bug/2073661)

---

### Post by #&amp;thj^% on 2024-07-20
What I see here:
```
Jul 20 14:14:30 LeosGamesLaptop kernel: [   84.907335] audit: type=1400 audit(1721477670.952:74): apparmor="DENIED" operation="exec" class="file" profile="snap.nordvpn.nordvpnd" name="/usr/bin/timedatectl" pid=1501 comm="nordvpnd" requested_mask="x" denied_mask="x" fsuid=0 ouid=0
```
And 
```
Jul 20 14:14:34 LeosGamesLaptop kernel: [   88.168531] audit: type=1400 audit(1721477674.389:75): apparmor="DENIED" operation="open" class="file" profile="snap.nordvpn.nordvpnd" name="/proc/1115/mountinfo" pid=1115 comm="nordvpnd" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
```

This is enough for me:
```
 apparmor="DENIED" operation="dbus_signal"  bus="session" path="/StatusNotifierItem" interface="org.freedesktop.DBus.Properties" member="PropertiesChanged" mask="send" name="org.freedesktop.DBus" pid=3261 label="snap.nordvpn.nordvpn" peer_pid=2566 peer_label="unconfined"
Jul 20 14:30:03 LeosGamesLaptop dbus-daemon[2318]: apparmor="DENIED" operation="dbus_signal"  bus="session" path="/StatusNotifierItem/menu" interface="org.freedesktop.DBus.Properties" member="PropertiesChanged" mask="send" name="org.freedesktop.DBus" pid=3261 label="snap.nordvpn.nordvpn" peer_pid=2566 peer_label="unconfined"
Jul 20 14:30:03 LeosGamesLaptop dbus-daemon[2318]: message repeated 11 times: [ apparmor="DENIED" operation="dbus_signal"bus="session" path="/StatusNotifierItem/menu" interface="org.freedesktop.DBus.Properties" member="PropertiesChanged" mask="send" name="org.freedesktop.DBus" pid=3261 label="snap.nordvpn.nordvpn" peer_pid=2566 peer_label="unconfined"]
Jul 20 14:30:25 LeosGamesLaptop nordvpn.nordvpnd[1115]: 2024/07/20 14:30:25 [NC] connection lost:  pingresp not received, disconnecting 
```

cboltz will have this figured out quickly if he is not busy elsewhere.

Have you tried disabling apparmor to confirm?

My bug report I actually removed apparmor temporally for proof.
Good Luck

---

### Post by lister171254 on 2024-07-21
I've stopped apparmor but that doesn't seem to be enough
```
&#9675; apparmor.service - Load AppArmor profiles
     Loaded: loaded (/lib/systemd/system/apparmor.service; enabled; vendor preset: enabled)
     Active: inactive (dead) since Sun 2024-07-21 10:44:14 CEST; 2min 19s ago
       Docs: man:apparmor(7)
             https://gitlab.com/apparmor/apparmor/wikis/home/
    Process: 515 ExecStart=/lib/apparmor/apparmor.systemd reload (code=exited, status=0/SUCCESS)
    Process: 7611 ExecStop=/bin/true (code=exited, status=0/SUCCESS)
   Main PID: 515 (code=exited, status=0/SUCCESS)
        CPU: 1ms

Jul 21 08:16:22 LeosGamesLaptop apparmor.systemd[515]: Restarting AppArmor
Jul 21 08:16:22 LeosGamesLaptop apparmor.systemd[515]: Reloading AppArmor profiles
Jul 21 08:16:11 LeosGamesLaptop systemd[1]: Starting Load AppArmor profiles...
Jul 21 08:16:25 LeosGamesLaptop apparmor.systemd[855]: Skipping profile in /etc/apparmor.d/disable: usr.sbin.rsyslogd
Jul 21 08:16:26 LeosGamesLaptop systemd[1]: Finished Load AppArmor profiles.
Jul 21 10:44:14 LeosGamesLaptop systemd[1]: Stopping Load AppArmor profiles...
Jul 21 10:44:14 LeosGamesLaptop systemd[1]: apparmor.service: Deactivated successfully.
Jul 21 10:44:14 LeosGamesLaptop systemd[1]: Stopped Load AppArmor profiles.

```

The issue is still there
```
Jul 21 10:45:40 LeosGamesLaptop nordvpn.nordvpnd[1065]: -P OUTPUT ACCEPT
Jul 21 10:45:42 LeosGamesLaptop NetworkManager[896]: <warn>  [1721551542.3047] platform-linux: do-add-ip6-address[3: fe80::fcf5:1632:5ed8:2a2]: failure 13 (Permission denied)
Jul 21 10:45:42 LeosGamesLaptop dbus-daemon[2446]: apparmor="DENIED" operation="dbus_signal"  bus="session" path="/StatusNotifierItem" interface="org.freedesktop.DBus.Properties" member="PropertiesChanged" mask="send" name="org.freedesktop.DBus" pid=7662 label="snap.nordvpn.nordvpn" peer_pid=2696 peer_label="unconfined"
Jul 21 10:45:42 LeosGamesLaptop dbus-daemon[2446]: apparmor="DENIED" operation="dbus_signal"  bus="session" path="/StatusNotifierItem/menu" interface="org.freedesktop.DBus.Properties" member="PropertiesChanged" mask="send" name="org.freedesktop.DBus" pid=7662 label="snap.nordvpn.nordvpn" peer_pid=2696 peer_label="unconfined"
Jul 21 10:45:42 LeosGamesLaptop dbus-daemon[2446]: message repeated 11 times: [ apparmor="DENIED" operation="dbus_signal"  bus="session" path="/StatusNotifierItem/menu" interface="org.freedesktop.DBus.Properties" member="PropertiesChanged" mask="send" name="org.freedesktop.DBus" pid=7662 label="snap.nordvpn.nordvpn" peer_pid=2696 peer_label="unconfined"]
Jul 21 10:45:44 LeosGamesLaptop NetworkManager[896]: <warn>  [1721551544.3052] platform-linux: do-add-ip6-address[3: fe80::931:b858:79a8:b4a6]: failure 13 (Permission denied)
Jul 21 10:45:46 LeosGamesLaptop NetworkManager[896]: <warn>  [1721551546.3073] platform-linux: do-add-ip6-address[3: fe80::ad9f:af02:ca97:dd89]: failure 13 (Permission denied)
Jul 21 10:45:48 LeosGamesLaptop NetworkManager[896]: <warn>  [1721551548.3101] platform-linux: do-add-ip6-address[3: fe80::c045:b6e8:46:df8b]: failure 13 (Permission denied)
Jul 21 10:45:49 LeosGamesLaptop systemd[1]: NetworkManager-dispatcher.service: Deactivated successfully.
Jul 21 10:45:50 LeosGamesLaptop NetworkManager[896]: <warn>  [1721551550.3125] ipv6ll[5a79121fbb926d53,ifindex=3]: changed: no IPv6 link local address to retry after Duplicate Address
```

Maybe I need to disable apparmor and reboot

---

### Post by #&amp;thj^% on 2024-07-21
I ran into that as well, so i actually removed apparmor for a session.
```
sudo systemctl stop apparmor
sudo systemctl disable apparmor
```
That still was not good enough on my end so i ran:
```
sudo apt purge apparmor
```
After the Reboot my VPN was good to go.

---

