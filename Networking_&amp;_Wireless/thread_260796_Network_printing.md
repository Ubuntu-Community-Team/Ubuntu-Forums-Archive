---
title: "Network printing"
date: 2006-09-19
forum: Networking &amp; Wireless
---

### Post by Alessandro Allegri on 2006-09-19
Hi everybody. I need some advice about network printing.
I have 2 ubuntu boxes, the printer (Epson Stylus-C46) is USB-ed to one of them. Locally it works. I followed several different howtos and I installed the same printer via cups (ipp) on the second machine, but it won't print.
All I am able to do is to send the test page from the client to the server: the printer jobs screen on the server machine shows the job for a second and then it makes it disappear as if the job was completed, which is not the case.
I imagine this means that the firewall is pierced through but there's still something on the server that is not set up properly. Could it be the permissions on the cups thing? I don't know how to set these, actually.
The server machine's ip is 192.168.1.4, the client's 192.168.1.2 and they are connected through a router, gateway 192.168.1.1 mask 255.255.255.0.
The allowed users on the server's cups page are:
192.168.1.2/24,
192.168.1.4/24,
192.168.0.0/24,
serveruser,
clientuser
Accessing the server's cups page remotely from the client's browser is possible and so is sending the test page request, providing the serveruser name and password.
So... what's wrong?!?
Thanks everybody for any kind of help!

---

### Post by tagra123 on 2006-09-19
CUPS is still broken as far as I can tell. I wrote a simple how to about how to use samba (which works) to accomplish the same thing.

[http://ubuntuforums.org/showthread.php?t=245052](http://ubuntuforums.org/showthread.php?t=245052)

---

### Post by Alessandro Allegri on 2006-09-20
Works like a charm! Great HOWTO, thanks!

---

### Post by tagra123 on 2006-10-01
You are welcome.

---

