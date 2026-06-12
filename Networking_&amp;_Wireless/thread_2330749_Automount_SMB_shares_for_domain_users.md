---
title: "Automount SMB shares for domain users"
date: 2016-07-14
forum: Networking &amp; Wireless
---

### Post by kevo89 on 2016-07-14
I am experimenting with adding Ubuntu machines to our school's active directory domain and have a few questions.  I was able to use Powerbroker Open to add login authentication for domain users.  I can also connect to shares on the domain using the file browser without having to put my password in again.  What I am looking for is to have every domain user's SMB share automatically mount when they log in.  All of the documentation I have read has been for hard coding usernames and passwords for a specific share into a config file that FSTAB can read.

What I want is something that can look at the username logging in and automatically mount smb://server/User$ as a folder on the desktop without having to store or input credentials again.

Thanks!

---

### Post by smelheim85 on 2016-07-23
I'm not that too familiar with setting up connections between Active Directory and Linux systems but I will try my best.  First off Active Directory is only a centralized authentication service that just says who can access the system and what systems they can access.  Now what you found about the /etc/fstab will need to be setup for automatic setup of drives at boot.  Can you use the user expression or there is a way to setup a specific group that will give permissions to used logging in.  From their a security group that is created in Active Directory can connect with the group you created on your Linux machine.

---

