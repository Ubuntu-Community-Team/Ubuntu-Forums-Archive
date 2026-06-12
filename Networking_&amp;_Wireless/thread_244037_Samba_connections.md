---
title: "Samba connections"
date: 2006-08-25
forum: Networking &amp; Wireless
---

### Post by Dubbayoo on 2006-08-25
How do I specify the user/pass for samba connections to another box? The local user does not having a matching account on the remote box.

---

### Post by jonj on 2006-08-27
This page helped me set up

[https://help.ubuntu.com/community/SettingUpSamba]("https://help.ubuntu.com/community/SettingUpSamba")

---
[http://know.homelinux.com/](http://know.homelinux.com/)

---

### Post by funchords on 2006-08-28
> **Dubbayoo said:**
> How do I specify the user/pass for samba connections to another box? The local user does not having a matching account on the remote box.

If you're using Gnome, click on Places, Connect to Sever

Under Service Type, choose Windows share.

Fill in the Server name, the Share name, and the User Name (an account on the Windows Box).  

Click on Connect.

On the desktop, an icon should appear.  Double-click that and you will be prompted to enter your Windows password for the account name that you used.  You can also save that password for future use in the Gnome keyring.

To use the Guest account (which may or may not be enabled on that Windows box), the username is Guest and the password is blank.

---

