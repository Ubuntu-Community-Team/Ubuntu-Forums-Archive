---
title: "Second user can't access Samba share"
date: 2019-02-23
forum: Networking &amp; Wireless
---

### Post by LeLaTe on 2019-02-23
So I've set up samba share on my server. Works fine on my own account. I've created another using with adduser, used smbpasswd -a to create Samba password for the account, and added the user to valid users in smb.conf, and then restarted Samba. I can access the shared folder just fine with my own account. When trying to acces the share with the new account, it says to "Please verify your user details". Have I missed something?

---

### Post by Risperix on 2019-02-23
I sugest you to check there are no permissions layer overlapping.

---

