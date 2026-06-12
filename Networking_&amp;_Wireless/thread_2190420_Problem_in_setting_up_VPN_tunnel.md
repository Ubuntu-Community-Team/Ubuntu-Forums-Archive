---
title: "Problem in setting up VPN tunnel"
date: 2013-11-27
forum: Networking &amp; Wireless
---

### Post by a.pulvirenti on 2013-11-27
Dear all,

after a long search, I don't find the way to solve my problem.

I needed to set up a VPN client to connect to a remote VPN network with PPTP.
I did this using the network manager.
Since I need to have internet working while being connected to the VPN, I went in the "IPv4" tab, opened the menu "Routes" and checked the box for "use this connection only for resources in its network".
In the main "IPv4" tab I selected Method: "Automativ (VPN) addresses only".

After I did this, when I connect to the VPN, it tells me that connection ws successful, and I do have internet, but I don't manage to connect to the remote machines I should access through the VPN: when I try to do this, either through SSH or by opening a web address specifying their internal IP address, this fails.

Unfortunately, I don't see any other post reporting such a problem and I don't understand what I am doing wrong, or how I can check that the VPN setup is correct or not.

Since I am not expert of VPN and networking, I add this info: the internal address I must use to access those machine is a 10.90.1.* one, which could probably be seen as an internal one, maybe this requires some additional specification in the VPN connection setup?

Thansk in advance for any help.

Alberto

---

