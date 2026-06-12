---
title: "Samba Permissions Issue"
date: 2008-10-05
forum: Networking &amp; Wireless
---

### Post by naugiedoggie on 2008-10-05
Hello,

I set up a share with Samba to be read/write.  It's read-only.  I can't write to it from any other system.  The smb.conf file lists the setting of the share as 

```
browseable = yes
public = yes
available = yes
writable = yes
```

Also, I set security = share.  I even tried turning on 'guest account' and 'guest ok = yes' in the share properties.  No joy.

Isn't it a little bit useless if the share setup GUI has a checkbox for "read only" that does not make your share writeable when you uncheck it?

Now, I have another Ubuntu box on which the smb share works fine and, AFAICS, the smb.conf file there is identical to the original on this errant box.  It may be that I did something on that box to make it work, but that would have been 2 years ago or more.

I would appreciate any help in making this share writeable.

Thanks.

mp

---

### Post by patrickballeux on 2008-10-05
Try this package : system-config-samba

It helped me a lot to put the proper configuration without having to edit the configuration files by hand.


Enjoy!

---

### Post by naugiedoggie on 2008-10-05
> **patrickballeux said:**
> Try this package : system-config-samba

It helped me a lot to put the proper configuration without having to edit the configuration files by hand.


Enjoy!

Hmm, weird, well that seemed to do something.  I didn't touch a thing after the install, all I did was look at the properties page and click OK.

I hate these "mystery" solutions, though, because I still have no idea what went wrong and so how to fix it when it happens again.  But, I'm glad to be able to get the work done!

Thanks!

mp

---

### Post by Iowan on 2008-10-05
A couple of years ago would have made the version Dapper or Edgy?  Unfortunately, the "new" version of Samba may be more secure... but less convenient.  I don't understand it nearly as well.  You might try the **force user =** and **force group=** options.

---

