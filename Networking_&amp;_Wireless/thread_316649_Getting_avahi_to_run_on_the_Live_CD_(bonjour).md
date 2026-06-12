---
title: "Getting avahi to run on the Live CD (bonjour)"
date: 2006-12-11
forum: Networking &amp; Wireless
---

### Post by lchrist on 2006-12-11
Hi all,

I would like to get avahi/zeroconf/bonjour running on the Live CD and also announce that it has an SSH Server running.

I've customized the Live CD and added openssh and avahi . But for some reason i cannot seem to find out how to automatically start the avahi daemon.

When i start it manually it does not register my SSH Service ? do anyone know why ?

BTW: Do anyone know how to make it announce a generic TCP based service on a generic port ?

Thanks in advance,

Lasse,

---

### Post by spd106 on 2006-12-11
To get avahi to work on start-up you toggle the setting in /etc/default/avahi-daemon

To get the daemon to register a service you need to put an xml service file in the /etc/avahi/services/ directory. Use the example file from /usr/share/doc/avahi-daemon/examples, which luckily for you is based on ssh.

---

### Post by lchrist on 2006-12-12
Thanks, 

That was exactly the thing i was missing :-)

---

