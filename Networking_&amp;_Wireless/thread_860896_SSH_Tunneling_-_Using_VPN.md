---
title: "SSH Tunneling - Using VPN"
date: 2008-07-16
forum: Networking &amp; Wireless
---

### Post by prakharv on 2008-07-16
Hi All,

We need to access Our Local Machine Globally, for that we need to create a VPN(Virtual Private Network) using Linux Machine.

Scenario: 

1)Global User, trying to access Machine using Internet, visible to global user, then that machine should be able to access Local Machine.

Basically, we need to create a SSH Tunnel between Global Machine and local machine,

Global Machine should be able to send request to Global Machine and Remote Machine should forward the request to Local Machine at some Port.

You can say it as Port Forwarding also.

Please, help me out how to forward the request generated at global machine to local machine using Tunnel.

Regards,
Prakhar

---

### Post by dmizer on 2008-07-16
check this howto: [https://help.ubuntu.com/community/SSH_VPN?](https://help.ubuntu.com/community/SSH_VPN?)

---

