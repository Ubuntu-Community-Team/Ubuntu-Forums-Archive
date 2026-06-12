---
title: "ASUS UX410UAK Ubuntu 16.04.2 Wifi working but unstable"
date: 2017-02-27
forum: Networking &amp; Wireless
---

### Post by kimaidou on 2017-02-27
Hi all, I have a Asus-ZenBook-UX410UA-GV069T-14 with last updated ubuntu 16.04.
Wifi is connected and always on, but the connection is not stable. After some minutes, I cannot reach websites nor ping public IPs, and then it comes back, but then after some other time it goes off again for a while.

NB: a friend of mine has no issue since he upgraded to 16.10

Here is the result of the wireless-info scripts
[https://paste.sh/Cnf4F1Rd#3tBggZaHIJiTIzmDMW_X_Bw9](https://paste.sh/Cnf4F1Rd#3tBggZaHIJiTIzmDMW_X_Bw9)

Thanks in advance for any help regarding this issue.

Cheers
kimaidou

---

### Post by kimaidou on 2017-02-27
I have just upgraded to 16.10, and it seems this issue is gone.

---

### Post by ajgreeny on 2017-02-27
That Intel Corporation Wireless 8260 wifi adapter needsd 16.10 to work so it is no surprise ypou have found this to be the case.
The 8260 chip is no new it really needs the updated kernel for the correct driver, though it is possible that the LTS 16.04.2 which already has the new 16.10 kernel and xorg version might also have worked for you.

Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to users searching the forum.

---

