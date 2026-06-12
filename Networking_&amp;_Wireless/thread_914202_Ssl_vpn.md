---
title: "Ssl vpn"
date: 2008-09-08
forum: Networking &amp; Wireless
---

### Post by bwaskiew on 2008-09-08
Greetings,

At work, we have a *Firebox SSL VPN Gateway* installed that allows us to securely connect to the network from home. It has a Linux client, but it doesn't work, and the product has been discontinued.

I am kind of expecting the worst here, but I figure I will ask the experts anyway:

Is there an open protocol for SSL VPNs? That is to say, could I swap something like OpenVPN as my client, and just configure a few settings (certificate, IP, domain, etc.) and connect from the OpenVPN client to the Firebox SSL VPN Gateway host?

I looked briefly at some of the OpenVPN release notes and FAQs, and there seems to be issues connecting between different versions of OpenVPN itself, so I would assume that connecting across a different SSL VPN solution would just not work.

If it won't work, are there any alternatives I could try? I probably don't have to say this to everyone here, but it is awfully frustrating to have to reboot into Windows, or start a Windows virtual machine.

I could try bugging their support constantly until they decide to update their Linux client :)

Thanks,
Brandon

---

### Post by d.donald on 2009-03-22
Hi Brandon,

I've encountered the same problem and I've just solved it yesterday by connecting simply using the openvpn client.

The Watchguard Firebox I connect to use SSL.

Abstract:

Install if necessary openvpn package (client)

Retrieve necessary files to use the following openvpn command.
It is easier to start from a Windows PC on wich the official Watchguard SSL client is already installed and works. You must then copy files generally stored in C:\Documents and Settings\*username*\Application Data\WatchGuard\Mobile VPN\ : **ca.crt, client.pem, client.crt, client.opn**

When you open a terminal in the folder containing the copied files you can just launch this command:

**sudo openvpn --config client.ovpn**

You will have to answer for username and password (of course, these are the same than with the Windows client) and it (must) works !

To end connexion, a CTRL+C is enough.

I hope this can help some Ubuntu users because my last searches for this issue hadn't had been very fertile.

---

