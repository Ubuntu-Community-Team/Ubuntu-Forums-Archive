---
title: "OpenLDAP remove anonymous bind"
date: 2018-05-25
forum: Networking &amp; Wireless
---

### Post by abhishek-papanna on 2018-05-25
Hi All,

I have a query in LDAP. I took a long time to get olcAccess to work and setup a few access lists. Now I am using 'anonymous auth' access everywhere  I want to avoid using 'anonymous auth' and instead use bind credentials to login. But when I remove this 'anonymous auth' from olcAccess, nothing seems to work. Once this is removed none of the users are able to login except cn=admin.
Now as per request I am supposed to remove this from the configuration, but nothing seems to be working. 
Please help.

default olcAccess:
```
olcAccess: {0}to attrs=userPassword by self write by anonymous auth by * none
olcAccess: {1}to attrs=shadowLastChange by self write by * read
olcAccess: {2}to * by * read
```

What I want to achieve:
```
olcAccess: {0}to attrs=userPassword by self write by <bind_user> auth by * break
olcAccess: {1}to attrs=shadowLastChange by self write by * break
```

How can I do this? once anonymous auth is removed, none of the users will be able to login.

Thanks,

---

