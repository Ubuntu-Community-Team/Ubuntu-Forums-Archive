---
title: "How Do I Delete Current Wireless Settings/Keys/SSID's?"
date: 2008-03-16
forum: Networking &amp; Wireless
---

### Post by chiques on 2008-03-16
Hello Everyone,
I have a borrowed notebook. I was using my home wireless network but would like to delete the current WEP key I have stored before I give it back. I've tried using the "Manual Configuration" option but I don't see any of the listed networks I have in my "Wireless Networks" list. Is there a file or a preferably a GUI I can use to accomplish this?

PS. In Win XP I would just go to the advanced wireless setting and delete the access point (along with the stored settings). I'd like to do the same in Ubuntu 7.10.


Thanks!

:guitar:

---

### Post by alan34 on 2008-03-16
The file your looking for is (in a terminal)

less /etc/network/interfaces                       to view

sudo gedit /etc/network/interfaces              to edit

---

