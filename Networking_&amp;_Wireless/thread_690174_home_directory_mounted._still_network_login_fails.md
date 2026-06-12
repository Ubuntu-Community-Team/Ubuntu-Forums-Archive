---
title: "home directory mounted. still network login fails"
date: 2008-02-07
forum: Networking &amp; Wireless
---

### Post by nish on 2008-02-07
Hi

I have installed ubuntu in one of the labs. Setup here is like, home directories are on remote server. we mount those home directories. then we login as network user.

here, I have mounted home directory. But still i cant do network login. (by that, i mean, say /users/pg/nish is my home directory which is mounted ar /users. But login using nish does not work) It asks for password but does not accept password.
Any clue?

Thanks
Nish

---

### Post by swerdna on 2008-02-07
If you are running this as a "workgroup" then add the owner of the shared folder to the samba user database and use thos credentials for the challenge that is made to the client machine

Swerdna

---

