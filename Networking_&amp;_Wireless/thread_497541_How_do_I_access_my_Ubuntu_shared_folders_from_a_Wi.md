---
title: "How do I access my Ubuntu shared folders from a Win machine?"
date: 2007-07-10
forum: Networking &amp; Wireless
---

### Post by mjpatey on 2007-07-10
Actually 2 questions...

How do I access folders/files on my Ubuntu machine from my Windows machines?  For some reason, I can access other computers' files from my Ubuntu machine just fine, but not the other way around.

And... my Ubuntu machine has a printer attached.  How do I print to it from my Windows machines?

Thanks!

-Mark

---

### Post by twistedtwig on 2007-07-10
you can use Samba to do shares to the windows SMB fingy (client / protocol)

I believe you can share the printer with Samba as well but never done that

---

### Post by mjpatey on 2007-07-10
Any idea how I do that?

---

### Post by mjpatey on 2007-07-10
OK, I just installed Samba.  But when I try to access an Ubuntu shared folder from a Windows machine on the network, it asks me for a username and password.  Any idea how to find out what those are?

I tried my Ubuntu login info, but that wasn't it.

-Mark

---

### Post by Nythain on 2007-07-10
google samba setup for answer to the login and password issue.

if you want to remove that alltogether edit your /etc/samba/smb.conf and change
```

security=user

```to
```

security=share

```
you might have to make a few other adjustments overall... hell i had to scrap the entire smb.conf and create a new VERY minimal one to get my networking working how i wanted it

---

