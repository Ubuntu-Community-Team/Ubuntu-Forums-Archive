---
title: "Computers don't see eachother in my network."
date: 2014-05-13
forum: Networking &amp; Wireless
---

### Post by Michel_de_Bruin on 2014-05-13
Goodmorning,

Can anyone help me with this? I installed Lubuntu 14.04 on two of my desktop pc's that share my home wifi network. Internet works fine. After the installation I went to 'PCmanFM', go--> network and all they see is the windows network. I cannot open it because it refuses the password, both for my windows account and the homegroup password.

What have I done to try and solve the problem?
[LIST]
[*]I installed Samba on both Lubuntu pc's. I added a shared folder (Home) and added a user (linux identity) with read and write rights on the folder. I did this on both pc's. Unfortunately this had no effect.
[/LIST]

What could be wrong? One pc is HP, intel 4 with 1 gig of ram. - The other pc is Dell, intel 4, with 2 gigs of ram. 

If would be great if someone could help me.

Cheers,
Michel

---

### Post by dannyboy79 on 2014-05-13
is the username and password the same on both machines? if you're using 'user' level security for samba you have to add those users to the smbpasswd file. a command like
```
sudo smbpasswd -a david
```
would create a samba password for user david and add it to the smbpasswd database. if the usernames are different you could use the username map option within your smb.conf file and then within the username-map.txt file you would map a username to another username.

---

