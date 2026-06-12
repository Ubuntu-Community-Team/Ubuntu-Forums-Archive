---
title: "Apache authentication"
date: 2009-07-05
forum: New to Ubuntu
---

### Post by ltwinner on 2009-07-05
Ive got LAMP setup on my laptop and Im trying to get apache authentication working. When I try to create the password with htpasswd it fails -

When I type:
htpasswd -c /var/passwords/.password john

I get:
htpasswd: cannot create file /var/passwords/.password

Anyone know what could be going wrong?

---

### Post by Boondoklife on 2009-07-05
are you running that as a user that has rights to that folder? try adding sudo to the front of it.

---

### Post by ltwinner on 2009-07-06
yes Im am running it as root.

---

