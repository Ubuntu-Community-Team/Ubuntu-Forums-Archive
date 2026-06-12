---
title: "Change Keyring Password"
date: 2009-03-23
forum: New to Ubuntu
---

### Post by pkulak on 2009-03-23
I've got one password for the user login, and a different one for the keyring. The consequence is that every time the user logs in he/she is prompted for the keyring password to access the wireless password. I've heard that if the keyring password is the same as the user account password the prompt will go away, but I have no idea how to change the keyring password. Thanks for any help!

---

### Post by iaculallad on 2009-03-23
Try the command below:

```
mv ~/.gnome2/keyrings/default.keyring ~/.gnome2/keyrings/default.keyring.old
```

---

### Post by pkulak on 2009-03-23
> **iaculallad said:**
> Try the command below:

```
mv ~/.gnome2/keyrings/default.keyring ~/.gnome2/keyrings/default.keyring.old
```

Ah, so I just wipe it and start over. Makes sense. Thanks!

---

### Post by mcduck on 2009-03-23
You can also do that with the keyrings & passwords manager:

1. Open Applications/Accessories/Passwords and Encryption keys.
2. Go to Edit/Preferences.
3. On the password Keyrings-tab select the "login"-keyring and click "Change Unlock Password"

---

### Post by Flag on 2009-03-23
Leave new password blank if you don't want to type passwords all the time.

---

### Post by mcduck on 2009-03-23
> **Flag said:**
> Leave new password blank if you don't want to type passwords all the time.

This is usefull if you are using automatic login. But with normal login it's enough to set the keyring password to same as the login password, the keyring will be automatically unlocked when logging in without having to re-type your password.

---

