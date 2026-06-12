---
title: "User privileges guide"
date: 2011-06-23
forum: New to Ubuntu
---

### Post by ligiopro on 2011-06-23
On the default account that Ubuntu creates for the first user, it seems that there are privileges (enabled or disabled) that contradict with what the user can actually do. For example, I see that the "connect to wireless and ethernet networks" is unchecked, yet the user is able to connect to such networks. 
"Use audio devices" is also unchecked, but sound is working fine.
Etc.

---

### Post by blazemore on 2011-07-01
That kind of permission is set by groups.

If you install a distro like Arch, you really won't be able to use sound devices unless you're part of the sound group, etc.

On Ubuntu, these groups still exist (and they're descriptions are displayed in the users and groups tool) but the default group has all these permissions anyway, which is why you can connect to your network.

---

### Post by ahears on 2011-07-01
> **ligiopro said:**
> On the default account that Ubuntu creates for the first user, it seems that there are privileges (enabled or disabled) that contradict with what the user can actually do. For example, I see that the "connect to wireless and ethernet networks" is unchecked, yet the user is able to connect to such networks. 
"Use audio devices" is also unchecked, but sound is working fine.
Etc.

That is because you are the Administrator,  as a part of the 'admin' group your account has access to everything.

---

### Post by blazemore on 2011-07-02
> **ahears said:**
> That is because you are the Administrator,  as a part of the 'admin' group your account has access to everything.

Except the ability to run commands as root without a password.

---

