---
title: "NetworkManager doesn't prompt for password on new connections"
date: 2018-07-22
forum: Networking &amp; Wireless
---

### Post by lashi on 2018-07-22
Hi all, 

So, I upgraded from 16.04 to 18.04 and it seems that this has introduced some weird behaviour into nm-manager.

When I try and connect to a new secure connection, it doesn't ask me for a password. However, when I do: 

sudo nmtui

and then go in through there to see the new connection (for which an entry is created), and I put the password in, then it all goes through swimmingly. 

Here's an output of the log: 

Jul 22 08:11:37 epsilon NetworkManager[1091]: <info>  [1532257897.7217] keyfile: add connection in-memory (2a9678ba-32ef-462c-aa23-b05c0fc033fa,"NET_2G899BEB")
Jul 22 08:11:37 epsilon NetworkManager[1091]: <info>  [1532257897.7260] device (wlan0): Activation: starting connection 'NET_2G899BEB' (2a9678ba-32ef-462c-aa23-b05c0fc033fa)
Jul 22 08:11:37 epsilon NetworkManager[1091]: <info>  [1532257897.7487] settings-connection[0x5602ae5f1750,2a9678ba-32ef-462c-aa23-b05c0fc033fa]: write: successfully commited (keyfile: update /etc/NetworkManager/system-connections/NET_2G899BEB (2a9678ba-32ef-462c-aa23-b05c0fc033fa,"NET_2G899BEB") and persist connection)
Jul 22 08:11:37 epsilon NetworkManager[1091]: <info>  [1532257897.7488] audit: op="connection-add-activate" uuid="2a9678ba-32ef-462c-aa23-b05c0fc033fa" name="NET_2G899BEB" pid=1883 uid=666 result="success"
Jul 22 08:11:37 epsilon NetworkManager[1091]: <info>  [1532257897.7589] device (wlan0): state change: disconnected -> prepare (reason 'none', sys-iface-state: 'managed')
Jul 22 08:11:37 epsilon NetworkManager[1091]: <info>  [1532257897.7592] manager: NetworkManager state is now CONNECTING
Jul 22 08:11:37 epsilon NetworkManager[1091]: <info>  [1532257897.7612] device (wlan0): state change: prepare -> config (reason 'none', sys-iface-state: 'managed')
Jul 22 08:11:37 epsilon NetworkManager[1091]: <info>  [1532257897.7620] device (wlan0): Activation: (wifi) access point 'NET_2G899BEB' has security, but secrets are required.
Jul 22 08:11:37 epsilon NetworkManager[1091]: <info>  [1532257897.7621] device (wlan0): state change: config -> need-auth (reason 'none', sys-iface-state: 'managed')
Jul 22 08:11:37 epsilon NetworkManager[1091]: <info>  [1532257897.7624] sup-iface[0x5602ae3b3190,wlan0]: wps: type pbc start...
Jul 22 08:12:02 epsilon NetworkManager[1091]: <warn>  [1532257922.7944] device (wlan0): No agents were available for this request.
Jul 22 08:12:08 epsilon NetworkManager[1091]: <info>  [1532257928.0014] device (wlan0): state change: need-auth -> failed (reason 'no-secrets', sys-iface-state: 'managed')
Jul 22 08:12:08 epsilon NetworkManager[1091]: <info>  [1532257928.0021] manager: NetworkManager state is now DISCONNECTED
Jul 22 08:12:08 epsilon NetworkManager[1091]: <warn>  [1532257928.0032] device (wlan0): Activation: failed for connection 'NET_2G899BEB'
Jul 22 08:12:08 epsilon NetworkManager[1091]: <info>  [1532257928.0179] device (wlan0): state change: failed -> disconnected (reason 'none', sys-iface-state: 'managed')
Jul 22 08:12:08 epsilon kernel: [  502.869197] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready


There's a "No agents were available" warning, I suspect this has something to do with it? 

I've mucked around a lot trying to get it to work, but I can't figure out what's going on for the life of me. 

The user in question is in netdev and sudoers, and I've also tried with a freshly created new user and it's the same problem. 

Thanks in advance! 

Cheers, 

- Lashi

---

