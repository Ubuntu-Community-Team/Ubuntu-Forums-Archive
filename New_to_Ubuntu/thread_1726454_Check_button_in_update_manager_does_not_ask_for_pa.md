---
title: "Check button in update manager does not ask for password"
date: 2011-04-11
forum: New to Ubuntu
---

### Post by adit on 2011-04-11
Clicking the "check" button in update manager updates my software sources without asking any password.  Clicking that button invokes the command
```
sudo apt-get update
```
in the background.  Isn't it? Then how can it update my software sources without asking for a password?

---

### Post by Grenage on 2011-04-11
> **adit said:**
> Clicking the "check" button in update manager updates my software sources without asking any password.  Clicking that button invokes the command
```
sudo apt-get update
```
in the background.  Isn't it? Then how can it update my software sources without asking for a password?

That merely updates the package listing, not your files; that would require:

```
apt-get upgrade
```

---

### Post by adit on 2011-04-11
> That merely updates the package listing, not your files
Even updating package listing requires password.  My ubuntu installation is updating my package listing without password.  How is it possible?

---

### Post by Grenage on 2011-04-11
Ah I see; I believe that was changed in a recent version (late last year?).  There will likely be a security policy in place which stops it being required for the update alone.

When using apt-get in BASH, it's probably not using this policy.

---

### Post by Ghost_Mazal on 2011-04-11
Synaptec asks for your password upon startup of the Synaptec program. Then it doesn't authenticate again when you are busy inside Synaptec.

---

