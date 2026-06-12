---
title: "Best way to transfer files"
date: 2007-09-27
forum: Networking &amp; Wireless
---

### Post by as2003 on 2007-09-27
Hello everyone!

I'm trying to transfer files from an XP laptop (running the Ubuntu live cd) to an Ubuntu desktop.

As far as connectivity is concerned, the laptop is wireless enabled, has a usb port and an ethernet port.
The desktop has a usb socket, usb wi-fi and an ethernet socket.

So, for the physical connection, do I get a usb cable or a twisted-pair ethernet cable or try the wireless route?

Secondly, how would I transfer files across a usb link? Perhaps I should use samba? How about running an ftp server? Is there an ftp server on the live cd? Are there other options?

Thanks for any help!
Aidan.

p.s. I can't plug the laptop's HD into the desktop because it's SATA, and the desktop is keeping things old skool with IDE.

---

### Post by peitschie on 2007-09-27
Hiya,

Since both computers have wireless networking, that might be the best way to go.  To setup a wireless network see here [https://help.ubuntu.com/community/WifiDocs/Adhoc]("https://help.ubuntu.com/community/WifiDocs/Adhoc").

Samba would be the easiest for transferring.  I would recommend that you share the folders from the XP side, and then browse via the network (Places > Network) to the computer.

---

### Post by as2003 on 2007-10-08
Thanks for the reply! I had a bit of trouble setting up the wireless link, but I got my hands on a crossover cable and used that!

Thanks for the response.

---

