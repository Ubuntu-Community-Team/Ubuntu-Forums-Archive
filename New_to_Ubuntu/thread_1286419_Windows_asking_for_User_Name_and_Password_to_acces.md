---
title: "Windows asking for User Name and Password to access files over network..."
date: 2009-10-08
forum: New to Ubuntu
---

### Post by bradsthompson on 2009-10-08
I am running Jaunty on a machine with System-Config-Samba installed.  I am sharing a few folders across my home network from this machine as well.

When I try to access these folders with a laptop running Windows 7, it asks for a User Name and Password even though I have enabled Samba to share the files with "Everyone".  When I type in my Jaunty username and password, it says that it is incorrect.

Not sure what to do....

Can someone help?

---

### Post by advocate 21 on 2009-10-09
i somehow got this working on vista... did you try using the windows 7 username and password?

---

### Post by wjp.reg on 2009-10-09
> **bradsthompson said:**
> I am running Jaunty on a machine with System-Config-Samba installed.  I am sharing a few folders across my home network from this machine as well.

When I try to access these folders with a laptop running Windows 7, it asks for a User Name and Password even though I have enabled Samba to share the files with "Everyone".  When I type in my Jaunty username and password, it says that it is incorrect.

Not sure what to do....

Can someone help?

Did you happen to remember to set the samba password as required to share folders?


If not, type the following in a terminal and provide the username(s) and associated passwords you wish to use.

```
sudo smbpasswd -a username
```

Once this is done, you should be able to access your shared folders from windows after a one-time prompt for the samba username and password.

Of course your windows machine also needs to be part of the same samba workgroup, but you knew that, right ;-)

---

### Post by wjp.reg on 2009-10-16
So is this solved?  Would help others to know..

cheers

---

