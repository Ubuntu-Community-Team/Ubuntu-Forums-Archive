---
title: "Changing samba connection with new network card"
date: 2013-10-10
forum: Networking &amp; Wireless
---

### Post by bav2 on 2013-10-10
I've been using my on-board lan to share files across my network with samba. It recently died  though so I purchased a new card and assigned it the same static IP address as my old one, but non of my windows devices can connect. I get the "windows cannot access ..." error. Am I forgetting to change some settings since everything is now using eth1 instead of eth0? I changed that in my smb.conf file but still nothing.

---

### Post by bav2 on 2013-10-11
I was able to change my new NIC's name to "eth0" but I still can't connect with any of my windows computers. My android tablet will connect just fine.

Edit: I got it to connect by typing \\"ip address of server" instead of \\"name". I'm not sure what that means though as to why it can't find the server by name

---

