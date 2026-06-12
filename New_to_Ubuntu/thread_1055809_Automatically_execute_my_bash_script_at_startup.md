---
title: "Automatically execute my bash script at startup?"
date: 2009-01-31
forum: New to Ubuntu
---

### Post by crazyfuturamanoob on 2009-01-31
Yeah, how?

---

### Post by mhh91 on 2009-01-31
from sessions,you'll find it in the "preferences" menu :)

---

### Post by Rinzwind on 2009-01-31
Do you mean at startup of your machine? 
Have a search for 'crontab' and 'cron'.
Example website: [http://www.adminschoice.com/docs/crontab.htm](http://www.adminschoice.com/docs/crontab.htm)

Do you mean when gnome is started?
Have a search for 'gnome' and 'sessions'. And have a look  at '/system/preferences/sessions'.

---

### Post by specialcharacter on 2009-01-31
Look into /etc/rc.local

---

### Post by crazyfuturamanoob on 2009-01-31
Done.

But how about running a script right before shutting down?

---

### Post by specialcharacter on 2009-01-31
Then you need to add a script into  /etc/rc6.d/.

Best to look at the update-rc.d command for editing these.

Heres a breakdown of the rc directory's:

    * rc0.d - System Halted
    * rc1.d - Single User Mode
    * rc2.d - Single User Mode with Networking
    * rc3.d - Multi-User Mode - boot up in text mode
    * rc4.d - Not yet Defined
    * rc5.d - Multi-User Mode - boot up in X Windows
    * rc6.d - Shutdown & Reboot

I believe that rc.local is run when you log in. Can someone confirm this?

---

### Post by lswb on 2009-01-31
> **crazyfuturamanoob said:**
> Done.

But how about running a script right before shutting down?

Here is one way:

[http://lwasserm.freeshell.org/ubuntu/rcshutdown.shtml](http://lwasserm.freeshell.org/ubuntu/rcshutdown.shtml)

---

