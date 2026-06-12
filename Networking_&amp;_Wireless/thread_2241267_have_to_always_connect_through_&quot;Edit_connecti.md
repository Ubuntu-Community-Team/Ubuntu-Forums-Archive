---
title: "have to always connect through &quot;Edit connections&quot; using NW"
date: 2014-08-25
forum: Networking &amp; Wireless
---

### Post by Elktro on 2014-08-25
What is wrong with my Network manager connection. I have a WPA & WPA2 Enterprise, tunneled TLS using PAP connection to a wireless network.

Everything was working fine until I changed the my password of my account which meant that I had to change it for the connection as well.

Now the only way I can connect to the wireless network is that if I go to the "edit connections" choose the appropriate ESSID name and go to the "Wifi Security" tab, enter my pass word and click save. Then it connects to the network.

If I select the ESSID name from the Network Manager list by right clicking the the nm-applet icon, it won't connect. It even does not seem to try to connect to the wireless network but immediately just disconnects.

If I now go to the connection properties there is no password saved. I now, again, I can enter the password and connect, but it won't save it. I have tried to delete and reconfigure the connection, I have tried to untick and tick the "All users may connect this network" option. I tried to tick the "Ask for this password every time" option on, but I won't even ask my password.

These are my syslog entries after a failed connection described above.

```
Aug 25 16:44:45 mycomputer NetworkManager[896]: <info> Activation (wlan0) starting connection 'prtctdwlan'
Aug 25 16:44:45 mycomputer NetworkManager[896]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Aug 25 16:44:45 mycomputer NetworkManager[896]: <info> NetworkManager state is now CONNECTING
Aug 25 16:44:45 mycomputer NetworkManager[896]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Aug 25 16:44:45 mycomputer NetworkManager[896]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Aug 25 16:44:45 mycomputer NetworkManager[896]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Aug 25 16:44:45 mycomputer NetworkManager[896]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Aug 25 16:44:45 mycomputer NetworkManager[896]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Aug 25 16:44:45 mycomputer NetworkManager[896]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Aug 25 16:44:45 mycomputer NetworkManager[896]: <info> Activation (wlan0/wireless): access point 'prtctdwlan' has security, but secrets are required.
Aug 25 16:44:45 mycomputer NetworkManager[896]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Aug 25 16:44:45 mycomputer NetworkManager[896]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Aug 25 16:44:45 mycomputer NetworkManager[896]: <warn> No agents were available for this request.
Aug 25 16:44:45 mycomputer NetworkManager[896]: <info> (wlan0): device state change: need-auth -> failed (reason 'no-secrets') [60 120 7]
Aug 25 16:44:45 mycomputer NetworkManager[896]: <info> NetworkManager state is now DISCONNECTED
Aug 25 16:44:45 mycomputer NetworkManager[896]: <info> Marking connection 'prtctdwlan' invalid.
Aug 25 16:44:45 mycomputer NetworkManager[896]: <warn> Activation (wlan0) failed for connection 'prtctdwlan'
Aug 25 16:44:45 mycomputer NetworkManager[896]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Aug 25 16:44:45 mycomputer NetworkManager[896]: <info> (wlan0): deactivating device (reason 'none') [0]
```

How to fix this?

---

