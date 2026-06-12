---
title: "(K)Ubuntu 20.04 completely ignoring VPN connection"
date: 2020-04-28
forum: Networking &amp; Wireless
---

### Post by Mr. Swiveller on 2020-04-28
I was wondering if someone might have run into the same issue as I have and/or have a solution to this problem.

When I start a VPN connection a Tun0 (OpenVPN) or 'wgivpn' (WireGuard, provided by IVPN) interface is enabled, yet internet-enabled programmes such as Firefox and Falkon completely ignore it, and use my regular connection instead: Google is displayed in my local language rather than that of the country I am connecting to, and can accurately tell me where my ISP is located.

I have tried both the IVPN CLI interface and the KDE networks GUI, with network-manager-openvpn installed. Wireguard, too, is installed.

This is a completely fresh Kubuntu 20.04 install - not an upgrade from 19.10, which I used previously. I've never run into this problem before, so I am not sure how to proceed.

---

### Post by SeijiSensei on 2020-04-28
I can't tell from reading this whether you expect opening the OpenVPN client alone should be enough to get you a VPN or not.  There needs to be a server upstream from you on the public Internet to which you can connect and create the tunnel. 

If you have such a setup already, then your routing table probably isn't set up correctly.  That's a bit tricky, so lets start with the first issue.  When you run the OpenVPN client do you connect to an OpenVPN server? What IP address do you get for tun0 on each end?

---

### Post by Mr. Swiveller on 2020-04-28
Many thanks for your reply!

I was typing an answer to your questions when I noticed that some sites did, in fact, accept the geographic location of the VPN server instead of that of my ISP. My working theory is that our internet provider has enabled IPv6, resulting in an IP leak. In any case, it is clear that my original assumption was wrong.

EDIT - yes, it's an IPv6 leak. A bit annoying, as I sometimes need to check how websites look outside of my own country, but it's something I can work around.

---

### Post by parrins on 2020-05-08
Some VPNs have special addons in order to prevent IP leakages. Try several other options, [cooltechzone]("https://cooltechzone.com/vpn-reddit") has a list the most popular ones.

---

