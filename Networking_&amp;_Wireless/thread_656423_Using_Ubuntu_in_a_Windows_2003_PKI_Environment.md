---
title: "Using Ubuntu in a Windows 2003 PKI Environment?"
date: 2008-01-02
forum: Networking &amp; Wireless
---

### Post by Modeverything on 2008-01-02
Hi guys,

I think this is the correct forum to post this question in.

We have a Windows 2003 environment, using Microsoft's PKI solution for all of our certificates.  We also use 802.1x LAN (not WAN) based authentication using the certs from our PKI to authenticate to our Cisco switches.  The certs get handed to other Windows clients via Group Policy.  The certs are Computer certs issued to the machines, not User certs.

What I would like to know, is there a way to install a Computer certificate from a Windows 2003 server onto an Ubuntu client and have it authenticate using 802.1x?

The client would not only have to have the cert, but be able to communicate using EAPOL and know to present it's cert for authentication.

Thanks!

---

