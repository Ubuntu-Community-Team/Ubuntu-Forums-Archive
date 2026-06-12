---
title: "Installing Drivers?"
date: 2010-11-08
forum: New to Ubuntu
---

### Post by john_jingle on 2010-11-08
Hello folks,

I am an absolute beginner, downloaded 10.10 tonight. Everything has gone smoothly so far (I hope).

My laptop is a samsung r580.

I am having problems with my wireless connection, the connection drops from 150mbs to 1mbps. I searched online and this seems like a common problem when using the Atheros AR9285 wireless card.

All forms/blogs suggested downloading compat-wirelss 2.6 package, which I have done. They then suggest re-installing the Ath9k driver, I can locate the folder but being a complete novice, I have no idea how to install.

Could anyone give me advice?

---

### Post by beew on 2010-11-08
See if this helps.

[https://help.ubuntu.com/community/WifiDocs/Device/Atheros/AR9285](https://help.ubuntu.com/community/WifiDocs/Device/Atheros/AR9285)

---

### Post by john_jingle on 2010-11-09
Thanks for the link, it has given me the knowledge on how drivers are installed. I successfully reloaded the driver but my connection was still dropping. I changed the IPV6 value on my config file to 1 and the connection has been fine for the last 20 minutes

---

