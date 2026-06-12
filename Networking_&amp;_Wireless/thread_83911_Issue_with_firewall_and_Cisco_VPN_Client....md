---
title: "Issue with firewall and Cisco VPN Client..."
date: 2005-10-29
forum: Networking &amp; Wireless
---

### Post by shadow07 on 2005-10-29
Can anyone shed some light as to why I'm having this problem?

the official Cisco VPN client is working just perfectly fine on my machine.  BUT, with the firewall enabled, I cannot access any machines on the remote network.  Not until I disable the firewall.

Is there something I can tweak on the built-in firewall to get beyond this problem?

When I have the vpn established, and I ping a host on the remote network, I get the following for every PING attempt:

ping: sendmsg: Operation not permitted

Thanks for any input or advice.

---

### Post by mlomker on 2005-10-29
I had the same problem.  I even [found some instructions]("http://www.fs-security.com/docs/vpn.php") on Firestarter's website for working around the issue.  I gave up and removed firestarter before I figured that one out.  I have a hardware firewall at home, anyway.

---

### Post by shadow07 on 2005-10-30
Thanks for your reply.  Based on the link, I took the solutino for OpenVPN, and just substitued "tun+" with "cipsec0".  I restarted the firewall, then established my VPN connection, and it works now.

---

