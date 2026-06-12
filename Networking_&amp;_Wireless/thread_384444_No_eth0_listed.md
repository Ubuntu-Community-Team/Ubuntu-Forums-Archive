---
title: "No eth0 listed"
date: 2007-03-14
forum: Networking &amp; Wireless
---

### Post by Netspeed on 2007-03-14
I had the network working yesterday perfectly. Now today it doesn't work. I ran ifconfig -a and all it shows is "lo". It doesn't list "eth0". How can I fix this?
Also, the LAN is built into the mobo...ESC P4M800Pro

---

### Post by Strider on 2007-03-14
Check your /etc/network/interfaces file to see if eth0 is listed.  Also, run "dmesg" and look for the ethernet card being detected or run "lspci" to see if the card was found.

If the card is not listed in /etc/network/interfaces, it will not come up.

-Mike

---

### Post by Netspeed on 2007-03-14
I ran the /etc/network....command and it said:
auto eth0
iface eth0 inet dhcp

Dmesg came back with a ton of stuff but I don't know what to look for.

lspci didn't show any ethernet installed (it's part of the mobo).

I tried loading the setup CD for the mobo but how do I load mainly windows-based drivers in a Linux environment?

Thanks for the help BTW

---

### Post by Netspeed on 2007-03-14
I figured out that I need WINE to load the drivers but I can't apply it because I have no network connection.

---

