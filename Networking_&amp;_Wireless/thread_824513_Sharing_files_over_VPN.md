---
title: "Sharing files over VPN"
date: 2008-06-10
forum: Networking &amp; Wireless
---

### Post by Moezzie on 2008-06-10
I set up a VPN server using [[COLOR="Red"]this guide[/COLOR]]("http://forums.bit-tech.net/showthread.php?t=132029") (using pptpd) a couple of days ago, in the hope to be able to access some of my important files from work and other places. Everything works fine, except for the file sharing part. Ive found lots of guides about how to set up VPN networks, but i cant seem to find any about sharing files.

How would you go about to have the server share a directory?
If pptpd isn't good enough i would be more than happy to change to something else as long as there is a good guide for it somewhere.

Regards
Moezzie

---

### Post by superprash2003 on 2008-06-10
you would need to install samba for that.. [http://prash-babu.blogspot.com/2008/05/how-to-setup-samba-in-linux.html](http://prash-babu.blogspot.com/2008/05/how-to-setup-samba-in-linux.html)

---

### Post by Moezzie on 2008-06-10
> **superprash2003 said:**
> you would need to install samba for that.. [http://prash-babu.blogspot.com/2008/05/how-to-setup-samba-in-linux.html](http://prash-babu.blogspot.com/2008/05/how-to-setup-samba-in-linux.html)
I do have samba installed, im running a samba based media server on the same machine.
This might seem like a really stupid question, but do i need to runa a VPN client, on the same computer that hosts the VPN server, to get it's shared folders to show?

---

### Post by superprash2003 on 2008-06-10
you need to connect to your VPN [https://wiki.ubuntu.com/mppeVPNhowto?highlight=%28VPN%29](https://wiki.ubuntu.com/mppeVPNhowto?highlight=%28VPN%29)

---

