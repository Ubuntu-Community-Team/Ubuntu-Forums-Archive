---
title: "Authenticating using 802.1x on a wired network with machine cert"
date: 2015-02-16
forum: Networking &amp; Wireless
---

### Post by pradeep12 on 2015-02-16
[COLOR=#000000]We have 802.1x configured on the wired ports , and we have an NPS authenticating clients via EAP-TLS. My Ubuntu 14.04 LTS laptop is part of AD and has a certificate which was manually requested from our enterprise CA, and i'm able to connect successfully to the network.[/COLOR]

[COLOR=#000000]If i copy the [/COLOR][COLOR=#000000]keypair and certificate from one machine to another , and modify the identity in wpa_supplicant.conf, im able to connect to the network as another machine , which is a security concern as other machines can impersonate as another and connect  to network. We want only corporate machines with the computer certificate to connect.[/COLOR]

[COLOR=#000000]1) Is there a way we can make the certificate not exportable like in windows?[/COLOR]

[COLOR=#000000]2) Also, is there a way to link the certificate with a unique id like “/var/lib/dbus/machine-id” , so that even if one copies the certificate to his machine it wouldn't work?[/COLOR]

---

