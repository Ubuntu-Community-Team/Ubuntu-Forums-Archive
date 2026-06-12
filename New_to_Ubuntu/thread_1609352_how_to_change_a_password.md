---
title: "how to change a password"
date: 2010-10-30
forum: New to Ubuntu
---

### Post by pk28831 on 2010-10-30
In the past I had difficulties in changing the password vi System/administration/users_and_groups.
Via th forum I found the answer was changing the password via /applications/Accessories/Password_and_encryption_keys.
This worked, but I want to change my password again. How to proceed, as I do not see any edit button.
There are 2 encrypted passwords in the window, one for desktopcouch_user_identification: basic and one for desktopcouch_user_identificatin: oauth
Perhaps I do not read the manual pages in the right way, but how can I change my password? 
Peter

---

### Post by Mark Phelps on 2010-10-30
Why not just go through System --> Administration --> Users and Groups, Password -- change.

---

### Post by lotharmat on 2010-10-30
Or just use 

```
passwd
```

from a terminal!

---

### Post by pk28831 on 2010-10-30
Thanks for your quick reply, but it seems that the problem is that my password, as under Windows XP is 11 characters long, not 8characters.
Mark Phelps,
I tried this, but the system hangs, as the password is more than 8 characters long, this was also the case in Kubuntu.
Iotharmat,
passwd also only takes probably 8 characters, as I only changed characters 9-11 and got the message that the old and new passwords were identical
Under windows, I have no problems changing the last 3 characters.

---

### Post by CharlesA on 2010-10-30
> **lotharmat said:**
> Or just use 

```
passwd
```

from a terminal!

Doing that instead of using the GUI doesn't change the keyring password IIRC.

---

