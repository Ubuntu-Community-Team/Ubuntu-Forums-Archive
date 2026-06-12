---
title: "Setting Network Connections Mgr. Correct for FTP Server"
date: 2008-01-12
forum: Networking &amp; Wireless
---

### Post by dbsoundman on 2008-01-12
I've been working on setting up an FTP server on my Ubuntu 7.04 desktop with proftpd. Everything is bunnies and sunshine when I connect to the FTP server on that same computer, using the "ftp localhost" command, but I can't even connect to it from another computer within my home network otherwise. What I get is a prompt for username and password, then it says that the login for that user failed, or something of that sort. I am using the "external" IP address to access it (meaning the IP address of the modem and not the router), but I don't think that's the issue, as I have forwarded all the appropriate ports as far as I know on those devices. I'm wondering if maybe I have messed something up in the network connections manager, in the hosts list, and that is why it isn't working. I have attached a picture of the manager window. I changed the "blackdiamond" host to the IP static IP address of the computer/server as given by the router, rather than the default it was set to, 127.0.0.1 I think, because with that set that way gproftpd wouldn't even start. So now, it starts, and I can connect to the server on the server, but not from anywhere else. What have I done/can I do?

Thanks,
Dan

---

