---
title: "Having trouble sharing files with Samba, &quot;access denied&quot;"
date: 2009-11-18
forum: New to Ubuntu
---

### Post by westvan23 on 2009-11-18
Hello everyone,
 
I quite a new Ubuntu user and am in need of some help. I have scoured the web for help for my problem but nothing seems to help me. A lot of the smb.conf files they reference seem different than the one I am using as perhaps they relate to older version(?).
 
So anyways, I have samba installed and have set a folder to share with full permissions. I can access this folder from windows BUT i can't access files that have been created in ubuntu. Again as mentioned I've tried dozens of suggestions through web searches but nothing has worked. Any help would be greatly appreciated.
 
Thank you,
 
WVan

---

### Post by VastOne on 2009-11-18
> **westvan23 said:**
> Hello everyone,
 
I quite a new Ubuntu user and am in need of some help. I have scoured the web for help for my problem but nothing seems to help me. A lot of the smb.conf files they reference seem different than the one I am using as perhaps they relate to older version(?).
 
So anyways, I have samba installed and have set a folder to share with full permissions. I can access this folder from windows BUT i can't access files that have been created in ubuntu. Again as mentioned I've tried dozens of suggestions through web searches but nothing has worked. Any help would be greatly appreciated.
 
Thank you,
 
WVan

I too am having several issues with Windows 7 and accessing or writing to my Samba shares

I cannot browse and see any of the shares. I can only access them via \\ip address connections.  

I can write and create and delete while accessing these shares but if I try to do a backup from Windows 7 it goes to the end and then claims that access is denied even though I have seen 98% of the files on the shares.

---

### Post by westvan23 on 2009-11-18
Well personally I just became aware of system-config-samba apt and downloaded it.  I thought everything would fall into place next but not quite.  I changed the workgroup to the same and have set all permissions for the file.
 
I still am not able to access files from windows, just see the contents of the folder.  What else do I have to do?
 
Thanks,
WVan

---

