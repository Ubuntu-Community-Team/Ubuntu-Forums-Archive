---
title: "How to add system certificates to all snaps"
date: 2023-12-03
forum: Networking &amp; Wireless
---

### Post by ajkessel on 2023-12-03
I have a VPN certificate in /usr/local/share/ca-certificates/ that is added to the system store in /etc/ssl/certs via update-ca-certificates. But apps installed via snap don't see this certificate and generate an SSL error when accessing https links over VPN. How do I get all snap apps to trust /etc/ssl/certs? 

I've found some related instructions but they seem to be specific to a given app such as the Snap Store ([https://forum.snapcraft.io/t/custom-ssl-certs-for-snapd-to-the-snap-store-communication/17446](https://forum.snapcraft.io/t/custom-ssl-certs-for-snapd-to-the-snap-store-communication/17446)). I'm trying to get this certificate trusted by all apps.

Edited on further research: I think the problem here is actually python certifi, which uses its own cacert.pem. But I don't see how to replace that file in a snap or otherwise get python scripts in the snap to use the system certificate store.

---

