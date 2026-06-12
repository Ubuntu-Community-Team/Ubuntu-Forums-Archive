---
title: "errors with isc-dchp"
date: 2021-05-28
forum: Networking &amp; Wireless
---

### Post by ulao3 on 2021-05-28
I noticed my dhcp was down today and I'm getting this error. 


running
root@ubuntuspawn:~# systemctl status isc-dhcp-serversystemctl status isc-dhcp-server

I get
Unit isc-dhcp-serversystemctl.service could not be found.
Unit status.service could not be found.
&#9679; isc-dhcp-server.service - ISC DHCP IPv4 server
   Loaded: loaded (/lib/systemd/system/isc-dhcp-server.service; enabled; vendor preset: enabled)
   Active: failed (Result: exit-code) since Fri 2021-05-28 16:27:22 UTC; 3min 55s ago
     Docs: man:dhcpd(8)
  Process: 6707 ExecStart=/bin/sh -ec      CONFIG_FILE=/etc/dhcp/dhcpd.conf;      if [ -f /etc/ltsp/dhcpd.conf ]; then
 Main PID: 6707 (code=exited, status=1/FAILURE)


I'm not sure what I may have done to cause this.

---

### Post by bls3427 on 2021-05-31
I saw this after I posted my question ([https://ubuntuforums.org/showthread.php?t=2462984](https://ubuntuforums.org/showthread.php?t=2462984)).

Can you look in your log and see what the specific error is? Is it "Can't clone pool group"?

---

