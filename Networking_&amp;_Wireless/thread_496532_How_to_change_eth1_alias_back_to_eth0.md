---
title: "How to change eth1 alias back to eth0?"
date: 2007-07-09
forum: Networking &amp; Wireless
---

### Post by rogblake on 2007-07-09
I'm running Ubuntu "Dapper" 6.06 and changed my network adapter from a Realtek to an Intel 10/100. Ubuntu picked up on the network card OK, but now the alias for it is eth1 instead of eth0. How can I change this back to eth0? On other distributions that I've used, the aliases are set in /etc/modprobe.conf or /etc/modules.conf, but that does not seem to be the case here. I see there is an /etc/modprobe.d directory, but did not see the ethernet aliases there. (Tried "grep eth *" and came up empty.)

Thanks for any help with this!

---

### Post by kevdog on 2007-07-09
Check you /etc/iftab file.

---

### Post by rogblake on 2007-07-09
> **kevdog said:**
> Check you /etc/iftab file.

I see, all that was needed was to edit that file, changing the mac address listed for eth0 to match the new NIC. Worked like a champ, thanks for the pointer!

---

### Post by lkstamenov on 2007-11-17
I have the same problem but I don't have /etc/iftab. It just doesn't exist. I run Ubuntu Desktop 7.10.

What can I do to get back to eth0. It is now eth38 and for static IP  I have to do:

1. sudo pico /etc/network/interfaces 
2. sudo /etc/init.d/networking restart

every time

Can I fix this for permanent. It seems it is a common problem

---

### Post by Suparious on 2008-06-11
I was having the same problem and found this thread. I use Ubuntu 8.10.

Looks like udev is handling things now.

Try editing this

```
sudo nano /etc/udev/rules.d/70-persistent-net.rules
```

---

