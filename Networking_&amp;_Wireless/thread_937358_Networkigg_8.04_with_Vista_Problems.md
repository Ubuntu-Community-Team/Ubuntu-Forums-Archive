---
title: "Networkigg 8.04 with Vista Problems"
date: 2008-10-03
forum: Networking &amp; Wireless
---

### Post by monkeystuner on 2008-10-03
When I view my network in Hardy, I see both my Mac Laptop which I can get files from but I also see my Vista computer but when I connect to it, it opens like I am connected but there is nothing there. Does anyone know what I might need to change so I can transfer files between Vista and Hardy. While I am here, I don't if anyone can help on this or not but I can see my MacBookPro in Hardy and I can pull files off of it but I can't see my 8.04 on my MBP, does anyone know why I can go one way and not the other? How do I fix this?

---

### Post by cariboo on 2008-10-03
You can see other computers on the network, because smbclient is installed by default, for more on smbclient see:

```
man smbclient
```

For the other computers on your network to access your hardy installation you need to install samba. For a samba howto look here:

[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

Jim

---

### Post by monkeystuner on 2008-10-03
Thanks for the reply, I will give this a shot

---

### Post by jonandrews on 2008-10-05
Hi - nice to see you're using 3 different operating systems. I've written a webguide to networking between Ubuntu & XP.  Many of the principles apply to Vista & Mac, so you may find it helpful:

[http://www.europe.eclipse.co.uk/Ubuntu/](http://www.europe.eclipse.co.uk/Ubuntu/)

---

