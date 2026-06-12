---
title: "LAMP - Trouble with phpmyadmin"
date: 2011-03-28
forum: New to Ubuntu
---

### Post by paulmr1968 on 2011-03-28
Hello,

I instead all of the LAMP applications/modules.  Also, I installed phpmyadmin.

However, I couldnt get phpmyadmin to show up in my web browser.  So I read another installation wiki and it said to NOT do a dbconfig-common.  And Im pretty sure I said YES to that.

So I try to remove phpmyadmin.  I didnt realize another window pops up to ask if i want to undo the dbconfig-common.  The remove package hangs on that request (at least thats what I thought.. reality was I didnt respond to the prompt).  So I close down the software center.  

Now I cant remove phpmyadmin cause of an error with the software package.  And I can figure out the terminal command.

Anyway, I refresh my Firefox tab that was on phpmyadmin and now it works.  Only now, it says I cant load the mycrypt extension.  Please check your PHP configuration.

So, do I still need to remove phpadmin?
Do I need to fix it?

Where am I? lol

---

### Post by wojox on 2011-03-28
See if it will let you redo it:

```
sudo dpkg-reconfigure -plow phpmyadmin
```

---

### Post by paulmr1968 on 2011-03-29
Didn't allow me.

5: Can't open /usr/share/dbconfig-common/dpkg/prerm.mysql

Thoughts?

---

