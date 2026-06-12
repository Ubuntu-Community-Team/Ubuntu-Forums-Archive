---
title: "Printer sharing"
date: 2008-05-01
forum: Networking &amp; Wireless
---

### Post by crabhunter on 2008-05-01
I'm sure this has been asked a thousand times before.
I have a typical home network.
Two pcs,two laptops and numerous games machines linked through a wireless modem/router.
My pc has the printer and runs vista,XP and Ubuntu 8.04 desktop.
I want the other pcs to be able to print when I am using Ubuntu on my pc.
I have googled and found lots of answers if you want Ubuntu to print to a windows pc but not the other way around.
If anyone can just give me a link to a tutorial that would be great.
Mike

---

### Post by cmnorton on 2008-05-01
You need to share your printer using samba. There are tons of posts in these forms. 

First, going between Windows and Linux, your linux workgroup name should match the Windows workgroup or domain name. Add the domain/workgroup name to /etc/resolv.conf

search your-domain-name, and include a .local if that is part of the domain name.

Make sure samba is installed and that printer sharing is installed by default.

---

