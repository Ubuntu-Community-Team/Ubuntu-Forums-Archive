---
title: "File Sharing Not Accepting Password"
date: 2019-09-22
forum: Networking &amp; Wireless
---

### Post by MrRubik on 2019-09-22
Hi all. I'm fairly new to Ubuntu but have been learning at a pretty steady pace. I'm trying to share files and folders over my local network. I have configured Samba and enable sharing on the folders I want to share on both my laptop and desktop. Both machines are recognizing each other and the folders that are shared. When I click on a folder to access it, it pops up asking for username, password, and workgroup. I'm assuming my workgroup is the default WORKGROUP because I haven't changed it. I'm using the username and password of my account on the machine (both usernames and password are the same on both machines). When I put in the username and password and click connect the window asking for username, workgroup, and password just comes right back up. It's like it isn't accepting my login credentials. Any help with this would be greatly appreciated as I'd really like to be able to share files over my local network.

---

### Post by #&amp;thj^% on 2019-09-22
Maybe this might help; [https://itsfoss.com/share-folders-local-network-ubuntu-windows/](https://itsfoss.com/share-folders-local-network-ubuntu-windows/)
You might just skip to "Samba server on Ubuntu".
Although it never hurts to read all on a page. :)

---

### Post by SeijiSensei on 2019-09-23
Samba maintains its own password database unless you choose a more advanced option.  Assuming that a *nix account for the user already exists on the machine, you can add a user to the password database with the command
```
sudo smbpasswd -a username
```
where "username" is the Linux username for the account.

---

