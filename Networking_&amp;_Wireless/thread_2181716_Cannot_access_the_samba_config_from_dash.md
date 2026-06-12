---
title: "Cannot access the samba config from dash"
date: 2013-10-18
forum: Networking &amp; Wireless
---

### Post by Mick8882003 on 2013-10-18
I am trying to get ubuntu (13.04) to share a file with my new laptop runing w8, I cannot bring up the samba config file in ubuntu.
I was working though this guide: [http://www.liberiangeek.net/2013/04/enable-file-sharing-between-windows-8-and-ubuntu-13-04-raring-ringtail/](http://www.liberiangeek.net/2013/04/enable-file-sharing-between-windows-8-and-ubuntu-13-04-raring-ringtail/)

Any tips?

Mick

---

### Post by houstonbofh on 2013-10-18
Which direction are you trying to connect?  From the file browser (nautilus) you can click File, and Connect to Server, and connect to your Windows box if sharing is enabled.

---

### Post by bobblex on 2013-10-20
What do you get when you do the following in the terminal?

> sudo smbd -b | grep smb.conf

---

