---
title: "samba users not working and data missing"
date: 2008-09-29
forum: Networking &amp; Wireless
---

### Post by cyclefiend2000 on 2008-09-29
typical monday morning. i get here and no one on our network is able to log on from their windows machine except for me. we are using ubunutu 7.10 on our server, and i access it using webmin 1.4.

i have checked the samba config and everything seems to be setup correctly. 

any thoughts or ideas?

---

### Post by superprash2003 on 2008-09-29
restart samba server.. by typing sudo /etc/init.d/samba restart .. ensure that pcs are able to ping server.. try accessing via ip instead of hostname

---

### Post by cyclefiend2000 on 2008-09-29
i did restart the samba server. the only way i could access the drives i had mapped on the other computers was to use my user name and password.

---

