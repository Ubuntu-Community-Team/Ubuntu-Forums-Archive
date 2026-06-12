---
title: "how to install backup software sources while keeping the basic ones"
date: 2009-01-28
forum: New to Ubuntu
---

### Post by rburkartjo on 2009-01-28
i used the command ray@ray-desktop:~$ sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup
to backup my software sources okay now need some help how to i install this backup and still keep the basic software sources that come with a new version of ubuntu like when 9.04 goes public. tks/cheesemaker

---

### Post by oldos2er on 2009-01-28
To restore your sources.list, just undo the previous command:
```
sudo cp /etc/apt/sources.list.backup /etc/apt/sources.list
```

 When/if you upgrade to 9.04, your sources.list will automatically be upgraded too.

---

### Post by ptn107 on 2009-01-28
The better bet is to leave the original '/etc/apt/sources.list' alone, and put any 3rd party sources in their own .list files in the '/etc/apt/sources.list.d/' folder.  This will also keep the dist upgrader from tripping if you intend to upgrade later and not clean install 9.04.

---

### Post by rburkartjo on 2009-01-28
old and ptn tks to both of you. if i am not mistaken the solved option is still not working/cheesemaker

---

