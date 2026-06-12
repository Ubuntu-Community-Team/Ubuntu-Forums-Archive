---
title: "recognising computer names"
date: 2008-11-09
forum: Networking &amp; Wireless
---

### Post by chris_tikva on 2008-11-09
I have 3 machines on my network connected to a router. One XP, one vista and one ubuntu. I'm trying to mount samba shares on the ubuntu machine but can only do so by specifying the IP address. If I specify the host name neither ping nor smbmount can find it. However, 'smbclient -L' DOES find it and so does the file browser if I click on "network". I guess there is probably something simple I'm missing. Any help gratefully received.

Chris

---

### Post by Iowan on 2008-11-09
Smbclient and ping use different protocols. The quick/dirty solution is to map IP address to hostname in the */etc/hosts* file - not viable in a DHCP environment.  There are a couple of other programs that should make Ubuntu and Windows talk hostnames - Winbind and making Samba server a WINS server.  Installing *winbind* and editing *nsswitch.conf* might help.  [Here]("http://ubuntuforums.org/showthread.php?t=789444") is a similar thread - [Here]("http://ubuntuforums.org/showthread.php?t=897149") is another.

---

