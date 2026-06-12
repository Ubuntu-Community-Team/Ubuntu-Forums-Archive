---
title: "Password Wifi"
date: 2009-09-17
forum: New to Ubuntu
---

### Post by Chris1000 on 2009-09-17
Hei,

There is something, I do not understand :confused:

I changed the login password some days ago. Now, every time I start up the PC, ubuntu ask for a "Keyring" password to get connected to the internet (WIFI). This password however is the old one!.

So, why does the system password change, but not for WIFI? And how can I change the "keyring" password?

Thanks
Chris

---

### Post by mcduck on 2009-09-17
Well, the keyring password is completely a separate thing from your login password. When you install Ubuntu both passwords are set to be the same, but if you change your login password afterwards the keyring password isn't automatically changed. This allows you to use different passwords for login and keyring, if you want to. As long as both passwords are the same (and you are not using automatic login) the keyring is unlocked automatically at login.

Anyway, changing the keyring password is easy:

1.Open the keyring manager (Applications/Accessories/Passwords and Encryption Keys)

2. Go to Passwords-tab

3. Right-click the "Passwords:login"-keyring & select "Change Password"

Now you can change the keyring password. If you use normal login set the password to same as your login password is to unlock the keyring automatically. If you use automatic login leave the new password fields empty to remove the keyring password.

---

### Post by Chris1000 on 2009-09-17
Thanks for your help, it worked.\\:D/

Chris

---

