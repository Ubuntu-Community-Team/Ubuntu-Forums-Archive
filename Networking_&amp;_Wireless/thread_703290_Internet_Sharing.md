---
title: "Internet Sharing"
date: 2008-02-21
forum: Networking &amp; Wireless
---

### Post by raiXer on 2008-02-21
Just yesterday I linux to my internet server and I had it all setup pretty with firestarter and ndiswrapper to make my usb wireless device work. It shared the connection and also had connection for itself. So I left it do the ubuntu updates overnight and then when I restarted to let it update the kernel I noticed that it still share internet connection as always but the server itself can't access any websites or connect anywhere.
In other words.. the workstations can access the internet throu the server but the server itself can't access any websites.

help?

---

### Post by raiXer on 2008-02-21
nevermind. I found the problem.
Figured that it was the dns info. I didn't have it set on the server but I did have it set on the clients

just added 'dns-nameservers ' commands to the /etc/network/interfaces   and restarted the networking service

---

