---
title: "What if I deleted vsftpd from etc/init.d?"
date: 2009-03-12
forum: New to Ubuntu
---

### Post by formidable on 2009-03-12
I wanted to completely remove and then re-install vsftpd from my Ubuntu box.  After uninstalling using apt-get (and even re-booting) I noticed that vsftpd still showed up in the service manager.  That didn't make any sense, so I looked for a way to get rid of it.  I looked in /etc/init.d and saw that vsftpd was still there, so I deleted it. 

Now that I've re-installed vsftpd, it won't work. The vsftpd file is not in /etc/init.d and it isn't showing up in the Services Manager.  

Have I broken something or am I missing something obvious?  I've tried re-re-installing.  Removing and re-installing.  No luck.  

Thanks.

---

### Post by ptn107 on 2009-03-12
Did you try:
```
sudo apt-get remove --purge --auto-remove vsftpd -y
```

before reinstalling:
```
sudo apt-get install vsftpd -y
```

---

### Post by formidable on 2009-03-12
All better now. You rock.

Thanks.

---

