---
title: "network-admin fails to run; error is child terminated with 1 status"
date: 2005-09-12
forum: Networking &amp; Wireless
---

### Post by josephproject on 2005-09-12
Hi - I am a two day old newbie, got the free CD of  Ubuntu 5.04 on saturday. I have a shadow password. I am trying to run the network-admin out of the shadow user. When I click it, I get a box entitled 

Changing User... 


and I assume it is asking for my root password. I put the root pw in and get the error

error is child terminated with 1 status

I am trying to change the IP address of my machine so that I can connect to a win XP via ethernet.

Tnanks
Thom

---

### Post by leezer3 on 2005-09-13
No.
You should be entering the password of the user you are running under. (At least, this is the case with standard non-shadow passwords).
The error you are getting tells you that the password is wrong. (If you ran the command network-admin in a terminal, then it would actually give you the full output telling you that the password is wrong :P )

-Leezer-

---

