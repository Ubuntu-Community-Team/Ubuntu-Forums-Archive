---
title: "how to change gateway wihout enter the root password"
date: 2007-03-25
forum: Networking &amp; Wireless
---

### Post by tyohan on 2007-03-25
i am an IT Staff who working on BANK. We will use Xubuntu on our branch. 
Our branch connected with radio link but sometime connection break off and can't communicate with our central office. If our connection get break off we usually change the gateway to communicate with dial up modem. In windows we using batch script. I try on Xubuntu with shell script using sudo and route commands but it must provide root password.

There's anything i can do with shell script so my user can change gateway address without root password? Thanks..

---

### Post by spd106 on 2007-03-25
As the default route is system setting rather than per user it's unlikely that you will be able to make this change without raising the level of access.

You could add the user to the sudoers group but restrict their access to specific commands. This way they use their own password and leave an audit trail of usage. Try this page to get you started [https://wiki.ubuntu.com/Sudoers](https://wiki.ubuntu.com/Sudoers).

---

