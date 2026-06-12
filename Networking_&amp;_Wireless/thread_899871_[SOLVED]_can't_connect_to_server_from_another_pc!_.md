---
title: "[SOLVED] can't connect to server from another pc! -HELP!"
date: 2008-08-24
forum: Networking &amp; Wireless
---

### Post by poo_22 on 2008-08-24
first off, i'm a noob... especially at running servers on linux. But i had a webserver goin on windows, everything was fine.

so. here's my problem:
i got a webserver going (abyss) and it works fine and displays my page when i type "http://localhost" in my browser. Then i type my local ip, also works fine. I tried to connect from a computer on my lan, no luck.

What could be the problem?
it can't be my port being blocked, because it works fine when i type my ip. so i'm confused.

---

### Post by poo_22 on 2008-08-24
solved!
ran:
iptables -I INPUT -p tcp --dport 80 -j ACCEPT

fixed 'er right up!

---

