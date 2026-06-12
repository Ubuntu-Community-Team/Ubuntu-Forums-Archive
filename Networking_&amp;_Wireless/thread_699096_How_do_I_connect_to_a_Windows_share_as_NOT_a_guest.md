---
title: "How do I connect to a Windows share as NOT a guest?"
date: 2008-02-17
forum: Networking &amp; Wireless
---

### Post by softtower on 2008-02-17
I have some Windows shared folders on my XP machine at home. I can access them just fine, but how do I do "Connect As..." to them? Ubuntu always connects as a guest, I don't want that - I want to connect as a Windows user to those shares. My wife's MacBook does this via "Connect As..." menu for any network resource it sees.

Can I do that in Ubuntu? I know how to mount shared resources with specific privileges, but how do I do that in Gnome?

Thank you.

---

### Post by Existentialist on 2008-02-19
It sounds like the best thing to do would be to fix the windows permissions.  If you are able to mount them without a user or password you should probably go to the permissions on the files you are sharing and get rid of the permissions for the Everyone group, which includes anonymous log ins.  Once you have only users with permissions Ubuntu should ask you for a login and you will have the permissions of that windows user for the files.

---

### Post by SpaceTeddy on 2008-02-20
if you connect through nautilus (i.e. from any filebrowser on your ubuntu) with something like *smb://computer*, then simply put a username you want to connect as in front of the computername... it shoould read something like *smb://username@computer*.
this acts as the "logon as" in ubuntu... 

hope it helps

---

