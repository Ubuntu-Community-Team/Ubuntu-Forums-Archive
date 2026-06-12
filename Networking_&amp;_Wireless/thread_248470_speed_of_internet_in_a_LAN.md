---
title: "speed of internet in a LAN"
date: 2006-09-01
forum: Networking &amp; Wireless
---

### Post by vamsidhar on 2006-09-01
Lets discuss about the speed of internet in ubuntu.Mostly this thread is about how this operating system affects in grabbing speed when internet is distributed over a group of computers....

---

### Post by vamsidhar on 2006-09-01
Hello guys a very predominant thing that i observed in ubuntu6.06 is that when u put in the live CD and work on it...u will find that ur internet is much faster than when u actually install the system....can any one tell me reason..>??????

---

### Post by MrHorus on 2006-09-01
Can't say I have noticed any differences in network connectivity.

---

### Post by sebastfr on 2006-09-01
check your dns configuration is ok:

edit /etc/resolv.conf and look if the 'nameserver' directive points to a correct dns server.
I had this problem a few weeks ago where my first 'nameserver' entry was our gateway/router which doesn't do dns!! So basically it takes some time for the address resolution (internet itself wasn't slower once you had the connection established, but it was v slow for making the first connection)

Seb

---

