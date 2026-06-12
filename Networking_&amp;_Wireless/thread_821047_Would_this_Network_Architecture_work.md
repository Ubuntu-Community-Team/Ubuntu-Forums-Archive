---
title: "Would this Network Architecture work?"
date: 2008-06-06
forum: Networking &amp; Wireless
---

### Post by shortcut144 on 2008-06-06
I have a wireless router with internet in Room A

In Room B I have an Ubuntu Web Server with a Wireless antenna. Connected to the Web Server is a small wired network with a router.

Would it be possible to bring internet from Room A to Room B onto the Web Server and have the internet shared with the network? Assuming the of course that the Web Server in Room B connects to the Wireless Router in Room A.



My experience with Web Server's is limited, I am more of hobbyist but I wanna know if this Architecture would work before I start investing hours of trial and error.

---

### Post by PilotJLR on 2008-06-06
This will work if you setup IP masquerade on the server and enable IP forwarding.

If the wired clients need dhcp, then you'll also need a dhcp server on the wired interface of the server. The wired subnet needs to be different from the wireless one!

---

