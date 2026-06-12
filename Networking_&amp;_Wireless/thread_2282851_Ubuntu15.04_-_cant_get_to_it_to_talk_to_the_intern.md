---
title: "Ubuntu15.04 - cant get to it to talk to the internet, pc not on domain"
date: 2015-06-17
forum: Networking &amp; Wireless
---

### Post by lithiumKid1976 on 2015-06-17
hi

ive installed 15:04 in a work environment.
Currently, i don't have the box added to the domain.

we use a proxy server for internet access (domain user name and password required).

so i set the proxy settings under the network, but i still don't get internet access.
i would be expecting firefox to prompt for the domain username and password, (and it does) but it wont acceptt my username and password

any suggestions on how i can get it to talk to the internet, so i can install some programs.

thanks
D

---

### Post by William_Parks_Walk on 2015-06-18
I know in windows you need to prefix the username with the domain ie /domain/user

---

### Post by wildmanne39 on 2015-06-18
*Thread moved to **Networking & Wireless**.*

---

### Post by lithiumKid1976 on 2015-06-24
thanks for the move.

still cant get it to work. checked all the forums, all everyone points to is editing the /etc/apt/apt.conf file, and adding the 
acquire::http::proxy "http://username:password@proxyserver@proxy/"
tried everything ive seen on line. cant see the answer.
firewall is fortigate,  webtitan is running also.

any other suggestions.

---

