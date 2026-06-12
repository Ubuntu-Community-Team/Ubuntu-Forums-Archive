---
title: "Problem deleting rules"
date: 2009-07-11
forum: New to Ubuntu
---

### Post by mojo_man on 2009-07-11
I have this in my ufw:

To                         Action  From
--                         ------  ----
22/tcp                     ALLOW   Anywhere
22/udp                     ALLOW   Anywhere
6667/tcp                   ALLOW   Anywhere

When I try and delete the 22/tcp and 22/udp rules I get:

mohit@mohit-desktop:~$ sudo ufw delete ALLOW 22/udp
Could not delete non-existent rule


What is going on?

---

### Post by porchrat on 2009-07-11
> **mojo_man said:**
> I have this in my ufw:

To                         Action  From
--                         ------  ----
22/tcp                     ALLOW   Anywhere
22/udp                     ALLOW   Anywhere
6667/tcp                   ALLOW   Anywhere

When I try and delete the 22/tcp and 22/udp rules I get:

mohit@mohit-desktop:~$ sudo ufw delete ALLOW 22/udp
Could not delete non-existent rule


What is going on?

How did you create those rules? If you created the rules by referencing a profile (in the case of port 22 I would imagine it was SSH) then you need to remove it by referencing that profile as well.

So for example if you created the rule using this command:
```
sudo ufw allow ssh
```
or
```
sudo ufw allow SSH
```
depending on what case it wants for the SSH profile you would use one of these to delete the rules:

```
sudo ufw delete allow SSH
```
or
```
sudo ufw delete allow ssh
```

If that doesn't help you and you can't remember the profile you used to create the rules then try using the ufw GUI package (gufw) as it will probably take care of it for you. I have never used gufw myself, but I hear it is quite good.

---

