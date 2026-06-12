---
title: "Wpa2/mschapv2 network"
date: 2014-04-22
forum: Networking &amp; Wireless
---

### Post by valters on 2014-04-22
Hello.
I`m experiencing some problems with the latest Ubuntu LTS 14.04. I`m trying to connect to eduroam (witch uses wpa2/mschapv2), the problem is that even if i choose to connect to the network without the certificate file, it seems to keep asking for it and thus not connecting.

 TLS: Certificate verification failed
wlan0: CTRL-EVENT-EAP-TLS-CERT-ERROR

The only solution that i know at this moment is to manually edit the /etc/NetworkManager/system-connections/eduroam file and set system-ca-certs=false, but the problem is that i have to do it every time i restart my computer. 

Maybe someone has a better idea what could be wrong?

---

### Post by valters on 2014-04-23
Got the certificate for the network and now i can connect to the network without disabling the verification. But the question still remains, why does it still request the certificate if you choose to ignore it?

---

