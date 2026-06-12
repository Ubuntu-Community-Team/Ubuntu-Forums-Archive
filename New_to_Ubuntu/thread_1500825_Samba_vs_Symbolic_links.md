---
title: "Samba vs Symbolic links"
date: 2010-06-03
forum: New to Ubuntu
---

### Post by taihlo on 2010-06-03
I have recently moved my file shares from Windows to Ubuntu and I am trying to lock down some security settings.  I have a private directory that was locked down with Windows ntfs settings.  I couldn't figure out how to do that with linux, so I made a separate directory for that private folder, and created a symbolic link from the original directory.  When I shared the original directory, I see the Private subfolder, but can't access it from a windows machine... 
I know I am new to linux file system level stuff... so If I am totally off base here, somebody please let me know how to do this properly!!!

what I am looking for is this:
(remember the clients are both linux and windows xp machines)

**shared folder** --- everyone has access via samba share
   |
    -- **Private Folder** --- only one user has access at all

*** just a point to say thank you, this is the first linux question, I have not been able to answer by poking around the forums... it's been 5 years ;-)

---

### Post by pricetech on 2010-06-03
That shouldn't require any more than sharing your private folder and restricting access to your user account.

System - Administration - Samba  should get you there.

---

### Post by airtonix on 2010-06-04
> **pricetech said:**
> That shouldn't require any more than sharing your private folder and restricting access to your user account.

System - Administration - Samba  should get you there.

That menu entry is only available if you install the system-config-samba package : 

```
sudo apt-get install system-config-samba
```

---

### Post by taihlo on 2010-06-04
That did the trick!, I knew I was doing something more complicated than it needed to be...
Thank you !!!

---

### Post by pricetech on 2010-06-04
> **airtonix said:**
> That menu entry is only available if you install the system-config-samba package 

True.  Bad assumption on my part, and I should remember better since I'm in the middle of setting up more than one Lucid system with Samba, among other things.

---

