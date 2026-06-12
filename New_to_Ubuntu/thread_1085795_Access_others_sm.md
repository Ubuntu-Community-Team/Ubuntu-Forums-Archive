---
title: "Access others s/m"
date: 2009-03-03
forum: New to Ubuntu
---

### Post by navaneethan on 2009-03-03
Friend i need the information to access the othersystem using ssh command....i don't know the password for root..i know the user password only...how can i derive the root permissinons to user....as well as how can i control other system...

---

### Post by albandy on 2009-03-03
are you the administrator of the two computers?

---

### Post by navaneethan on 2009-03-03
> **albandy said:**
> are you the administrator of the two computers?

No i am **user** of both my friend

---

### Post by jdong on 2009-03-03
You mean, how to gain root access on a system without permission to do so?

---

### Post by albandy on 2009-03-04
Your user should be in the adm and admin groups, so if the system administrator don't add your user to that groups you can't use administration commands

---

### Post by navaneethan on 2009-05-09
I am in guest accout for example in ubuntu some nautilus commands are used to get the root permission similar way what the thing need to get root permission in fedora,redhat whthout root password

---

### Post by jdong on 2009-05-10
The guest account is hardened by Mandatory Access Controls through an AppArmor profile. Even gaining root under the guest user is useless -- it has no more access than the guest user itself.

---

