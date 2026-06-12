---
title: "feisty and mod_proxy"
date: 2007-04-23
forum: Networking &amp; Wireless
---

### Post by rgrig on 2007-04-23
After upgrading to feisty my apache reverse proxy stopped working: It kept saying FORBIDDEN.
The solution is to add the following lines

LoadModule proxy_connect_module /usr/lib/apache2/modules/mod_proxy_connect.so
LoadModule proxy_ftp_module /usr/lib/apache2/modules/mod_proxy_ftp.so
LoadModule proxy_http_module /usr/lib/apache2/modules/mod_proxy_http.so

to the file

/etc/apache2/mods-enabled/proxy.load

Hope this will help someone.

---

### Post by akame on 2007-05-02
Thank you! Yes it helped and saved me hours of hunting :-)

---

