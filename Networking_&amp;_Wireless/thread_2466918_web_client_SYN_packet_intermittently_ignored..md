---
title: "web client SYN packet intermittently ignored."
date: 2021-09-10
forum: Networking &amp; Wireless
---

### Post by kevin-dinsdale on 2021-09-10
Hi, I am running 21.04 (have nothing to compare to previous vers) and am trying launch a web server. I find when I connect to the server it will intermittently not respond to the client SYN packet. This can be seen on the Tshark trace. I have searched various forums which suggest that parameters in /etc/sysctl may need tweaking. All attempts to fix have failed.
Would anyone have any ideas on areas to address to effect a fix ??

Many thanks

Kev

---

### Post by The Cog on 2021-09-10
This is very interesting, and may help: [https://veithen.io/2014/01/01/how-tcp-backlog-works-in-linux.html](https://veithen.io/2014/01/01/how-tcp-backlog-works-in-linux.html)
I suspect your server is slow getting through its workload. Increasing the backlog should help if the overload is only temporary.

---

