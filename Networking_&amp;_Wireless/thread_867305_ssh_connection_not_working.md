---
title: "ssh connection not working"
date: 2008-07-22
forum: Networking &amp; Wireless
---

### Post by wiseguyxp on 2008-07-22
I recently reinstalled Ubuntu 8.04 (I upgraded from 7.10, but wanted to do a clean install because my sound wasn't working).  I backed up all of my config files and put them in their respective folders.  I have my ssh set to port 8080, and I have forwarded it to my computer.  When I try to connect on port 8080 (using my external IP), it just sits there and does nothing.  After a while, it will just return me to the terminal prompt with no error message.  I can connect from localhost and hostname within the local network.  When I telnet to test the connection to port 8080 using the external IP, it replies that ssh is running on the port.  So the port is presumably forwarded correctly and set up correctly, so I have no idea what's going wrong.

---

### Post by Bachstelze on 2008-07-23
Try running SSH in verbose mode (i.e. [font="Courier New"]ssh -v[/font]).

---

