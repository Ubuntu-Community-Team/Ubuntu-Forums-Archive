---
title: "Firefox can't connect to the internet"
date: 2007-07-13
forum: Networking &amp; Wireless
---

### Post by John Melbourne on 2007-07-13
I've just set set up an old computer with my first LINUX OS ( Ubuntu 5.10) hoping to try it out.  The computer is attached to a home network with a broadband router and three other computers all running windows. I've eventually got the LINUX system up and running after various problems with the very old BIOS and video card but I can't get firefox to link to any internet site. All I get is a long wait then either "Timed out"  or "Connection refused"

Ubuntu can see and communicate with the other computers on the network and firefox can link to the admin interface of the router so DHCP and the network interface are all fine. Using Terminal, i can Ping Google.com, getting an immediate response so, I can get out via the router and, presumably, connect to a DNS somewhere.

I've even tried getting firefox to connect direct to the IP address returned by the ping but to no avail though it worked fine from another machine on the network.

---

### Post by mips on 2007-07-13
Disable IPv6

---

### Post by John Melbourne on 2007-07-14
Brilliant!     It now works OK.


Thanks very much.

---

