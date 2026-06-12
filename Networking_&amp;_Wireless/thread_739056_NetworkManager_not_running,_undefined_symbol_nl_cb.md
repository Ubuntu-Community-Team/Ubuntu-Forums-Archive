---
title: "NetworkManager not running, undefined symbol: nl_cb_alloc"
date: 2008-03-29
forum: Networking &amp; Wireless
---

### Post by tist on 2008-03-29
I have recently made the upgrade to Hardy, and to my surprise NetworkManager did not seem to be running.

nm-tool gives the following output:
```
NetworkManager Tool

get_nm_state(): didn't get a reply from NetworkManager.


NetworkManager appears not to be running (could not get its state).
```

NetworkManager --no-daemon gives the following output:
```
NetworkManager: <info>  starting...
NetworkManager: <info>  New VPN service 'openvpn' (org.freedesktop.NetworkManager.openvpn).
NetworkManager: <info>  New VPN service 'vpnc' (org.freedesktop.NetworkManager.vpnc).
NetworkManager: <info>  New VPN service 'ppp' (org.freedesktop.NetworkManager.ppp_starter).
NetworkManager: <info>  Found radio killswitch /org/freedesktop/Hal/devices/ipw_wlan_switch
NetworkManager: symbol lookup error: NetworkManager: undefined symbol: nl_cb_alloc
```

Which leads me to believe that the culprit is libnl?

libnl1 is at version 1.1-1
network-manager is at version 0.6.6-0ubuntu4

Any ideas or thoughts are appreciated.

Thanks,
tist

---

### Post by eudoxos on 2008-04-28
You can try running

 ldd /usr/sbin/NetworkManager

and making sure that libnl points to the right file in /usr/lib.

I had the same problem, because an older hand-compiled version of libnl was installed in /usr/local/lib and it takes precedence.

---

### Post by tist on 2008-04-28
I don't know how, but there was an old libnl in /lib (while the deb package installs libnl to /usr/lib).

Upon removal networkmanager runs again.

Thanks

---

