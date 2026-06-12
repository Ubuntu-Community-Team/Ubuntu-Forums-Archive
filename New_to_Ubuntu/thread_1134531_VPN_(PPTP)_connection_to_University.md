---
title: "VPN (PPTP) connection to University"
date: 2009-04-23
forum: New to Ubuntu
---

### Post by Cape on 2009-04-23
I'm trying to connect to my university network using the network manager after I installed the packages listed here:

[https://wiki.ubuntu.com/VPN](https://wiki.ubuntu.com/VPN)

I am able to connect from my windows machines, but I've had no luck with the ubuntu network manager. Unfortunately the university only has Mac and Windows instructions for configuring (for everything else it has the holy trinity), but as you will see from the instructions linked below for configuring for windows XP it seems pretty standard for vpn configuration.

[http://www.york.ac.uk/services/cserv/net/vpn/help/vpnxp.html](http://www.york.ac.uk/services/cserv/net/vpn/help/vpnxp.html)

I create a PPTP vpn profile where I fill in my user name, password, and the gateway (vpn.york.ac.uk). However, when I select the profile for connecting I either get no visible activity or have a short wait before a prompt that says the connection failed (not sure of the exact wording).

Can anyone help?

PS: ignore the proxy configuration of page 2 of the XP instructions - that is optional so you can access certain extra services on the university network - but is not a requirement for the initial connection.

---

### Post by j_zhill on 2009-04-23
You might be having the same problem as I did when trying to connect my uni's VPN. After contacting the network admins, it turned out that their PPTP VPN required 128-bit point-to-point encryption. The MPPE (point-to-point) checkbox is unchecked by default - you can enable it by going to:

network connections > VPN tab > edit > advanced... button

In the advanced settings dialogue box, check "Use Point-to-Point Encryption" and set the security option to "All Available".

Give it a shot and let me know how you go.

---

### Post by j_zhill on 2009-04-23
The next thing you might try would be to contact your admin and ask them to look up the connection history for your account - any more info from the server side of connection would be helpful.

You could also take the opportunity to bug them about providing directions for ubuntu on their VPN support page :) Not that I've had any luck with the UWA tech support guys...

---

