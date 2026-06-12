---
title: "Samba weirdness"
date: 2008-07-09
forum: Networking &amp; Wireless
---

### Post by crmccreary on 2008-07-09
I've got a strange samba problem that I haven't encountered before.

The Samba server is running Hardy, new install. The client is Hardy, upgraded from Gutsy. The client is a laptop with two NICS, wired & wireless (using the wireless for this example). I installed Samba on the server and the client. On the server, I created a directory, TestShare, in my home directory. I then set the permissions to create & delete and set the same for enclosed files (essentially chmod -R a+w). I then set the share to allow everyone to read & write.

On the client, Places-> Network and then select on the server icon, nothing is shown. If I manually enter "smb://xxx.xxx.xxx.xxx/TestShare" where the x's are the IP address in the nautilus address bar, Voila! Success! 

Why is this? Unfortunately the samba logs are not revealing much on the server or client, even at log level 3.

I've checked a lot of threads on related posts but I haven't seen a clear cut solution. Both the server and client are fully up to date.

---

