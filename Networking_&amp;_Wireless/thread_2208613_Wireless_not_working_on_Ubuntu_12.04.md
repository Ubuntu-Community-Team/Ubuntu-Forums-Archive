---
title: "Wireless not working on Ubuntu 12.04"
date: 2014-03-01
forum: Networking &amp; Wireless
---

### Post by dottore2 on 2014-03-01
Hi,

I'll preface this post by saying I am a relatively new user to Ubuntu.

I have a new laptop Fujitsu Lifebook AH512. Yesterday I installed everything from scratch and everything was working correctly, the wireless networks were recognized etc. Today it stopped recognizing my wireless network. Wired connections work.

How do I diagnose this? Please include detailed instructions. None of the topics that I've read here have helped me. The troubleshooter at [https://help.ubuntu.com/12.04/ubuntu-help/net-wireless-troubleshooting.html](https://help.ubuntu.com/12.04/ubuntu-help/net-wireless-troubleshooting.html) didn't help as well.

Thanks!

---

### Post by praseodym on 2014-03-01
Please show the terminal outputs of these commands:
```

uname -a
lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list
cat /etc/resolv.conf
```
Does LAN work?

---

### Post by dottore2 on 2014-03-01
Since the installation was pretty fresh I went and started a new installation again. It's currently installing so I'll get back to you with result. Although wireless works on Live CD.

> [COLOR=#000000]Does LAN work?[/COLOR]

Yep.

---

### Post by dottore2 on 2014-03-01
Installation is done and everything is working so I'll tag this thread as resolved, but will keep these commands in mind if it happens again, and will definitely come back to the forum. Thanks!

---

