---
title: "error while using update manager 8.04"
date: 2009-03-09
forum: New to Ubuntu
---

### Post by aszxcv on 2009-03-09
> W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/x/xulrunner-1.9/xulrunner-1.9-gnome-support_1.9.0.6+nobinonly-0ubuntu0.8.04.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/x/xulrunner-1.9/xulrunner-1.9-gnome-support_1.9.0.6+nobinonly-0ubuntu0.8.04.1_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/x/xulrunner-1.9/xulrunner-1.9_1.9.0.6+nobinonly-0ubuntu0.8.04.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/x/xulrunner-1.9/xulrunner-1.9_1.9.0.6+nobinonly-0ubuntu0.8.04.1_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/f/firefox-3.0/firefox-3.0-gnome-support_3.0.6+nobinonly-0ubuntu0.8.04.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/f/firefox-3.0/firefox-3.0-gnome-support_3.0.6+nobinonly-0ubuntu0.8.04.1_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/f/firefox-3.0/firefox-3.0_3.0.6+nobinonly-0ubuntu0.8.04.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/f/firefox-3.0/firefox-3.0_3.0.6+nobinonly-0ubuntu0.8.04.1_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/f/firefox-3.0/firefox_3.0.6+nobinonly-0ubuntu0.8.04.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/f/firefox-3.0/firefox_3.0.6+nobinonly-0ubuntu0.8.04.1_all.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/f/firefox-3.0/firefox-gnome-support_3.0.6+nobinonly-0ubuntu0.8.04.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/f/firefox-3.0/firefox-gnome-support_3.0.6+nobinonly-0ubuntu0.8.04.1_all.deb)
  404 Not Found
..

---

### Post by Nxion on 2009-03-10
Can you post the contents of your /etc/apt/sources.list file? Open a terminal and type:

```
sudo cat /etc/apt/sources.list
```

Also, is this an ongoing issue? Or has this been a one time thing? have you tried to run update manager recently?

---

