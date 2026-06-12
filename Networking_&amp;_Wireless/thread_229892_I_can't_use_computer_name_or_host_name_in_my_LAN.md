---
title: "I can't use computer name or host name in my LAN"
date: 2006-08-05
forum: Networking &amp; Wireless
---

### Post by edeaux on 2006-08-05
I have a mandrake 10.0. I used it as MySQL server. I don't have problem with it when it comes to network coz by just providing hostname (dbserver) the server can be pinged (from other pc) by ping dbserver, can connect to MySQL using hostname too and even FTP by ftp dbserver. Now, I installed a server using ubuntu 5.10 and will be used it for MySQL and FTP server instead of mandrake 10.0. The set the hostname as dbftpserver. My problem is can't ping it using hostname (dbftpserver) and also from ubuntu i can't ping other pc using hostname or pc name (Windows XP). Anybody here knows how to fix it?

---

### Post by ylixir on 2006-08-05
you could use bind.  that's kind of a lot of work for a small lan though.  personally, i'm kind of lazy and just use ip addresses for my lan.  that might be the easiest option if you have a small network.

---

### Post by Joeak on 2006-08-05
(Shamelessly cut out of [http://ubuntuforums.org/showthread.php?t=190542](http://ubuntuforums.org/showthread.php?t=190542))

In order resolve each other's hostnames on the local LAN, the Ubuntu machine(s) must be running winbind. This allows an Ubuntu system to send and receive netbios broadcasts for name resolution.  Also, add "wins" to the hosts: line in /etc/nsswitch.conf.

    hosts: files dns mdns wins

This will allow ordinary TCP/IP programs to resolve hostnames with netbios.  I'm not sure if this fixes the problem in the other direction (from Windows machines to Ubuntu).

---

