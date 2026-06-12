---
title: "WPA2 username and password"
date: 2014-09-09
forum: Networking &amp; Wireless
---

### Post by bkvaluemeal on 2014-09-09
I have an AppleTV that I run Ubuntu server on. I use ndiswrapper to connect to wireless networks. I can connect to networks, but here at college we need to authenticate with a username and password. I can't seem to make that work as I really only know how to work with a pass phrase. How do I connect?

---

### Post by varunendra on 2014-09-11
Sounds like you need to set up a "WPA & WPA2 Enterprise" connection.

In Network Manager (if you are using it), make the "Wireless Security" settings look like the following screenshot :

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=256371&stc=1&d=1410449976[/IMG]

The "CA Certificate" field may be left as (None), but if your school authority uses a certificate for connection, you may have to get it from them and tell this field to use it. Some commonly used CA Certificate files are already available in "/usr/share/ca-certificates/" directory in Ubuntu.

---

### Post by bkvaluemeal on 2014-09-11
I run Ubuntu Server. I don't have a gui. I will research enterprise connections.

---

