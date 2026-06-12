---
title: "eth0 up, but no websites load or pings return"
date: 2007-03-22
forum: Networking &amp; Wireless
---

### Post by weijie90 on 2007-03-22
Hi,

I just got a dell inspiron 6400, with the wired LAN Broadcom 440x card.

when i plug in to my office network, dhcp seems to connect, but when i try to surf in firefox, it does "looking up www.site.com" and then hangs at Connecting to...

When i do a ping [www.google.com](www.google.com), the output shows its IP address. However, no pings are returned, 100% ping loss.

The most surprising part is that Samba works perfectly. I can read and write to the office fileserver.

Please help.. Thanks!

---

### Post by ffxr on 2007-03-22
sounds like DNS..

try adding your DNS servers manually in the network control applet ..

or even use the opendns servers.. by adding 208.67.222.222 & 208.67.220.220 to your dns server list .. [http://opendns.com/](http://opendns.com/)

---

### Post by MrCheese on 2007-03-22
If you are getting an adress for the sites you are pinging then dns is resolving ok.

Check that eth0 is set to default gateway in your networking setup

see if you can access anything on your side by address (eg if you have a broadband router, try accessing the router config page) if this works your basic networking is working ok.

---

### Post by weijie90 on 2007-03-22
Thank you! OpenDNS works!!

Productivity decreases in 3.. 2... 1....

---

