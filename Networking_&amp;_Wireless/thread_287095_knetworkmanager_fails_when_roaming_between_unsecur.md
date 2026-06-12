---
title: "knetworkmanager fails when roaming between unsecured and WPA networks"
date: 2006-10-28
forum: Networking &amp; Wireless
---

### Post by K0LO on 2006-10-28
I am having a strange problem with knetworkmanager in Edgy that was not present in Dapper. My Kubuntu installation is on a laptop with an Intel 2915abg network adapter that is managed by knetworkmanager. At work the wireless networks are open but require VPN. At home my network is secure using WPA2 with AES. I used to be able to roam freely between work and home and knetworkmanager would automatically connect to either network.

Here's what happens now. If I roam to work, a connection is automatically established to the open network. Afterwards if I return home, the following sequence happens. During the boot sequence when the kde desktop is first displayed I can see the tray icon for knetworkmanager briefly. The icon displayed is the one showing a broken connection with a red X. Then a couple of seconds later the popups from knetworkmanager show that the link has been established. At this point the icon vanishes from the tray and the connection never completes.

The only way that I've found to reestablish the connection is to log out of kde and log back in, at which time the sequence completes normally. I can tell that it will complete normally because the tray icon switches to the rotating gear display as the connection is being established and then switches to the signal strength bar graph upon successful completion.

When the icon vanishes from the tray there does not appear to be any way of gaining control over the networkmanager or restarting it. Restarting nm-applet doesn't help, nor does restarting networking or restarting dbus; only a logout/login seems to help. But after establishing the connection once, from then on I can reboot the laptop as many times as I want and it will automatically reconnect to the secure WPA network. It continues to work normally until I roam to a different area and establish a connection to an open wireless network. After doing this it will always fail to reconnect to a secure WPA network as described above.

Has anyone else noted this behavior? Any troubleshooting advice? It would appear to me to be a timing issue; perhaps the networkmanager process is being started too early in the boot sequence.

**31 October update**
Another clue. If I suspend to disk instead of rebooting, knetworkmanager works perfectly 100% of the time. It only gets hung up if it was last associated with an open wireless network and is then rebooted in an area with a secure WPA network.

Question -- how do you kill knetworkmanager when it's hung up? sudo killall knetworkmanager doesn't do it.

---

