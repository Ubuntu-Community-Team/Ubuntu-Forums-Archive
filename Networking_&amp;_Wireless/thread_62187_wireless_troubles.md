---
title: "wireless troubles"
date: 2005-09-03
forum: Networking &amp; Wireless
---

### Post by blade_II on 2005-09-03
Hi i'm using a compaq armada m700 laptop, i have an atheros airlink 101 wireless card, i used iwconfig to configure it to my network, when i check iwconfig ath0, i get the correct wep key, and essid, i then checked the connection properties in ubuntu, it showed ath0 connection status as idle 17 received packets and 42 sent, signal strength at 85%, now when i try to goto [www.google.com](www.google.com) to check it, it says "www.google.com" cannot be found.  not sure what i'm doing wrong here, any help will be much appreciated, let me know if you need any outputs or anything pasted here, thanks again..    ](*,)

---

### Post by 0vermind on 2005-09-03
yes, like you said I would like to see some outputs first then I'll see waht I can do!!

Mike

---

### Post by tictoc on 2005-09-03
Sounds like you haven't specified the DNS for your ISP.
If using a router, they generally acquire them and pass them on to the OS but I've had to manually config them on a few occasions.
I'd go to your ISP's help page and find the DNS and input them manually. Once you have the server IPs try:
```
sudo network-admin
```
DNS tab for your interface>enter the servers>OK

---

