---
title: "DNS Settings Change"
date: 2007-03-07
forum: Networking &amp; Wireless
---

### Post by Jsgrabo on 2007-03-07
Ok heres my problem; under system>administration>networking, i click the DNS tab and remove the default DNS servers and then add my own. Everytime i close my browser or change workspaces or restart my computer, the DNS setting go back to the original settings and i have to delete them and enter my own again. Any suggestions?

Thanks

---

### Post by Floppyjoe on 2007-03-07
This link may be of help:

[http://www.opendns.com/start/unix.php](http://www.opendns.com/start/unix.php)

---

### Post by Mr. C. on 2007-03-07
From were are you getting your DNS server IP addresses ?  (your ISP ? )

Are they configured in your router?

How are you getting your IP address? (static / dynamic via DHCP ? )

If via DHCP, then the DNS settings configured in your router would override each time.

MrC

---

### Post by Jsgrabo on 2007-03-07
I have a static ip on this computer and I am using the DNS server that i have always used on my other computers.

---

### Post by Mr. C. on 2007-03-07
Ok, that's some questions answered.

Your DNS server is setup in /etc/resolv.conf.  It will look like:

search yourdomain.com
nameserver 192.168.0.250

You may have up to 3 servers listed.  They are tried in order.  You want the fastest, most reliable one first.

Adding or remove entries there will be reflected in Network Manger.

Closing your browser will not change this file, or changing workspaces will not change this file.

MrC

---

### Post by Jsgrabo on 2007-03-08
ok i edited the resolv.conf file and seems to have solved the problem. thanks for the help!

---

### Post by Mr. C. on 2007-03-08
Excellent!

Best of luck,
MrC

---

### Post by zanglang on 2007-03-10
Hmm, I've noticed that if I use NetworkManager simply changing /etc/resolv.conf won't work, but the OpenDNS link suggests changing /etc/dhcp3/dhclient.conf instead, which works beatifully. Great tip. :D

---

### Post by Mr. C. on 2007-03-10
The file /etc/resolv.conf directs all DNS lookups by the system resolver.  The nameservers listed are used.  The dhclient.conf file is used to configure /etc/resolv.conf when DHCP is used to supply IP information.  Its configuration will override IP and DNS settings each time that client is run.

MrC

---

