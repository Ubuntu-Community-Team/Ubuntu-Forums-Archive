---
title: "Ubuntu LAMP php/ Wants to DL not run"
date: 2009-02-15
forum: New to Ubuntu
---

### Post by cerealtx on 2009-02-15
i have index.html in /var/www with a link to my php file, when i click the link to the php file, it wants to download it and not run it in the browser, what am i doing wrong?

---

### Post by anders_c_ on 2009-02-15
have you restarted the web server after installing php support??
sudo /etc/init.d/apache2 restart

---

### Post by cerealtx on 2009-02-15
> **anders_c_ said:**
> have you restarted the web server after installing php support??
sudo /etc/init.d/apache2 restart

so simple, yet powerful, thanks bro fixed it 100% :)

---

