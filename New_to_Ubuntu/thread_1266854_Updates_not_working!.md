---
title: "Updates not working!"
date: 2009-09-15
forum: New to Ubuntu
---

### Post by kapi on 2009-09-15
after several attempts I seem to be getting no where.

Does anyone know why I keep getting this:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/f/firefox-3.0/firefox-3.0-branding_3.0.13+nobinonly-0ubuntu0.9.04.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/f/firefox-3.0/firefox-3.0-branding_3.0.13+nobinonly-0ubuntu0.9.04.1_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/x/xulrunner-1.9/xulrunner-1.9-gnome-support_1.9.0.13+nobinonly-0ubuntu0.9.04.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/x/xulrunner-1.9/xulrunner-1.9-gnome-support_1.9.0.13+nobinonly-0ubuntu0.9.04.1_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/x/xulrunner-1.9/xulrunner-1.9_1.9.0.13+nobinonly-0ubuntu0.9.04.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/x/xulrunner-1.9/xulrunner-1.9_1.9.0.13+nobinonly-0ubuntu0.9.04.1_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/f/firefox-3.0/firefox-3.0-gnome-support_3.0.13+nobinonly-0ubuntu0.9.04.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/f/firefox-3.0/firefox-3.0-gnome-support_3.0.13+nobinonly-0ubuntu0.9.04.1_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/f/firefox-3.0/firefox-3.0_3.0.13+nobinonly-0ubuntu0.9.04.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/f/firefox-3.0/firefox-3.0_3.0.13+nobinonly-0ubuntu0.9.04.1_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/f/firefox-3.0/firefox_3.0.13+nobinonly-0ubuntu0.9.04.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/f/firefox-3.0/firefox_3.0.13+nobinonly-0ubuntu0.9.04.1_all.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/f/firefox-3.0/firefox-gnome-support_3.0.13+nobinonly-0ubuntu0.9.04.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/f/firefox-3.0/firefox-gnome-support_3.0.13+nobinonly-0ubuntu0.9.04.1_all.deb)
  404 Not Found

---

### Post by ithinkitschad on 2009-09-15
> **kapi said:**
> after several attempts I seem to be getting no where.

Does anyone know why I keep getting this:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/f/firefox-3.0/firefox-3.0-branding_3.0.13+nobinonly-0ubuntu0.9.04.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/f/firefox-3.0/firefox-3.0-branding_3.0.13+nobinonly-0ubuntu0.9.04.1_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/x/xulrunner-1.9/xulrunner-1.9-gnome-support_1.9.0.13+nobinonly-0ubuntu0.9.04.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/x/xulrunner-1.9/xulrunner-1.9-gnome-support_1.9.0.13+nobinonly-0ubuntu0.9.04.1_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/x/xulrunner-1.9/xulrunner-1.9_1.9.0.13+nobinonly-0ubuntu0.9.04.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/x/xulrunner-1.9/xulrunner-1.9_1.9.0.13+nobinonly-0ubuntu0.9.04.1_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/f/firefox-3.0/firefox-3.0-gnome-support_3.0.13+nobinonly-0ubuntu0.9.04.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/f/firefox-3.0/firefox-3.0-gnome-support_3.0.13+nobinonly-0ubuntu0.9.04.1_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/f/firefox-3.0/firefox-3.0_3.0.13+nobinonly-0ubuntu0.9.04.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/f/firefox-3.0/firefox-3.0_3.0.13+nobinonly-0ubuntu0.9.04.1_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/f/firefox-3.0/firefox_3.0.13+nobinonly-0ubuntu0.9.04.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/f/firefox-3.0/firefox_3.0.13+nobinonly-0ubuntu0.9.04.1_all.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/f/firefox-3.0/firefox-gnome-support_3.0.13+nobinonly-0ubuntu0.9.04.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/f/firefox-3.0/firefox-gnome-support_3.0.13+nobinonly-0ubuntu0.9.04.1_all.deb)
  404 Not Found

Whats the entire output of "sudo apt-get update" 
?

---

### Post by MelDJ on 2009-09-15
edit

---

### Post by MelDJ on 2009-09-15
the url is not available...server error perhaps. try doing apt-get update

---

### Post by kapi on 2009-09-15
Thanks will try suggestions

---

### Post by katakaio on 2009-09-15
> **MelDJ said:**
> the url is not available...server error perhaps. try doing apt-get update

Yep . . . the last time that happened to me, the server was down temporarily. Running **apt-get update** the next day did the trick!

---

