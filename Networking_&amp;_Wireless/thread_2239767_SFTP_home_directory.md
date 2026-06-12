---
title: "SFTP home directory"
date: 2014-08-15
forum: Networking &amp; Wireless
---

### Post by Jamesy281 on 2014-08-15
Hi There,

I am having an issue with SFTP for a user. I have created the account, set the home directory and relevant permissions, assigned the primary group and other relevant groups and assigned the proper permissions to the relevant shared folders.
The users are CHROOTED and so are jailed to their home driectories. There is an images folder which all the other users see as well as their home directory when they connect. I need this user to be the same but when they log in they only see an empty home folder.

Looking at id, groups and /etc/passwd the user looks the same as all the others. I'm not sure what I have missed. any pointers would be greatly appreciated.

Thanks,
James.

---

### Post by TheFu on 2014-08-15
How confident are you that the chroot environment is setup properly?  Things like mirroring the /etc/passwd/group files, correct?

---

### Post by Jamesy281 on 2014-08-15
I'm pretty sure it is set up correctly, It was configured by someone else but there are plenty of other user accounts that work fine. The issue is that I am not sure how to configure this final piece.

---

### Post by TheFu on 2014-08-16
HOME is controlled by the password entry.  That can come from /etc/passwd ... but in a chroot environment, access to that file is impossible, so you need to copy it over under the chroot.  Or passwd entries can come from other places - LDAP, AD, RDBMS ... and you'd need to setup enough of the infrastructure inside the chroot to get that working too.

So - it is unclear what you mean by "final piece" - can you clarify?  I'd check the passwd DB (where ever that is) carefully.

---

### Post by Lars Noodén on 2014-08-16
Maybe we should take a look at what has been set up.  Would you mind posting the sshd configuration file so we can see what the server is expecting?  It is /etc/ssh/sshd_config

---

