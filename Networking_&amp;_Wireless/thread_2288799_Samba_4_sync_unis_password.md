---
title: "Samba 4 sync unis password"
date: 2015-07-30
forum: Networking &amp; Wireless
---

### Post by corsairetc on 2015-07-30
Hello, when I type testparm for samba I always get the error:
```
ERROR: the 'unix password sync' parameter is set and there is no valid 'passwd program' parameter.


```
In conf file I had passdb backend = smbpasswd
Where's should be the problem.
Thank you for help.

---

### Post by bab1 on 2015-07-30
> **corsairetc said:**
> Hello, when I type testparm for samba I always get the error:
```
ERROR: the 'unix password sync' parameter is set and there is no valid 'passwd program' parameter.


```
In conf file I had passdb backend = smbpasswd
Where's should be the problem.
Thank you for help.
Why did you change this parameter from the default setting of```

 passdb backend = tdbsam

```
This parameter sets the backend storage type for user information.  The parameter *smbpasswd* is not one of the options available.  Read the man pages```
man smb.conf
```

If this is just a standalone file server, the default parameter should be good enough.

---

