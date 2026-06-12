---
title: "UFW Firewall Setting"
date: 2021-01-30
forum: Networking &amp; Wireless
---

### Post by zergling on 2021-01-30
Hello Everyone,
I am a novice when it comes to setting up a firewall in Linux... 
So, what I would like to achieve is to force all my traffic through VPN/Wireguard using the ufw firewall and when the VPN/Wireguard is down, I want the firewall to stop all my traffic IN/OUT.
How would I accomplish this?

---

### Post by TheFu on 2021-01-30
I don't think ufw can do that. It is the "uncomplicated" fwall at the expense of fewer features.

Use iptables to block all traffic that isn't over the tunnel interface or lo interface.

---

