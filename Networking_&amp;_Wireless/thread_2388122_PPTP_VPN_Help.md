---
title: "PPTP VPN Help"
date: 2018-03-28
forum: Networking &amp; Wireless
---

### Post by AlexBryan on 2018-03-28
Hi all,

I posted this on the security forum but it might actually be more suitable here.

I'm running a new install of Ubuntu 16.04 and trying to get a VPN up and running. I've followed [this guide]("https://support.purevpn.com/pptp-configuration-guide-for-ubuntu"), and everything seems to have worked fine and the VPN has successfully connected, but when I go to whatismyipaddress.com, it's still showing my normal IP address and location. 

Below are route -n results with and without the vpn connected. I have no idea what I'm looking at here to be honest, but hopefully someone will be able to see what the problem is?

Without VPN:
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0            192.168.0.1     0.0.0.0         UG    600    0        0 wlp2s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlp2s0
192.168.0.0     0.0.0.0         255.255.255.0   U     600    0        0 wlp2s0

VPN connected:
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         0.0.0.0         0.0.0.0         U     50     0        0 ppp0
0.0.0.0         192.168.0.1     0.0.0.0         UG    600    0        0 wlp2s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlp2s0
188.72.118.3    192.168.0.1     255.255.255.255 UGH   0      0        0 wlp2s0
188.72.118.5    0.0.0.0         255.255.255.255 UH    50     0        0 ppp0
192.168.0.0     0.0.0.0         255.255.255.0   U     600    0        0 wlp2s0
192.168.0.1     0.0.0.0         255.255.255.255 UH    600    0        0 wlp2s0

Any help would be much appreciated!

---

### Post by TheFu on 2018-03-29
PPTP and security doesn't compute.  PPTP has been hacked since 2005 and tools to totally hack it have been available since 2012 for anyone to run.

PPTP is only useful when you don't need security.

[https://rfsp.blogspot.com/2016/11/hacking-any-pptp-vpn-in-3-minutes.html](https://rfsp.blogspot.com/2016/11/hacking-any-pptp-vpn-in-3-minutes.html)
[https://www.computerworld.com/article/2505117/cyberwarfare/tools-released-at-defcon-can-crack-widely-used-pptp-encryption-in-under-a-day.html](https://www.computerworld.com/article/2505117/cyberwarfare/tools-released-at-defcon-can-crack-widely-used-pptp-encryption-in-under-a-day.html)
[https://docs.microsoft.com/en-us/security-updates/SecurityAdvisories/2012/2743314](https://docs.microsoft.com/en-us/security-updates/SecurityAdvisories/2012/2743314)

You may have a great reason for using PPTP, which is perfectly fine. Just felt it was important to note the security issue.

Please wrap text output in code tags so it lines up correctly. That's Adv Reply (#).

---

### Post by AlexBryan on 2018-03-31
Thanks for the reply, I wasn't aware PPTP wasn't secure. I've switched to OpenVPN (hopefully that's a more secure option?) but the problem persists.

Basically the result I want is when I enable the VPN, all internet traffic should be routed via that VPN connection. I've only used VPNs on Windows machines before, and that's always been the default behaviour, but in Ubuntu, when the VPN is connected, my browser traffic appears to be bypassing the VPN. I've Googled and have found a number of references to this issue, but the fixes suggested either don't work, or are for older versions for Ubuntu and the settings no longer exist, or aren't explained in granular enough detail for a relative novice like me to understand.

I'm hoping this is a quick fix, so if someone wouldn't mind hand-holding me through the steps required to force Ubuntu to push all internet traffic through the VPN when it's connected, I'd be very, very grateful!

Cheers, Alex

---

### Post by TheFu on 2018-03-31
Please post your vpnserver.conf (no comments) from the server and the ovpn settings for the client.
Also the output from **route -n** when the VPN is active from a location on a different subnet than the openvpn server.

Glad you stopped using PPTP. Please share this knowledge.  Friends don't let friends use PPTP, plain FTP, telnet, or nc.

---

