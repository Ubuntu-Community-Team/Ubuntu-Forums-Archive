---
title: "Windows loginscript in ubuntu client?"
date: 2008-05-07
forum: Networking &amp; Wireless
---

### Post by Asmodision on 2008-05-07
Hi!

Have successfully made my Ubuntu client a member of our company domain and are able to login in with all kinds of users on my machine.
We are using a w2k3 server as a PDC and the last thing I want to work is that when a user logins it should run a login script localized on the windows server.

For examples: //<windows server>/netlogon/loginlinux.sh or something like that. This script would initially only contain network shares and home directories for the users.

So...how do I make samba to understand that this file exists and run it?

With regards
Mattias

---

### Post by superprash2003 on 2008-05-07
you could do this..
 first mount the drive mount -t smbfs -o username=username,password="" //locationofshfile /local/directory
then you could run the sh file locally by typing sh /local/directory/loginlinux.sh

---

