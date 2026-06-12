---
title: "ufw configuration question"
date: 2009-10-24
forum: New to Ubuntu
---

### Post by Loki57701 on 2009-10-24
I enabled ufw and set it to default deny, and now I'm wondering if I need to add some rules for everything to work right like imap, smtp, ftp.. or is that just if I was running a server?

---

### Post by Loki57701 on 2009-10-24
Bump

Anyone?

---

### Post by ankspo71 on 2009-10-24
Hi,
You only need to make those rules if you want someone else to connect to your computer (inbound traffic). Those ports you need are all outbound traffic if you are the one initiating them. This is my understanding anyways.
James

---

### Post by Loki57701 on 2009-10-24
That makes sense, thanks.

---

### Post by donato roque on 2009-10-25
You only need to additional rules if you are going to add "server" programs. Like Samba, ftp and such.  If you have a regular desktop with programs that initiate the connection to the internet then you don't have to do anything.  You're set to go.

---

