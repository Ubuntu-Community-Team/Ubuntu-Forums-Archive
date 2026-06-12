---
title: "How can I apply Samba Permission via Active directory users?"
date: 2015-02-27
forum: Networking &amp; Wireless
---

### Post by hack3rcon on 2015-02-27
Hello.I can't apply Permission to Samba share via AD users. Please looking at below link and it is my Samba configure :[http://pastebin.com/YZykxPhjI](http://pastebin.com/YZykxPhjI) change SElinux like below too :chcon -t samba_share_t -R /path/to/shareand then :# chgrp -R "domain users" demo/# chmod -R g+rw demo/but not worked :(Any idea?

---

