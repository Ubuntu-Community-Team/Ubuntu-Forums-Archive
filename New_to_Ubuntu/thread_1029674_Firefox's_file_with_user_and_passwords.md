---
title: "Firefox's file with user and passwords"
date: 2009-01-03
forum: New to Ubuntu
---

### Post by rootk1t on 2009-01-03
Hello,

Firefox crashed after a upgrade. The point is I want to install 8.10 version (I have 8.04), but I don't remember all my sites with users and passwords that were remembered by the old firefox.

Is there a way to see the file with all the stored users and passwords?

Thank you!

---

### Post by Michael.Godawski on 2009-01-03
hi,

the password are saved in

```
/home/username/.mozilla/firefox/.....default/signonX.txt
```

but they are obfuscated, so you cannot really make use of it.

---

### Post by rootk1t on 2009-01-03
Thank you.

So after a fresh ubuntu install, if I replace the default file with this file, should I be able to read it?

PS:

Why there are many instances of this file?

root@john:/home/john# ls -l /home/john/.mozilla/firefox/dbimpox5.default/signons*
-rwxrwx--- 1 john john  6344 2008-08-23 21:43 /home/john/.mozilla/firefox/dbimpox5.default/signons2.txt
-rwxr-x--- 1 john john 12470 2008-12-31 14:19 /home/john/.mozilla/firefox/dbimpox5.default/signons3.txt
root@john:/home/john#

---

### Post by Michael.Godawski on 2009-01-03
It is worth a try, yes.

 Tell me if that worked please. Would be good to know if this is possible.

---

### Post by rootk1t on 2009-01-03
OK, i'll write down this.

---

### Post by rootk1t on 2009-01-04
> **Michael.Godawski said:**
> It is worth a try, yes.

 Tell me if that worked please. Would be good to know if this is possible.

OK, tried this and it worked.

I copied the ~/.mozilla into the live cd's /home/ubuntu/.mozilla

Dont forget to chown -R ubuntu:ubuntu /home/ubuntu/.mozilla

Allthough you must remember the old master password if you had one.

---

