---
title: "Network Manager Problem"
date: 2007-12-19
forum: Networking &amp; Wireless
---

### Post by pmalvr on 2007-12-19
Hi,
I have Ubuntu 7.10 (Gutsy) and i have some problems with the network manager.
When i have the "Roaming" option selected, everything works, except the fact that every time i restart the computer, it gives me as a dns server, the ip of my router. I don't want this, because it slows my "web surfing" and even if i change the dns servers, when i reboot again i loose them. 
The only way i can allways have my dns servers ip's between restart's, is going to "manual configuration" and remove the option "roaming", but when this appends the network manager doesn't show the bars of the wireless strength.  Can someone help me in this issue?

---

### Post by spd106 on 2007-12-19
You should really modify the router 's DHCP server to provide a different DNS server IP.

If you can't do that for whatever reason then you can also modify your dhcp client to use a different DNS server. Open the /etc/dhcp3/dhclient.conf file and where it says *#prepend domain-name-servers 127.0.0.1;* change this to point to your DNS server and remove the comment marker.

---

