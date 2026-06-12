---
title: "protect folders"
date: 2010-02-27
forum: New to Ubuntu
---

### Post by emailadress on 2010-02-27
Hello everyone! I was wondering if it is possible to protect a folder with my user password. This doesn't have to be a high security thing, I just want my password to be required to access my porn. Just as the wireless connection asks me for my password to access something every time I log into a wireless connection. Then, I can put a folder on my desktop, call it "pornography", laugh at everyone who tries to open it and feel VERY mature about it. ;) Is this possible?

Thanks in advance!

---

### Post by HermanAB on 2010-02-27
Just make different user account for porn.

or do:
sudo chown -R root:root /home/username/porn

From then on, you would need to use sudo to access it.

---

