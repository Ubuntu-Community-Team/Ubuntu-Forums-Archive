---
title: "Updating DNS server to use when connecting to wireguard"
date: 2024-05-25
forum: Networking &amp; Wireless
---

### Post by sniper8752 on 2024-05-25
I added the following to my [interface] section in my wg-conf:
`PostUp = resolvectl dns %i 192.168.1.2#192.168.1.2; resolvectl domain %i ~
DNS = 192.168.1.2`

Yet my system still defaults to 9.9.9.9.  The systemd-resolved.service service is running.

---

### Post by ActionParsnip on 2024-05-26
If you restart the systemd.resolved service after the VPN comes up does it help? Personally I have a script that bring up my VPN then updates the resolv.conf file as I desire.

---

### Post by sniper8752 on 2024-05-26
> **ActionParsnip said:**
> If you restart the systemd.resolved service after the VPN comes up does it help? Personally I have a script that bring up my VPN then updates the resolv.conf file as I desire.

It doesn't look like I have that installed.

---

