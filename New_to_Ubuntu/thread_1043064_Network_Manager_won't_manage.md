---
title: "Network Manager won't manage"
date: 2009-01-18
forum: New to Ubuntu
---

### Post by 44tr on 2009-01-18
Hi.  I've been searching and reading (really), but I can't seem to get the answer to the following problem:

My network connection won't enable upon boot.  If I type ```
sudo dhclient eth0
``` into the command line (and pw), then I'm connected and no problem, but I have to do it every time I boot.

The Network Manager icon has an exclamation point that says the connection is unmanaged, or no valid active connections detected (either before I connect manually or after).  I have added a wired connection (networking is enabled), but it has no effect.

Setup:  Ubuntu 8.10, AT&T DSL service, router/switch connected to modem.

If network manager is not going to be helpful, can someone explain what configuration file to edit (and how) to get the command to execute on startup?

Thanks in advance for any help.

---

### Post by 44tr on 2009-01-18
Bumping up a bit, is this a hard question to answer or so easy it should be obvious?

---

### Post by stderr on 2009-01-18
I too struggled with the new implementation of NM. As for getting the wired eth working, I left it out of NM's configuration, and added it to interfaces. Perhaps that would help you too? FWIW, NM still shows no valid connections, but the connection works fine.

Could you post your /etc/network/interfaces file?

---

### Post by 44tr on 2009-01-18
The contents of the file are:  ```
auto lo
iface lo inet loopback

iface eth0 inet static
address x.x.x.x
netmask 255.255.255.0
gateway x.x.x.x

iface wlan0 inet static
address xxx.xxx.xxx.xxx
netmask 255.255.255.0
gateway xxx.xxx.xxx.xxx
wireless-key xxxxx
wireless-essid xxxxxxx

auto wlan0

auto eth0

```

Thanks for reply.  Ideas and work arounds are most welcome.

---

### Post by 44tr on 2009-01-19
OK, I see now.  I had it set for a static IP address in the interfaces file.  I just didn't know the name of the file to look in.  I commented out the lines where eth0 is assigned a static IP, and NM connects just fine.  Thanks for the tip.:D

---

### Post by stderr on 2009-01-19
No problem, glad you got it working :)

---

