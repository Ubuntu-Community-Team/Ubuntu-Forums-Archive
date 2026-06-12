---
title: "Samba setup on Ubuntu and Winxp"
date: 2008-04-02
forum: Networking &amp; Wireless
---

### Post by superprash2003 on 2008-04-02
have you added a samba user   sudo smbpasswd -a system_username  ???

gksudo gedit /etc/samba/smbusers

    *
          o Insert the following line into the new file 

system_username = "network username"

from [www.ubuntuguide.org](www.ubuntuguide.org)

---

