---
title: "Automatic VPN connection script?"
date: 2015-04-01
forum: Networking &amp; Wireless
---

### Post by carlo-1973 on 2015-04-01
Hi everyone, 

I have a question that I'm hoping you may be able to help me with.

I am using a VPN service through NordVPN (a VPN provider). Occasionally they will take servers offline, or issues will arise, and the connection will become unstable. This is simple enough for me to fix, by disconnecting and then connecting to one of the other servers in their pool. My question is, is there a script that I can use to automate this - test if the connection is up/resetting/down, and then connect to another server (randomly is fine or if need be a specific order) to maintain the connection. 

My configuration is a headless Ubuntu Server 14.10. No GUI. 

any and all help appreciated :)

thank you in advance!

---

### Post by Chris_Langdon on 2015-04-02
Hey Carlo,

I need more details. are you using OpenVPN?

---

### Post by carlo-1973 on 2015-04-03
Thanks for the quick reply Chris,

Yes I am actually using OpenVPN. 

NordVPN has .ovpn config files for each of their servers.

Currently I run this manually with the following command:

sudo open&#65279;vpn --config ca2.nordvpn.com.udp1194.ovpn 

Does this help any?

---

