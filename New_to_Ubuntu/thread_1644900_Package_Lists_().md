---
title: "Package Lists (?)"
date: 2010-12-13
forum: New to Ubuntu
---

### Post by jonjon0789 on 2010-12-13
I'm on 10.10 amd64 and I'm using SBackup to backup my system.  I've completed my first backup, but if I can access and copy the "source.list" file under my software sources, isn't there a similar file for Synaptic or Aptitude Package Managers?  It would be helpful to not only have "sources.list" but a package list as well... just in case I get too happy with GParted again :)   

Also, what are some suggested files that I should be (or should not be) backing up?

Thanks for any help  :)

---

### Post by A_M_S on 2010-12-13
I'm not sure if this is what you want

you can find a list of the installed files in you system in

/var/log/dpkg.log       (the most recent file)
/var/log/dpkg.log.1
/var/log/dpkg.log.2.gz
        .
        .


Hope that helps

---

