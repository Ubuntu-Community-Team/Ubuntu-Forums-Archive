---
title: "Watching Traffic"
date: 2006-12-15
forum: Networking &amp; Wireless
---

### Post by SuperMike on 2006-12-15
I have a very secure environment of two firewalls and a virus scanner on Ubuntu, but something odd happened last night. While I didn't have any application open, my net card was reading and writing bytes on the network in a kind of 0%, 100%, 0%, 100% pattern on the second. I stopped /etc/init.d/networking and the problem went away. I started /etc/init.d/networking and the problem didn't come back. The only things I have running were:

* NTP queries every once in a great while
* Apache1.5 web server
* PostgreSQL database
* MySQL database
* SSH daemon
* SSHFS connection to another Linux system

The virus scanner was not running and neither was freshclam.

Is there a way to figure out what's going on? The 'top' command didn't help. I sort of know the 'lsop' command, but not to determine something like this. Is there any other command I can use?

---

### Post by SuperMike on 2006-12-15
No one has an answer on this? No one is skilled with 'lsof'?

---

### Post by speedman on 2006-12-15
apt-get install jnettop

SM

---

### Post by SuperMike on 2006-12-16
Exactly. Big help. Noticed a server-for-you.de connection, which was odd. That was either an advertisement, Firefox update check, or something from some web page I had open. Or, it was a rootkit! I put this entry in my /etc/hosts file, just in case.

127.0.0.1   server-for-you.de   [www.server-for-you.de](www.server-for-you.de)

---

