---
title: "restore the files &amp; folders  proprieties"
date: 2009-08-20
forum: New to Ubuntu
---

### Post by jrev on 2009-08-20
Hi all,

I saved the folder "my documents" onto a CD then I installed the new version of Ubuntu 9.04, erasing my hard disk.

When I restored "my documents" the files and folders were in read only permission.

By which command of chmod can I change the permission of each files and folders inside the "my documents" folder ?

Thanks for your help

---

### Post by slakkie on 2009-08-20
chmod u+w $file

Next time if you backup your files, use tar:

```

tar zcvf backup.tgz /path/to/files /path/to/another/file

```

This preserves permissions, or, you can do this, before you make the backup:

```

find $location -exec stat -c "chmod %a %n; chown %U:%G %n " {} +

```

Save the output to a file and then you can later on execute that file, giving the original permissions to those files

---

### Post by jrev on 2009-08-20
Thanks for this excellent answer !

I noted that you are still on the ubuntu 8.04 like me ...

I installed the 9.04 version but I am unable to share a dial-up internet connexion on my local network !

So I am back to the good old 8.04 :P

---

### Post by slakkie on 2009-08-20
Actually, I'm hopping back and forth between hardy (8.04) and karmic (9.10 - dev version) atm.

---

