---
title: "WPA2 ENT users incorrectly sharing 802.1x credentials"
date: 2020-08-30
forum: Networking &amp; Wireless
---

### Post by richardi99 on 2020-08-30
I have one Ubuntu 20.04 client, which has two user accounts.  Wifi network uses WPA2 ENT PEAP.  Each user has unique radius credentials.  Radius assigns each user to a different vlan.  DHCP is in use - no fixed IPs

Instead of each client user account authenticating with their credentials, the radius credentials seem to be shared between ubuntu accounts.  This is incorrect and a security issue for me.

So, for example:
Adam logs onto the client, and enters his radius credentials to access wifi.
Bob logs onto the client, and is not asked for his radius credentials. Instead, he is already authenticated using Adam’s.

To complicate things till further, changing credentials causes network issues. For example:
In the above scenario, if Bob then goes Into Wi-Fi settings, and changes the security credentials to match his radius credentials, he is assigned a correct IP address, but the client still tries to use the old default route, which means he has no Internet access.  The client retains the default route relating to Adams subnet; even though IP settings are assigned by DHCP.  I can see no way of manually changing the default route in Wi-Fi settings.

Hosts file holds no relevant information.

Am I doing something wrong?

---

