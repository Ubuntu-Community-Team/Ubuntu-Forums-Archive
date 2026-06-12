---
title: "I cannot load samba"
date: 2007-02-09
forum: Networking &amp; Wireless
---

### Post by overkill2006 on 2007-02-09
I took an old Dimension 8100 desktop and installed 6.10. I have got everything working. I can access the internet and all my other programs function. 

The problem is when I attempt to share a folder. The software tells me to install samba and I tell it to go ahead. A few seconds later it pops back up asking me again to install samba. I have rebooted and it still does the same thing. Over and over and over again. The main reason I switched to ubuntu to use this machine as a file server. So I am counting on the ability to share files over a windows network. Thanks!

---

### Post by tbroderick on 2007-02-09
Are there any error messages? I would make sure samba is installed, from a terminal;
```
sudo apt-get install samba
```

---

### Post by overkill2006 on 2007-02-09
Ok I am completely new to this, where do I go to enter the codes? 

No I am not getting any errors, and I tried connecting through wireless and a dirrect ethernet cable connection. I have rebooted several times to no avail. I am currently running the updates, about a 2 and a half hour download. I just wanted everyone to know the situaton. I'm learning alot though. So far I really like it!

---

### Post by tbroderick on 2007-02-09
Press Alt-F2, then type in; gnome-terminal and hit enter. A terminal should open up and you can enter sudo apt-get install samba. But you have to wait until the updates are done.

---

### Post by overkill2006 on 2007-02-10
Ounce I completed the updates it worked perfectly. Thanks for all the help!

---

