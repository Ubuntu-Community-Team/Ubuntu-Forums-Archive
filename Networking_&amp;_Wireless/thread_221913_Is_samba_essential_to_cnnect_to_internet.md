---
title: "Is samba essential to cnnect to internet??"
date: 2006-07-24
forum: Networking &amp; Wireless
---

### Post by true_friend on 2006-07-24
i have configured my kubuntu DD system in every aspect for static ip address but i have not access to internet. at same system windows xp 2006 working fine. i use cable net. the gentelman helped me on kubuntu forums made sorry in the end he was unable to solve my problem. now i want to ask i have not installed samba yet. is samba essential to connect to internet or not???
Note: pining to my local server 191.168.0.1 was fine and other out puts like route, ifconfig were also ok. plz tell me is it possible to get internet after sabma installation or it is a netwrok sharing tool only???

---

### Post by Titus A Duxass on 2006-07-24
Samba is not necessary.
Have you looked at Systems => Adminstration => networking?

You should see your card there.

---

### Post by Thund3rstruck on 2006-07-24
Samba is only needed if you're machine is serving files to windows machines. the samba filesystem (smbfs) is needed to connect to windows shares. Neither are needed to access the internet. 

Start with ifconfig to validate that your device has the proper network settings and then follow up with ping and traceroute to validate connectivity

---

