---
title: "[SOLVED] Unable to connect to Network Printer"
date: 2007-12-31
forum: Networking &amp; Wireless
---

### Post by Davehogs on 2007-12-31
Been reading as many posts as I can to try to find a solution yet none of what I have found helps. Have a Canon MP390 printer which I have been connecting directly to my computer ( Ubuntu 7.04) and using the S600 drivers. Was even sharing it with my Windows computer suing my wireless router with the Ubuntu computer acting as a server. Now I have it hooked up to a Netgear PS121NA v2 printer server. Works perfect with my other computer running XP yet I cannot print to it from my Linux computer.  IP address 192.168.1.104 for the printer server. The address pings from the linux computer. Can even access the printer server set up with the Linux computer yet have been unable to print to it. Tried all of the solutions I have read as many have used different approaches yet have gotten absolutely nowhere ... IPP/Cups server , Unix LPD or TCP/Socket . I am stumped. Can anybody walk me through a procedure that will work??

---

### Post by HermanAB on 2008-01-01
Do a simple test with telnet and see what response you get:

$ telnet printserveripaddress 9100

Cheers,

Herman

---

### Post by Davehogs on 2008-01-01
> **HermanAB said:**
> Do a simple test with telnet and see what response you get:

$ telnet printserveripaddress 9100

Cheers,

Herman


Believe it or not I resolved the problem last night. Got into the setup screens and changed it from static to dynamic addressing and then back. Reset the static address back to 192.168.1.104 . Added the printer again as socket://192.168.1.104 and it actually works again using the S600 driver. Forgot to call off the request for help. Thanks for your quick response.

-Dave

---

