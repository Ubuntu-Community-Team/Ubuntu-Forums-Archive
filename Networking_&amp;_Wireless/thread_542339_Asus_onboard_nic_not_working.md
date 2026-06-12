---
title: "Asus onboard nic not working"
date: 2007-09-03
forum: Networking &amp; Wireless
---

### Post by cyu6722 on 2007-09-03
I installed Ubuntu 7.04 on my computer with a ASUS p5l-vm 1394 motherboard with onboard NIC and everything worked.  This was at home with a cable modem and a netgear router. I am at school now which provided us with a modem/router from time warner. I had to reinstalled ubuntu but this time, I don't have any internet. It's strange cause during installation, it says the network device not found, but at home, I had internet even afterwards. This appeared both times that I have installed it.  I tried to compile the linux driver from the asus site but it kepts saying config.h not found. Anyone have any suggestions on how to get my internet working?

---

### Post by noob12 on 2007-09-04
Can you post the output of
```

lspci -nn

sudo lshw -C network

ifconfig -a

```

If you have a USB jump drive you can use it to transfer the output in a text file to a computer where you can post to the forum.

---

### Post by mmcmonster on 2008-01-03
[This link]("http://ubuntuforums.org/archive/index.php/t-292838.html") may be of help.

I'm thinking of getting this motherboard.  Has this issue been resolved in Ubuntu 7.10?

---

