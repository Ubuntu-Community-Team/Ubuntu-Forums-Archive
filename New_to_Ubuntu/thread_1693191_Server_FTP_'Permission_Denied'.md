---
title: "Server FTP 'Permission Denied'"
date: 2011-02-22
forum: New to Ubuntu
---

### Post by bigmonmulgrew on 2011-02-22
Hi guys.
I'm setting up a web server using ubuntu server 10.10 and apache2

I can access the server using fireFTP and view the directory structure but when I try to copy files to it I get "Permission Denied" error.

The directory I'm trying to copy to is /var/www/me.co.uk

I'm guessing I need to setup some access permissions but I dont know how.

Any help would be appreciated.

---

### Post by bigmonmulgrew on 2011-02-22
Ok I have managed to solve this but I'm not convinced the fix is a good idea. I've asked advice about that in anothe rthread but for now heres the solution

```
sudo chmod g+rwx /folder
```

This gives me access to copy the files over. I'm sure opening up access is a bad idea though.

---

