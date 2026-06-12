---
title: "Only ping works, rest is death!"
date: 2008-09-04
forum: Networking &amp; Wireless
---

### Post by bimbom on 2008-09-04
From time upgrading to 8.04.1 network disepeared!

WORKING: ping to gate, ping to LAN, ping to both DNS servers, ping to remote (WAN) serwer with name, ping to remote server with IP(so DNS is working)

NOT WORKING: Firefox, any ftp client, "apt-get update" shows updates, but CAN NOT download them

Same on any Live!CD I have put my hand on, same on Fedora
On same hardware and ISP connection with WindowsXP network is doing fine! ISP refuses to react, claim it is my distro problem!

Any body knows what to do?
Few projects, including Open Source translation are freezed.
Help, please!

---

### Post by alpage2 on 2008-09-04
A version upgrade can cause problems for the network adapter, although if you can ping, it suggests that this is working. By being able to ping the WAN, do you mean you can ping machines on the internet?

Try a website or two, such as:

ping -c3 bbc.co.uk

Does that work.

Is it a wired or wireless network? Can you paste the output of ifconfig in a reply, please?

Alan

---

