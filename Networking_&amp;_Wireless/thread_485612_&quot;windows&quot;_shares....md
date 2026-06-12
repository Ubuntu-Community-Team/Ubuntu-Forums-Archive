---
title: "&quot;windows&quot; shares..."
date: 2007-06-27
forum: Networking &amp; Wireless
---

### Post by agent154 on 2007-06-27
I've managed to find out how to create a share using smb, however when I try to access it from my windows box, it asks for a login/pass and the one I use to login on Ubuntu doesn't work. Where do I access the login info?

---

### Post by yota on 2007-06-27
Hi,

you can add samba users with
```

smbpasswd -a <username>

```
quote from 'man smbpasswd'
> 

 -a This option specifies that the username following should be added to
          the local smbpasswd file, with the new password typed (type  <Enter>
          for  the  old password). This option is ignored if the username fol&#8208;
          lowing already exists in the smbpasswd file and it is treated like a
          regular  change password command. Note that the default passdb back&#8208;
          ends require the user to already exist in the system  password  file
          (usually /etc/passwd), else the request to add the user will fail.


or you can just disable password checks and make a public share:
[http://ubuntuforums.org/showthread.php?t=473970](http://ubuntuforums.org/showthread.php?t=473970)
(look specifically at the security=share part)

Hope this helps!

---

