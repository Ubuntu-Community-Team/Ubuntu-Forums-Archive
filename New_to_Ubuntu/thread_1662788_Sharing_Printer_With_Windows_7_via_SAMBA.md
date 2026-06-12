---
title: "Sharing Printer With Windows 7 via SAMBA"
date: 2011-01-08
forum: New to Ubuntu
---

### Post by Jacobah on 2011-01-08
Hi, I'm very new to linux and have been using ubuntu 10 for about a week now. I am trying to connect to a printer on our windows 7 pc through samba, but it keeps asking me for a username and password. I've looked around and everywhere says the username and password are what I use to login to the windows computer. I've put the correct name and password but it still doesn't allow me to connect. I only have a username on the computer and no password, do I have to put a default phrase if there is no actual password? I've tried dozens of combinations, I have file and printer sharing enabled, with password protected sharing turned off on the windows pc and I just don't get it. Any help would be appreciated.

EDIT: I did finally find the answer. Enable lpd sharing on the windows 7 computer, set up SAMBA just as you normally would except instead of smb://user/printer name do lpd://ip.address.of.computer/printer name

---

### Post by sandyd on 2011-01-08
> **Jacobah said:**
> Hi, I'm very new to linux and have been using ubuntu 10 for about a week now. I am trying to connect to a printer on our windows 7 pc through samba, but it keeps asking me for a username and password. I've looked around and everywhere says the username and password are what I use to login to the windows computer. I've put the correct name and password but it still doesn't allow me to connect. I only have a username on the computer and no password, do I have to put a default phrase if there is no actual password? I've tried dozens of combinations, I have file and printer sharing enabled, with password protected sharing turned off on the windows pc and I just don't get it. Any help would be appreciated.sharing doesnt work with windows 7 if your usin homegroups

---

### Post by oldsoundguy on 2011-01-08
Don't use Windows 7 .. never have and never will. I DO have an XP box that serves as my print server.

But, believe it or not .. here is some info that might do it for you in Win7:
[http://social.answers.microsoft.com/Forums/en-US/w7network/thread/49458c16-e99e-4af9-8cd9-40299af66f8e](http://social.answers.microsoft.com/Forums/en-US/w7network/thread/49458c16-e99e-4af9-8cd9-40299af66f8e)

---

