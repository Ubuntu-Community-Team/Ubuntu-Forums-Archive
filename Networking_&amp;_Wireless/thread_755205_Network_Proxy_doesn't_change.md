---
title: "Network Proxy doesn't change"
date: 2008-04-14
forum: Networking &amp; Wireless
---

### Post by Zodiachus on 2008-04-14
Hello there,


I use a laptop, so when I have it at work, I set a proxy in network proxy settings. I noticed however, that when I get home and set it to "direct connection", programs such as synaptic and apt-get still tries to go through the proxy. Is this a feature of some sort or a bug?

---

### Post by kevdog on 2008-04-14
Try this

sudo /etc/init.d/networking restart

after making the proxy changes.

---

### Post by Zodiachus on 2008-04-15
Thanks for the hint! Unfortunately it didn't work. It seems my computer has permanently locked the proxy in, regardless of what I do. It doesn't even change after a restart. I attached a screenshot to illustrate.

---

