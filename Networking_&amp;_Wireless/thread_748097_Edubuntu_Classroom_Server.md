---
title: "Edubuntu Classroom Server"
date: 2008-04-07
forum: Networking &amp; Wireless
---

### Post by helives95 on 2008-04-07
I want to boot up Edubuntu like a classroom server. Etc, each student having their own account. I tried boot to LAN, but that just doesn't work.

P.S This is not a classroom server, but it has the same principle.

---

### Post by J-Ram-z on 2008-04-09
Hi:
I'm running Edubuntu 7.10 at a school with thin clients in several rooms. I'm still a little on the new side, but I have some experience. What is your actual question?

---

### Post by helives95 on 2008-04-09
How do I do a DHCP boot, (boot to LAN in BIOS) so I can boot off of one computer, and have all the other computers booting off of that. 

EXAMPLE

One computer has all 500 student accounts

All 30 computers boot off of that to access their account, games, etc.

---

### Post by maybeway36 on 2008-04-14
Make the server (with the accounts on it) be 192.160.0.1 on a private network connecting it to the clients, and have the server (NOT the clients) connect to the Internet on another interface.

---

