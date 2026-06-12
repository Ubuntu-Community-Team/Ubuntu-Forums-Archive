---
title: "Upgrade to 9.4 lost username and/ or password"
date: 2009-06-22
forum: New to Ubuntu
---

### Post by suebaby41 on 2009-06-22
When I upgraded to 9.4, I am unable to log on.  The user name I thought I had and the password does not work.

What can I do?

---

### Post by Bodsda on 2009-06-22
> **suebaby41 said:**
> When I upgraded to 9.4, I am unable to log on.  The user name I thought I had and the password does not work.

What can I do?

Hi, when you boot up you see the menu (Grub) choose the single user mode/ recovery mode (probably the second one). This will bring you to a terminal menu, from there choose to access a root shell, when you have the prompt enter the following command.```
passwd <<name>
``` where <name> is the name of the user you wish to change the password for, for example if I had the username 'dave' I would use```
passwd dave
```

Hope this helps

Regards,

Bodsda

---

### Post by suebaby41 on 2009-06-22
Thanks.

---

