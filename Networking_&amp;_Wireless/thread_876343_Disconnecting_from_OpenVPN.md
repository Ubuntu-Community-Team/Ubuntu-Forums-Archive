---
title: "Disconnecting from OpenVPN"
date: 2008-07-31
forum: Networking &amp; Wireless
---

### Post by infinitezero on 2008-07-31
I currently use the CLI command, "sudo openvpn --config ContractorVPN.ovpn", to connect to my clients VPN (OpenVPN) but I can get the connection to terminate unless I reboot. Does anyone know the, " disconnect/kill/stop/don't do that any more", command.

Thanks,
iz


Anyone?

---

### Post by SpaceTeddy on 2008-08-07
you can neither use ctrl+c and cannot kill openvpn from another console via the kill command ?

very strange... never had that before...

---

### Post by AnvarIT on 2012-11-09
> **infinitezero said:**
> I currently use the CLI command, "sudo openvpn --config ContractorVPN.ovpn", to connect to my clients VPN (OpenVPN) but I can get the connection to terminate unless I reboot. Does anyone know the, " disconnect/kill/stop/don't do that any more", command.
Anyone?
Sorry to re'up this old thread but I have the same problem. My server makes connection to an openvpn server (as a cronjob) but when the openvpn server reboots he doesn't close the connection. Did you find a command to close the connection?

---

