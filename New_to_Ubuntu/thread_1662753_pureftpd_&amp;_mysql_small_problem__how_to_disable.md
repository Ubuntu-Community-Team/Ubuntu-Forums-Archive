---
title: "pureftpd &amp; mysql small problem | how to disable root login"
date: 2011-01-08
forum: New to Ubuntu
---

### Post by Faks on 2011-01-08
hi dear community problem is not serious i need to disable root login i tried searching and tried everything what I founded and couldn't locate pureftpd.conf i think it's missing :D  by the way i follow the guide [http://www.howtoforge.com/pureftpd_mysql_virtual_hosting](http://www.howtoforge.com/pureftpd_mysql_virtual_hosting) and i succeed and all works but only root problem is present .
i hope somebody can spare a bit time and help beginner to find way to resolve this issue :confused:

---

### Post by star123 on 2011-01-08
> **Faks said:**
> hi dear community problem is not serious i need to disable root login i tried searching and tried everything what I founded and couldn't locate pureftpd.conf i think it's missing :D  by the way i follow the guide [http://www.howtoforge.com/pureftpd_mysql_virtual_hosting](http://www.howtoforge.com/pureftpd_mysql_virtual_hosting) and i succeed and all works but only root problem is present .
i hope somebody can spare a bit time and help beginner to find way to resolve this issue :confused:

[http://techie-buzz.com/foss/disable-direct-root-access-logins-in-linux.html](http://techie-buzz.com/foss/disable-direct-root-access-logins-in-linux.html)
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Faks on 2011-01-08
> **star123 said:**
> [http://techie-buzz.com/foss/disable-direct-root-access-logins-in-linux.html](http://techie-buzz.com/foss/disable-direct-root-access-logins-in-linux.html)
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
ow man you didn't understand me ...
problem is simple i don't use root but i have my own user for example i have logged in with user xxx and i can login in with it in ftp but i need disable 
[http://www.itsolutionskb.com/2008/10/disable-proftp-direct-root-login/](http://www.itsolutionskb.com/2008/10/disable-proftp-direct-root-login/)
i tried this but i don't have proftpd.conf its simply missing all what i have mysql.conf :( !

---

### Post by Verbeck on 2011-01-08
> **Faks said:**
> ow man you didn't understand me ...
problem is simple i don't use root but i have my own user for example i have logged in with user xxx and i can login in with it in ftp but i need disable 
[http://www.itsolutionskb.com/2008/10/disable-proftp-direct-root-login/](http://www.itsolutionskb.com/2008/10/disable-proftp-direct-root-login/)
i tried this but i don't have proftpd.conf its simply missing all what i have mysql.conf :( !
from what i gather from the first post and the thread title, you installed _pureftpd_
that guide explains how to disable root login in [U]proftpd
[/U](they are different programs)

hope that helps

---

### Post by Faks on 2011-01-09
> **Verbeck said:**
> from what i gather from the first post and the thread title, you installed _pureftpd_
that guide explains how to disable root login in [U]proftpd
[/U](they are different programs)

hope that helps
my bad :(

---

