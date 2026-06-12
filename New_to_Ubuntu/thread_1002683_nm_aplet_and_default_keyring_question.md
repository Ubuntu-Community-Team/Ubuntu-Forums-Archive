---
title: "nm aplet and default keyring question?"
date: 2008-12-05
forum: New to Ubuntu
---

### Post by mariane_08 on 2008-12-05
nm aplet and default keyring?
When I boot up I always get the box which says:

"Enter password for default keyring to unlock"
"application nm-aplet wants access to default keyring but is locked"

How do automate this so I dont have to do this every time?

I understand "nm" means network manager but I get this at boot regardless of whether I want to use my WiFi.

---

### Post by vanadium on 2008-12-05
Strange you have this issue. It happens when the pasword of the keyring and that of your system login are different. In System - Preferences - Encryption and keyrings, on the "Password Keyrings" tab, set the "unlock" password for "login" to your user password (click the line "login" and then the "Change Unlock Password" comes available).

Also mention the Ubuntu version you are using.

---

### Post by mariane_08 on 2008-12-05
> **vanadium said:**
> Strange you have this issue. It happens when the pasword of the keyring and that of your system login are different. In System - Preferences - Encryption and keyrings, on the "Password Keyrings" tab, set the "unlock" password for "login" to your user password (click the line "login" and then the "Change Unlock Password" comes available).

Also mention the Ubuntu version you are using.

hmmm...:confused: my passwords are the same! to check I just went to terminal and tried to change it and it responded "password unchanged". So they are the same!

I'm using Hardy Heron

---

### Post by vanadium on 2008-12-07
Should work out of the box on a Hardy system. You might also try to set a blank password in keyring manager. This would be less secure, though (if that matters: this will depend on your requirements).

---

