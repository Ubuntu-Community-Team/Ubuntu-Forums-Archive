---
title: "Sharing files over the lan"
date: 2008-07-07
forum: Networking &amp; Wireless
---

### Post by rsnow on 2008-07-07
I have 8.04 on one machine and XP on another. I can access from XP my files that I designated to be shared on Ubuntu. But I cannot access the files on XP that are marked as shared. When I click on Places/Network I can see the XP machine but when I click on it the browser shows it to be searching but it never comes up with the folders on the XP machine. I have tried typing the XP user name but I get the same results.

Any ideas as to what I should check?

Oops! I meant to post this in another forum----disregard

Now I am confused because this showed up in both the Beginner and Network forums. So if anyone has suggestions I would appreciate your help.

---

### Post by rbc on 2008-07-07
Welcome to the quirkiness of Samba. Actually, I read somewhere in the forums that some of the problems are with nautilus, not Samba. Don't know if that's true or not. with that said, I cannot exactly fix your issue, but here are the workarounds I do:
1. In the file browser, type: smb://ipaddress (of XP machine)
2. Type the exact path of the share: smb://nameofxpcomputer/user/nameofuser/nameoffolder/nameofsubfolder
3. Install konqueror. I have never had a problem with samba, when using it with the konqueror file browser, although I have not found a way for the print shares to show up with this browser

---

### Post by rsnow on 2008-07-07
Typing the ip address worked. I then still had to give myself permission to access the files on the xp machine. Thanks for the help.

---

