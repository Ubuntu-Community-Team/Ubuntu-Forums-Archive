---
title: "Network connection dies on its own :("
date: 2007-09-14
forum: Networking &amp; Wireless
---

### Post by LunakO2 on 2007-09-14
My internet connection seems to drop on it own after some time due to No response from the echo requests.

lspi command gave me the following output:
> Ethernet controller: Intel Corporation 82566DC Gigabit Network Connection (rev 02)

> Sep 15 08:24:29 ubuntu-desktop pppd[18446]: primary   DNS address x.x.x.x
Sep 15 08:24:29 ubuntu-desktop pppd[18446]: secondary DNS address x.x.x.x
Sep 15 08:24:39 ubuntu-desktop pppd[29116]: No response to 4 echo-requests
Sep 15 08:24:39 ubuntu-desktop pppd[29116]: Serial link appears to be disconnected.
Sep 15 08:24:39 ubuntu-desktop pppd[29116]: Connect time 3.0 minutes.
Sep 15 08:24:39 ubuntu-desktop pppd[29116]: Sent 18180 bytes, received 569282 bytes.
Sep 15 08:24:45 ubuntu-desktop pppd[29116]: Connection terminated.
Sep 15 08:24:45 ubuntu-desktop pppd[29116]: Modem hangup

Any help appreciated, thankyou.

PS: I am using pppoe to connect to the internet :)

---

