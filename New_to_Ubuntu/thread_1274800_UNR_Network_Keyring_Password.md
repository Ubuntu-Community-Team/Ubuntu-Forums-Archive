---
title: "UNR Network Keyring Password"
date: 2009-09-24
forum: New to Ubuntu
---

### Post by sseelbinder on 2009-09-24
My Ubuntu UNR password and Network Keyring Password are different, requiring me to login to each when booting up.  How do I change my Network Keyring Password (to match my login password) so I do not need to enter both?

---

### Post by mikewhatever on 2009-09-25
Here you go [http://pherricoxide.wordpress.com/2009/02/22/ubuntu-keyring-password-change/](http://pherricoxide.wordpress.com/2009/02/22/ubuntu-keyring-password-change/)

---

### Post by sseelbinder on 2009-09-25
Thank you MikeWhatEver, this worked!

---

### Post by mikewhatever on 2009-09-25
Welcome, and welcome to the forums.:)

---

### Post by mcduck on 2009-09-25
> **mikewhatever said:**
> Here you go [http://pherricoxide.wordpress.com/2009/02/22/ubuntu-keyring-password-change/](http://pherricoxide.wordpress.com/2009/02/22/ubuntu-keyring-password-change/)

For the future reference, that's not a great way for doing it since it will also delete all keys storde in the keyring. Which could be a serious problem in case somebody has some important encryption keys etc. in their keyring..

Besides, changing the keyring password the proper way isn't hard:

1.Open the keyring manager (Applications/Accessories/Passwords and Encryption Keys)

2. Go to Passwords-tab

3. Right-click the "Passwords:login"-keyring & select "Change Password"

---

### Post by mikewhatever on 2009-09-25
Indeed, that's a much better way. Thank you.

---

