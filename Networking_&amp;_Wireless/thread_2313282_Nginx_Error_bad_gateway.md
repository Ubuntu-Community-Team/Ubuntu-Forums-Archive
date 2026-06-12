---
title: "Nginx Error bad gateway"
date: 2016-02-11
forum: Networking &amp; Wireless
---

### Post by Isky on 2016-02-11
I see a lot of post on internet about nginx error bad gateway and its possible solution but my problem is a little difference.
I don't have nginx installed.
I install on my vps apache2 and php7 (without php7.0-fpm).
Then i install gitlab and now nothign seems to work. I purge this package but i still continue to have nginx bad gateway.
I try to search if I have some nginx config file on my system but i don't find anything and I don't have any nginx package installed.

How can i solve this?
Thanks.

---

### Post by alexandari on 2016-02-12
Hello! Gitlab install comes with nginx as a web server. If you installed the gitlab bundle package using their official documentation, you are running nginx. Two things you could try - stop apache and restart the whole gitlab bundle

**service apache2 stop**
**gitlab-ctl restart ** or **gitlab-ctl reconfigure**

Tell me if this worked

---

