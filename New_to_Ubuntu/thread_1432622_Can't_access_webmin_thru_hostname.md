---
title: "Can't access webmin thru hostname"
date: 2010-03-18
forum: New to Ubuntu
---

### Post by rgotten on 2010-03-18
i did recently and upgrade to Ubuntu 9.10...i have used webmin to manage the server and now if i type: [https://hostanme:10000](https://hostanme:10000) i get a: Internet explorer cannot display the webpage....but if i use: [https://ipadress:10000](https://ipadress:10000) it works fine..any idea or help will be appreicate

rgotten

---

### Post by HermanAB on 2010-03-18
Your DNS is broken.

Test it with dig or nslookup.

---

### Post by wjm on 2010-03-18
Here's a pretty simple guide on how to setup/maintain a BIND server on Ubuntu - [http://www.ubuntugeek.com/dns-server-setup-using-bind-in-ubuntu.html](http://www.ubuntugeek.com/dns-server-setup-using-bind-in-ubuntu.html)

---

