---
title: "Can't install ubuntu 9.04 on Windows 7 with Wubi"
date: 2010-02-15
forum: New to Ubuntu
---

### Post by smorton on 2010-02-15
I am trying to install ununtu on a windows 7 machine.  I keep getting this message:

wubi installer’s pyrun.exe says “no disk”

I can't go any further.  Any ideas?

Thanks

SM

---

### Post by NightwishFan on 2010-02-15
Are you installing from the CD or the standalone installer? Try the other either one you are using.

---

### Post by philinux on 2010-02-15
> **smorton said:**
> I am trying to install ununtu on a windows 7 machine.  I keep getting this message:

wubi installer’s pyrun.exe says “no disk”

I can't go any further.  Any ideas?

Thanks

SM

You cant at the moment.
[http://wubi-installer.org/](http://wubi-installer.org/)

> Requirements
Memory 384 MB memory
Harddisk Space 5 GB harddisk space
Operating System Windows 98, 2000, XP, Vista


---

### Post by smorton on 2010-02-15
I have Wubi both on the computer and in a flash.  I have ubuntu on an ISO on the computer and in a CD form.  Can't get around this any way I try.

Thanks

SM

---

### Post by NightwishFan on 2010-02-15
I suppose 7 support is a work in progress then? Then please disregard my earlier post.

---

### Post by smorton on 2010-02-15
> **NightwishFan said:**
> Are you installing from the CD or the standalone installer? Try the other either one you are using.

So I can install on Windows 7?  With Wubi?

Thanks

SM

---

### Post by NightwishFan on 2010-02-15
Read the above posts.

---

### Post by smorton on 2010-02-15
> **NightwishFan said:**
> Read the above posts.

I don't mean to be obtuse, but your post implies that ubuntu can be installed on Windows 7.

---

### Post by NightwishFan on 2010-02-15
I assumed it could, and was corrected by the above poster. It seems that Windows 7 support does not exist yet.

---

### Post by smorton on 2010-02-15
Thanks.

SM

---

### Post by Mark Phelps on 2010-02-16
From what I've read in these forums, it's the combination of the following that prevents Wubi installation from working in Win7:
1) Win7 preinstalled -- using the new two-partition method
2) Ubuntu 9.10 installation -- using GRUB2 by default

However, I do remember seeing posts where people WERE able to install Ubuntu using Wubi into Win7 providing the following were true:
1) Win7 only installed into one partition -- no separate boot partition
2) Ubuntu 9.04 -- using legacy GRUB by default

And yeah, all these months later, the Wubi Guide has STILL not been updated to provide definitive info regarding Win7 support -- or the lack thereof.

---

