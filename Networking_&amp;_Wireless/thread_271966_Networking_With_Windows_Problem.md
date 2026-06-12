---
title: "Networking With Windows Problem"
date: 2006-10-05
forum: Networking &amp; Wireless
---

### Post by SimonomiS on 2006-10-05
I have a wireless network of three computers, two Windows ones and a Ubuntu one.

The Ubuntu one has internet access but can't seem to ping the other two computers, and they can't seem to ping it either, however they can ping each other.

I don't want to share files on this, so do I not need Samba? How can I get Ubuntu detected in the network?

---

### Post by Mr Frosti on 2006-10-05
When you are "pinging" the machines, make sure that you are pinging the IP address of the machine, and not the machine name. Name resolution is dependant on other processes and is probably where the breakdown is occuring.

If you have no intention of sharing files, then you don't need the Samba packages, however they do allow you to share things such as printers.

---

### Post by SimonomiS on 2006-10-05
No printers either, pinging by internal ip, 192.168.1.100 etc.

---

### Post by SimonomiS on 2006-10-08
Nothing? Not even a link to a basic setting up a Linux/Windows server howto?

---

### Post by Iowan on 2006-10-09
[http://www.ubuntuforums.org/showthread.php?t=202605]("http://www.ubuntuforums.org/showthread.php?t=202605")
If you don't need to share files or printers, does it matter if the machines can't see each other?

---

### Post by SimonomiS on 2006-10-09
LAN Counterstrike Server. Probably should have said that earlier, but the server itself is fine, others can connect to it no problem, it's just getting onto it from another computer in network that's a problem.

Tried connecting through internal ip, at which point I found out the machines can't see each other.

---

### Post by SimonomiS on 2006-10-11
Another question:

Should the IP address I enter for my wlan0 be the internal one or external one?

---

### Post by SimonomiS on 2006-10-14
Could it be something to do with either the Linux firewall (is iptables it?) or a Windows one, since I have one?

---

