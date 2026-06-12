---
title: "Users &amp; Groups"
date: 2009-07-22
forum: New to Ubuntu
---

### Post by rideburton56 on 2009-07-22
Hi All,

I have sucessfully infiltrated another windows box, and did a dual boot install of 9.04 on the family computer (MUHAHAHA).  Id like to set each user up with a Username and Password, which will provide them with all the capability that I have (for example, being able to sudo and do anything w/ a pass, but always being prompted for a password to say, install packages). It is my understanding this is a big part of why Ubuntu is so secure.  When I go to add a new user, it has a pulldown to be either a desktop user or an admin.  Which would be better for everyone?

---

### Post by bacil on 2009-07-22
your users will have to be admin if you want them to use sudo

or you can add them individually in to /etc/sudoers

---

### Post by rideburton56 on 2009-07-22
Am I increasing the security risk by doing this?  I am not concerned with my family members viewing my files, but with creating a security risk by having more than one admin.

---

### Post by poosietgp on 2009-07-22
i think its better if you set them as users only, that way you will not encounter problems such as family members misconfiguring your machines, well, based on my experience family members are always a security threat :).

---

