---
title: "Active Directory"
date: 2010-06-08
forum: New to Ubuntu
---

### Post by rick_arnold on 2010-06-08
Is it possible to make 10.4 join a Windows AD network?
 
Thanks,
 
Rick

---

### Post by fatality_uk on 2010-06-08
GUI > If you look in the software centre for an application called LikeWise.

CLI > From the terminal, enter ```
sudo apt-get install likewise-open
```

Once installed, run it and you need the FQDN for the AD server. Just add the username and password. You might need to add the FQDN before the user name in some circumstances such as *domainname.local.com/username*

---

