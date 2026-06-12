---
title: "samba force chmod no matter what is happening?"
date: 2008-04-07
forum: Networking &amp; Wireless
---

### Post by Guenter on 2008-04-07
is there anyway to force explicit the creation mode of files on samba shares?

using this config:

 ```
  create mask = 0000
   directory mask = 0000
   force create mode = 0660
   force directory mode = 0770
   security mask = 0770
```

works perfectly on directories, but files are always created rw-r--

i thought "force create mode" should handle this?

---

### Post by Eiríkr on 2008-04-07
From the man page section for [force create mode]("http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#FORCECREATEMODE"):
> The modes in this parameter are bitwise 'OR'ed onto the file mode after the mask set in the create mask parameter is applied.

While this would seem to override the "create mask" value, it's possible that the man page isn't fully correct (or that my interpretation isn't), so try setting the "create mask" value to 0770 and see if that does the trick.

Also, it sounds like you don't need the [security mask]("http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#SECURITYMASK") option:
> This parameter controls what UNIX permission bits will be set when a Windows NT client is manipulating the UNIX permission on a file using the native NT security dialog box.

...

Administrators of most normal systems will probably want to leave it set to 0777.

HTH,

Eiríkr

---

