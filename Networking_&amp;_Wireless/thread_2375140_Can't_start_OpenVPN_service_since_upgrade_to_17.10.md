---
title: "Can't start OpenVPN service since upgrade to 17.10"
date: 2017-10-22
forum: Networking &amp; Wireless
---

### Post by trolley on 2017-10-22
I had OpenVPN configured to start as a systemd service on 17.04 but since upgrading to 17.10 it no longer works. systemctl gives the error:

```

user@ubuntu:/etc/openvpn $ sudo systemctl start openvpn@vpn.service
Failed to enable unit: Unit file openvpn@vpn.service does not exist.

```

My OpenVPN config file still exists in /etc/openvpn with the same name it had before:

```

user@ubuntu:/etc/openvpn $ ls
ca.crt  vpn.conf  client.crt  client.key  update-resolv-conf

```

Listing my service unit files only shows one entry and it's state is "masked" which I don't know the meaning of:

```

user@ubuntu:/etc/openvpn $ systemctl list-unit-files --type=service | ag 'openvpn'
openvpn.service                            masked

```

EDIT:
I searched for "masked" and found how to unmask, so now it shows:

```

user@ubuntu:~ $ systemctl list-unit-files --type=service | ag 'openvpn'
openvpn.service                            generated

```

That's no more helpful though.

Let me know if there's anything else I can post that would help.

EDIT 2:

Turns the openvpn package was removed by the upgrade and just needed to be reinstalled. It didn't even occur to me that it could be gone.

---

