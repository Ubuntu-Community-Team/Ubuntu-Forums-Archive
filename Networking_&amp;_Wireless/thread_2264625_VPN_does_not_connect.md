---
title: "VPN does not connect"
date: 2015-02-08
forum: Networking &amp; Wireless
---

### Post by leehodg on 2015-02-08
When I try to connect to my VPN it doesn't seem to do anything. Examining the logs shows the error messages:

    Feb  9 09:13:48 titania NetworkManager[799]: <info> Starting VPN service 'pptp'...
    Feb  9 09:13:48 titania NetworkManager[799]: <info> VPN service 'pptp' started (org.freedesktop.NetworkManager.pptp), PID 5573
    Feb  9 09:13:48 titania NetworkManager[799]: <info> VPN service 'pptp' appeared; activating connections
    Feb  9 09:13:48 titania NetworkManager[799]: <error> [1423448028.441626] [nm-vpn-connection.c:1374] get_secrets_cb(): Failed to request VPN secrets #2: (6) No agents were available for this request.
    Feb  9 09:13:48 titania NetworkManager[799]: <info> Policy set 'leewifi' (wlan0) as default for IPv4 routing and DNS.
    Feb  9 09:13:53 titania NetworkManager[799]: <info> VPN service 'pptp' disappeared

If I logout and login again, the VPN works strangely.

Anyone know how I can fix this?

---

