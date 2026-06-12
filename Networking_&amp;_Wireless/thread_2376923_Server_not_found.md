---
title: "Server not found"
date: 2017-11-07
forum: Networking &amp; Wireless
---

### Post by Chesslover on 2017-11-07
Yesterday I worked on DNS leaks during OpenVPN sessions and I followed these instructions (third post): [https://www.privateinternetaccess.com/forum/discussion/23756/pia-client-on-ubuntu-17-04-dns-leak](https://www.privateinternetaccess.com/forum/discussion/23756/pia-client-on-ubuntu-17-04-dns-leak)

So I added dns=none line in NetworkManager.conf, disabled and stoped systemd-resolved, restarted Network Manager and added googles nameservers in resolv.conf file. It worked, but today after restart I don't have internet. Network manager says my wired connection is ON and working, but firefox says Server not found. Why is that and how to get internet back?

Now I see someone mentioned in that thread, that reboot could cause problems (because DHCP will overwrite resolve.conf file at startup). I checked my resolve.conf file and it's actualy blank...

---

### Post by SeijiSensei on 2017-11-07
/etc/resolv.conf is rewritten at every boot.  One solution is to edit (as root with sudo) the file /etc/resolvconf/resolv.conf.d/head and add the nameservers there like this:
```

nameserver 8.8.8.8
nameserver 8.8.4.4

```
This file is prepended to the top of resolv.conf when the file is rewritten.

---

### Post by Chesslover on 2017-11-07
I don't have folder /etc/resolvconf/resolv.conf.d

SOLVED by enabling and starting systemd-resolved and rebooting:
sudo systemctl enable systemd-resolved.service && systemctl start systemd-resolved.service

---

### Post by SeijiSensei on 2017-11-07
Ah, I'm still on 14.04 without systemd.  Thanks to you, I'll know not to repeat this advice in the future.  Glad you got it resolved.

Now that you solved your problem, please use the Thread Tools drop-down at the top of this page to mark this thread [SOLVED].

---

