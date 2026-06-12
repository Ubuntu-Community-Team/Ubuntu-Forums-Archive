---
title: "Mount SMB Share over VPN"
date: 2008-07-27
forum: Networking &amp; Wireless
---

### Post by RMOP on 2008-07-27
I've posted about this before, but with no replies, so thought I'd give it another try with more detail. Yes, that makes for a redundant post, but I'm sure SOMEONE in Ubuntuland knows how to work this. I'm looking for guidance.

I have several SMB shares on my XP machine at home. When my Ubuntu eeePC is connected via WiFi to my home network, the desired shares automount w/o a hitch. I'd like to have something similar happen when I connect to my XP machine over a PPTP VPN. I can establish the VPN, but can't mount the SMB shares.

Here's the situation:
1) Ubuntu 8.04 with latest updates
2) Ubuntu->XP PPTP VPN connects readily and actually (I've had someone actually verify on the XP machine that the expected connection is established).
3) My Palm TX->XP PPTP VPN also connects easily, the difference being that my Palm allows me to mount XP shares and move files and/or Hotsync over VPN.
4) I conclude that my VPN is setup just fine, but that I'm ignorant about making Ubuntu "see" the SMB shares over this connection.
5) Home router gateway is 192.168.1.254 (odd, I know -- blame O2)
6) Remote router gateway is 192.168.1.1
7) With the VPN running, and using Places->Connect to Server and filling in the requested info yields a "Cannot Mount..." message.
8) If, while connected to my HOME WiFi network, I try to establish the same VPN connection between Ubuntu and XP, it actually connects (evidently Loopback is enabled on my home router?). If I try then the same Places->Connect to Server routine, the SMB share actually mounts and appears as a networked folder on my Ubuntu desktop.

VPN Network Route specified on my Ubuntu VPN is 192.168.1.0/24

THIS may or not be an issue. Both routers assign an address of 192.168.1.xxx to their respective computers. Meaning, the Ubuntu and XP machines have the same internal IP address on their respective networks. Which makes me wonder if there is some confusion when I try to mount an SMB share on an XP machine having the identical (internal) IP address as the remove Ubuntu machine. Shouldn't matter, I don't think, but I don't know for sure.

Assistance would be most appreciated. I'm clearly stuck.

Many thanks.

---

