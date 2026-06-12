---
title: "Vinagre Remote Desktop"
date: 2009-04-21
forum: New to Ubuntu
---

### Post by Frank_F on 2009-04-21
Hello

I constantly receive when connecting from my laptop to desktop via vinagre joe-desktop:o that connection is closed after remote desktop viewer is open.

when i press connect find in remote desktop viewer on my ubuntu laptop I dont see any vnc servers.

Keep in mind I can connect to the desktop using vinagre joe-desktop to itself. SSH is working between latop and desktop. Portforwarding 5900 on router and ubuntu firewall

I have tried sudo, su - ...etc

please help

---

### Post by cariboo on 2009-04-22
If you have a router, why run a firewall on your ubuntu computer? Do you have a static ip address on your desktop? If you have a static ip address, do you have it aliased in /etc/hosts eg:

```
192.168.1.100     joe-desktop
```

on your laptop? THe above ip address is just an example, substitute your desktops ip address for the above example.

---

### Post by Frank_F on 2009-04-22
thanks ! it was the firewall after all

---

