---
title: "Ethernet lost"
date: 2007-08-16
forum: Networking &amp; Wireless
---

### Post by fordexplorerdotnet on 2007-08-16
Realtek NIC.  Fiesty.
I'm using the same card and DSL modem under Win right now.

I had no nic problems, last night 5 min before I went to bed sk0tcom was vnc'd in to my system. Today I get home and fire it up and Ubuntu isn't activating the nic on boot, the ethernet light on the modem never turns on. If I boot windows, it works fine. I did sudo /etc/init.d/networking restart and no changes. I had copied the whole thing but I don't know where it went. I cannot ping 192.168.1.1 (dsl modem) and I can ping 127.0.0.1. I'm stumped.
I just booted w/ my live cd and it didn't work then either. The only changes that have been made are various XP updates, as this is a clean install.

---

### Post by bapoumba on 2007-08-16
What is the output to:
```
cat /etc/network/interfaces
cat /etc/resolv.conf
ifconfig
```
Is this a wired connection? A wireless? If wireless, can you try an ethernet connection? Do you have a firewall set up, and changed something?

---

### Post by fordexplorerdotnet on 2007-08-16
I'm not at home right now so I can't try the code, but it's a wired connection.  There is a wireless card present, but not in use.  No firewall setup, the dsl modem is a Westell 1600 which acts as a router and all ports are open.  The modem couldn't be the issue though, as it works fine under Windows.

---

