---
title: "SSH works, Naulitus browse does not"
date: 2019-10-31
forum: Networking &amp; Wireless
---

### Post by tomer132246 on 2019-10-31
I can connect to my remote PC just fine using the terminals regular ssh.
when trying to view the files using naulitus, im getting an error - Permission denied.
(while using the same password.)


thanks in advance! :)

---

### Post by uRock on 2019-10-31
Are you using SFTP, Samba, or what? Please tell us what you're doing to initiate the connection.

---

### Post by TheFu on 2019-10-31
I don't think "network browsing" works with ssh/sftp.  That is a Windows-Netbios thing.  Have you tried entering a specific URL?
I don't use nautilus, but *caja* (mate file manager) uses URLs **sftp://hadar/** like that.  hadar is a hostname on the network and my client knows the hostname-to-IP translation thanks to /etc/hosts settings.

Plus, if you setup ssh-keys between the client and the server, then the connection will be more secure. Set that up with just 2 commands:
```
ssh-keygen -t ed25519
ssh-copy-id -i ~/.ssh/id_ed25519.pub userid@remote
```
replace your userid and "remote" as needed.  That will be the last time you need to enter a password for that connection.

---

