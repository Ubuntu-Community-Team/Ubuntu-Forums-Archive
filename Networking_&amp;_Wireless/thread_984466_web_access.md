---
title: "web access"
date: 2008-11-16
forum: Networking &amp; Wireless
---

### Post by crobinson on 2008-11-16
I have netgear router. One computer accesses well, wirelessly.
After trying to add a wireless laptop the master computer, ethernet attached, will not display web pages.
What did I do wrong???

---

### Post by cariboo on 2008-11-16
Did you turn off wired access in your router. You didn't say whether your  desktop computer was running Windows or Ubuntu.

To check if you windows computer is getting an ip address go to Start-->Run and type cmd then press enter, this will open a DOS window, at the prompt type:

```
ipconfig /release
```

when the command has finished type:

```
ipconfig /renew
```

This will renew the ip address.

If your desktop is running Ubuntu, open an Applications-->Accessories-->Terminal and type:

```
sudo /etc/init.d/networking restart
```

THis will renew the ip address.

Jim

---

