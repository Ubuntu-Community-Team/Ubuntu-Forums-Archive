---
title: "Firefox not upgraded?"
date: 2010-01-01
forum: New to Ubuntu
---

### Post by bobin on 2010-01-01
Maybe i am missing something but my firefox is still 3.0.16  . Though i did note that some weeks ago firefox 3.5 branding packages were being downloaded

---

### Post by stlsaint on 2010-01-01
try this in terminal:
```
sudo apt-get update && sudo apt-get dist-upgrade
```

---

### Post by bobin on 2010-01-01
what does this do?

---

### Post by stlsaint on 2010-01-01
apt-get update will download updates and dist-upgrade shall install them.

if this solves issue please mark thread as solved.

---

### Post by mkvnmtr on 2010-01-01
If you are 0n 9.04 that is the default Firefox. If you want 3.5 you should be able to go to the package manager and download a browser 3.5. That is an unbranded Firefox 3.5. If you want something even newer you can use Ubuntutweek to enable the development repositories for Firefox. That gave me Firefox 3.5.8pre. It is nice.

---

### Post by Sef on 2010-01-01
If you want the latest Firefox, then go the the [Ubuntu Firefox PPA]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa").

---

