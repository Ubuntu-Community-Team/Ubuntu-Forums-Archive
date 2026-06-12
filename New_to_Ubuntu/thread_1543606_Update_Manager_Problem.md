---
title: "Update Manager Problem"
date: 2010-08-01
forum: New to Ubuntu
---

### Post by butters13 on 2010-08-01
Hello All, running the latest Ubuntu and when I try and run the' update manager' it asks me for my password (administrators) and i enter my root password or my normal user password and it rejects them? I enter su - in the terminal and i enter my root password and i go to root no prob... What is the prob here? The response from the window after i enter my password and am refused is 'the underlying autherization mechanism (sudo) does not allow you to run this program. Contact your Admin... Any help with this???
~k
[email]mind@themindworking.com[/email]

---

### Post by snowpine on 2010-08-01
Hi Butters, Ubuntu does not have a "root password" and if you accidentally enabled one, it is likely you broke your sudo permissions. Please see this link for how to lock the root password and restore Ubuntu default security: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

If you are having trouble using the Update Manager you can try upgrading from the terminal:

```
sudo apt-get update
sudo apt-get dist-upgrade
```

---

