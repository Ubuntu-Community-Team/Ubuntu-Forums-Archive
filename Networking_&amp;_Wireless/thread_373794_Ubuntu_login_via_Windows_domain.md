---
title: "Ubuntu login via Windows domain"
date: 2007-03-01
forum: Networking &amp; Wireless
---

### Post by sergiodlc on 2007-03-01
Hi folks:

We have a small lab with some PC's running Windows. Our main server has Windows installed and all the users log in to their workstations using their accounts on a windows domain supported by the server. We want to encourage users to move to Ubuntu by installing it in one PC. It would be highly desirable that users log in to the Ubuntu system using the same account they use on the other (windows) PC's at the lab.

Does anyone know how to do it, or even if it's possible?

Regards,

Sergio

---

### Post by spd106 on 2007-03-03
It sounds like your going to be having some fun with samba. There's a guide in the wiki that will help you to get started.
[https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto](https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto)

---

### Post by sergiodlc on 2007-03-05
Thanks so much. It helped a lot.

Sergio.

---

### Post by marvelchip on 2007-12-31
It seems one need to be in the command mode, i`m using GUI, so how do  i get back to this mode for editing these "AC...ryWinbindHowto".

---

### Post by spd106 on 2007-12-31
To access the command line you can open a terminal emulator from the menu in Ubuntu, Applications -> Accessories -> Terminal.

The other Ubuntu variants have terminals too or you can switch to a virtual terminal by pressing Ctrl + Alt + F1 - F6. Press Ctrl + Alt + F7 to get back to the GUI.

---

### Post by marvelchip on 2007-12-31
Thanxs a mil i got there.

---

