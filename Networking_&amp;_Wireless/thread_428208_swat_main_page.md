---
title: "swat main page"
date: 2007-04-30
forum: Networking &amp; Wireless
---

### Post by bilacus on 2007-04-30
I did  install swat to manage samba options...when i type 127.0.0.1:901/ after the login appears the administration page of samba ..fine, 

the problem is that I see only 4 main Icons " HOME, STATUS, VIEW, PASSWORD"

I did aspect more icons like "SHARE, GLOBALS, WIZARD,PRINTERS" practically I can change only the password but nothing else. It seems I'm logged in without administration
rights.

any help will be appreciated.

Marco - It -

---

### Post by ErikTheRed on 2007-05-02
You need to login as root to access the other options. Make sure you've given the root account a password.

```
sudo passwd root
```

---

