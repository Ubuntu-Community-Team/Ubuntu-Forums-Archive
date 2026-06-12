---
title: "Socket connection refused"
date: 2008-05-20
forum: Networking &amp; Wireless
---

### Post by Jawfish on 2008-05-20
I find with a 7.10 desktop installation and a 7.10 server, that the server will allow socket connections on unallocated port numbers, but my desktop will not. I tried adding a line in /etc/services and rebooting the desktop ( it needed one anyway) but no help. I can connect to known ports like 21 and 445.

myserver# socket mydesktop.me 5020   FAILS "connection refused"
myserver# socket mydesktop.me 445   connects

mydesktop# socket myserver.me 5020 connects

running as root everywhere. Could there be a hidden dns lookup or something thats blocking? dmesg shows zilch.
thanks
John

---

### Post by Jawfish on 2008-05-21
Well I would still like some basic sockets education, but I found the problem with the software I am using, and now it works using sockets through the browser.
John

---

