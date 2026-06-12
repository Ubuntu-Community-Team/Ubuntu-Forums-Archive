---
title: "SSH Permissions?"
date: 2007-07-25
forum: Networking &amp; Wireless
---

### Post by Peter1234123 on 2007-07-25
When I am at home, and I use my internal IP (192.168.1.4) to connect to my server, through SSH, I can connect 100% well. But, whenever I attempt to connect via my external IP, with a different port (Which I correctly added in SSH config)...it tells me that my connection was refused, any advice?

---

### Post by punx45 on 2007-07-25
do you have a router?   you would need to configure it to forward that port to the local IP of your machine.

---

### Post by Peter1234123 on 2007-07-25
Did that xD

---

### Post by punx45 on 2007-07-26
trying to brainstorm a solution...

are you able to SSH over the other port from inside your LAN?

have you been able to operate any other publicly available services on the global IP? (i.e. HTTP, FTP, etc.)
(wondering if the ISP blocks all incoming requests)

---

