---
title: "Require Password to log in and decrypt home folder?"
date: 2010-05-26
forum: New to Ubuntu
---

### Post by TriBlox6432 on 2010-05-26
I've installed Ubuntu Netbook Remix 9.10

How do I make it require a password to log in and decrypt my home folder?  There was an option, but I selected Log in automatically.

---

### Post by kerry_s on 2010-05-26
look under system for login

---

### Post by bodhi.zazen on 2010-05-26
> **TriBlox6432 said:**
> I've installed Ubuntu Netbook Remix 9.10

How do I make it require a password to log in and decrypt my home folder?  There was an option, but I selected Log in automatically.

1. You have to disable automatic log in.

2. As you install, you select the option to encrypt home.

3. Post install you would need to manually configure this option.

You could either learn ecryptfs or create a new user.

[http://bodhizazen.net/Tutorials/Ecryptfs](http://bodhizazen.net/Tutorials/Ecryptfs)

new user:

```
sudo adduser --encrypt-home new_user_name
```

---

