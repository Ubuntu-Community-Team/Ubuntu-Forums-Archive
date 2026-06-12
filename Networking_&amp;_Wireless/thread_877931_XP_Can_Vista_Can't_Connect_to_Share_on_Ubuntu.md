---
title: "XP Can Vista Can't Connect to Share on Ubuntu"
date: 2008-08-02
forum: Networking &amp; Wireless
---

### Post by chrism3568 on 2008-08-02
I have Ubuntu 8.04.1 installed and I've setup a share. My Windows XP box connects to this share fine, I put in the \\ip\share and enter the ID & password. On Vista this does not work, I get a message stating that it can't find the network path. Both machines are connected to the router wirelessly. The Vista machine can see the networked printer (note the printer isn't shared via Ubuntu but has its own Network card).

This seems to be a Vista issue but hope someone has some ideas I can try. I turned of the firewall and protection on Vista, still got the same results.

Thank you,

Chris

---

### Post by chrism3568 on 2008-08-11
OK - this is embarrassing, I forgot at I had the firewall restricting access by IP address. The Vista laptop was new, it was assigned a new IP address and no access. Once I added the IP address to Firestarter I was able to see the shares.

---

