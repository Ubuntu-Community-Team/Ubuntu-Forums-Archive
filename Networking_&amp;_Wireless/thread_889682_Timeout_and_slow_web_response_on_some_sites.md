---
title: "Timeout and slow web response on some sites"
date: 2008-08-14
forum: Networking &amp; Wireless
---

### Post by jose_ramirez on 2008-08-14
Hi,

Since a few days ago I have been experiencing some "strange" behavior browsing the web on my Kubuntu 8.04 desktop. On some sites the response is extremely slow and often the connection timeouts. I have tried with several web browsers (Firefox 2 & 3, Konqueror and Sea Monkey). I also have a Windows XP virtual machine running under VirtualBox and it behaves the same way. For me it looks like something within Kubuntu is causing the problem, I checked and there is no iptables running. I also have a laptop running Vista and there is no problem there so I discard the router. Any help and/or ideas of what may be causing the problem?

Regards,

Jose

---

### Post by Crazed_by_Penguins on 2008-08-14
I have been experiencing a similar problem. I am running Ubuntu 7.10, which I just installed yesterday. My Vista laptop also works fine.

I did some checking, and I can ping the sites just fine, and they show up if I enter the IP address into the browser. I think it may be a problem with DNS.

---

### Post by Crazed_by_Penguins on 2008-08-14
I tried changing the DNS Server to use OpenDNS, using the instructions on [http://www.opendns.com/]("http://www.opendns.com/"). I used the instructions for the computer, not the router, as the internet works fine on other computers. This worked for me, and now the internet works great. Try this and see if it solves your problem.

---

### Post by jose_ramirez on 2008-08-14
Ok, thanks for the reply, I will try it and will let you know.

Regards,

Jose

> **Crazed_by_Penguins said:**
> I tried changing the DNS Server to use OpenDNS, using the instructions on [http://www.opendns.com/]("http://www.opendns.com/"). I used the instructions for the computer, not the router, as the internet works fine on other computers. This worked for me, and now the internet works great. Try this and see if it solves your problem.

---

### Post by jose_ramirez on 2008-08-19
Unfortunately the problem persists... I will keep searching...

---

