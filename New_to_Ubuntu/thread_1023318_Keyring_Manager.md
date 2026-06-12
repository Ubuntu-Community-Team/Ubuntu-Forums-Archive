---
title: "Keyring Manager"
date: 2008-12-27
forum: New to Ubuntu
---

### Post by strangelymade on 2008-12-27
What is it exactly and what is it for?

---

### Post by Coder543 on 2008-12-27
Please be more specific. Are you talking about the "Passwords and Encryption Keys" or the "Encryption and Keyring" or the firefox keyring manager, or another third part app? The first two deal with file encryption the firefox manages online passwords...

---

### Post by strangelymade on 2008-12-27
When you click on System > Administration there is something called Keyring Manager (On my list it's just under Firestarter and above Language support, just wondered what it was for and what it did.

---

### Post by polmir on 2008-12-27
Type in terminal:```
apt-cache search keyring manager
```

```
apt-cache show  gnome-keyring-manager
```

More information can be found in:```
man apt-cache
apt-cache -h
man man
```

---

