---
title: "gpasswd"
date: 2011-08-31
forum: New to Ubuntu
---

### Post by teklu on 2011-08-31
the root can give adminstrator previlage for the user for his own private group with

gpasswd -A "username" "userprivategroupname"

how can the root take the adminstrator previlage from this user .

i try gpasswd -M 
                    -r

any body have idea how to do this?

---

### Post by Rex Bouwense on 2011-08-31
Check here:
[https://help.ubuntu.com/8.04/serverguide/C/user-management.html](https://help.ubuntu.com/8.04/serverguide/C/user-management.html)

---

### Post by Wim Sturkenboom on 2011-08-31
From the man page
-d to delete the user
next
-a to add him/her again

Never tried it, but I think it should work.

---

### Post by sisco311 on 2011-08-31
> **teklu said:**
> the root can give adminstrator previlage for the user for his own private group with

gpasswd -A "username" "userprivategroupname"

how can the root take the adminstrator previlage from this user .

i try gpasswd -M 
                    -r

any body have idea how to do this?

Hi, and welcome to the forums!

"username" must be a comma separated list of users. If you want to remove all users from the administrators, you can leave it empty:
```
gpasswd -A '' groupname
```

If you have more administrators: admin1,admin2,admin3 and want to remove admin1 you can run:
```
gpasswd -A "admin2,admin3" groupname
```

The same applies for the members.

Alternatively, as root, you can edit the gshadow file manually. Use the vigr command:
```
vigr -s
```
or if you want to use another editor:
```
EDITOR=nano vigr -s
```

---

