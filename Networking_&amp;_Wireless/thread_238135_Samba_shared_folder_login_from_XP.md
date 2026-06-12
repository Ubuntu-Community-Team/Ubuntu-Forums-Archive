---
title: "Samba shared folder login from XP"
date: 2006-08-17
forum: Networking &amp; Wireless
---

### Post by sdebo on 2006-08-17
After setting up Samba to access a folder on Ubuntu Dapper from XP I got a host/Guest logon dialog asking for a password. I edited smb.conf and synched the accounts with Linux. Now should I create a Guest account? Alternatively, why were my deafault username and password not accepted?

---

### Post by gerbman on 2006-08-17
[This]("http://ubuntuforums.org/showpost.php?p=1265314&postcount=2") is how I have my Samba set up to do what you're trying to do. A few other users have been successful with the same configuration. The username/password you'll need to enter when trying to connect from Windows will be whatever you specific in step 4. Hope it helps.

---

### Post by dmeehan on 2006-08-18
thanks! that was just what i was looking for
short and sweet and straight to the point.

especially the restart command for samba, previously i had to reboot my xububtu server for it to pick up the changes

---

### Post by gerbman on 2006-08-18
You're welcome. :)

---

### Post by sdebo on 2006-08-18
that worked. thanks for your help.

---

