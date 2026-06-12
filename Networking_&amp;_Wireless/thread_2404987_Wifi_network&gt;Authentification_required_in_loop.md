---
title: "Wifi network&gt;Authentification required in loop"
date: 2018-10-31
forum: Networking &amp; Wireless
---

### Post by liquidfat on 2018-10-31
Dear everybody,
Here my hardware model: chuwi 14.1 lapbook
Including network controller: intel corp wireless 3165 (rev 91)
System recently installed via rEFInd  : ubuntu 18.04 LTS
Kernel driver in use: iwlwifi
Kernel: 4.15.0-29-generic

My issue:  good detection of wifi networks in the air but no possibility to connect to them when typing the good password. authentification impossible with a request for connexion in loop.

Thank you to anybody having a solution to indicate which steps to take. Regards

---

### Post by Autodave on 2018-11-01
Couple of things to try:

1. Before typing in the password, hit the backspace key a few times and then type in your password.
2. Make a text file and type your password into that. Then, copy and paste the password into the box when prompted. (I have a Dell here that ONLY works that way and I have a friend with the same problem on a different manufacturer.

---

### Post by liquidfat on 2018-11-03
Thank you very much Autodave. Option 2 actually did work.

---

