---
title: "Urgent help.. how to remove the password saved by pppoeconf?"
date: 2005-07-21
forum: Networking &amp; Wireless
---

### Post by sapo on 2005-07-21
i ve installed ubuntu in a box here.. and used my user and password to conect to my adsl.. using pppoeconf..

but now it connects on boot.. i tried to run pppoeconf again but it didnt worked.. i ve removed the password from /etc/ppp/chap-secrets and pap-secrets.. 

BUT IT IS STILL CONNECTING!


ahhhhhhhh i cant leave my password there..  ](*,) 

please how do i remove the user and password or change it?

thanx!

---

### Post by az on 2005-07-21
Don't panic!

Sudo pppoeconf and put in another password.

Anyway, your password should be hidden in /etc/ppp/peers/dsl-provider...

---

