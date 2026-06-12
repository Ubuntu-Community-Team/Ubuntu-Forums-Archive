---
title: "help setting up squid"
date: 2011-09-07
forum: New to Ubuntu
---

### Post by cye05 on 2011-09-07
hi i was wondering if i could get some help with squid. i want to set up a proxy for chaching, and this is just for fun and to restore an old computer that i don't use. i installed lubuntu on the server box and squid. now i'm not sure if my logic is off but this is how it is set up. i have a wireless nic running the server and i forward my webbrowsing from my ubuntu 10.04 machine to the ip address and port of the sever box (oh and i installed apache the machines both talk to each other through ssh and website).when i do this it says access denied contact webmaster. is there a good manual you would recommend or something you see that I'm doing wrong?

---

### Post by bodhi.zazen on 2011-09-07
[https://help.ubuntu.com/10.04/serverguide/C/squid.html](https://help.ubuntu.com/10.04/serverguide/C/squid.html)

If you get stuck with some step, ask.

---

### Post by cye05 on 2011-09-08
Thank you so much bodhi. that was exactly what i was looking for. just one note for anyone else who does this you have to comment this line out http_access deny in /etc/squid/squid.conf all and put http_access allow all. after i set it up using the manual and did this everything worked fine.

---

### Post by bodhi.zazen on 2011-09-08
> **cye05 said:**
> Thank you so much bodhi. that was exactly what i was looking for. just one note for anyone else who does this you have to comment this line out http_access deny in /etc/squid/squid.conf all and put http_access allow all. after i set it up using the manual and did this everything worked fine.

Feel free to add that to the wiki, it is after all a community maintained wiki ;)

---

