---
title: "what system files to backup?"
date: 2010-04-14
forum: New to Ubuntu
---

### Post by Achilles124 on 2010-04-14
Just for security if something goes wrong, what system files should I backup?

---

### Post by mbzn on 2010-04-14
For beginners like myself you could try Backintime which has a gui. in most cases your home folder is all you need to worry about accept for if you have custom config files.

---

### Post by Paqman on 2010-04-14
I wouldn't worry too much about system files, as it's so easy to reinstall. Just make sure your data and your whole home folder are safe.

About the only system stuff i'd bother to back up would be /etc/fstab and a list of your installed packages. Maybe a copy of /opt if you've installed weird software into it.

---

### Post by plucky on 2010-04-14
```
/var/cache/apt/archives/
``` is where all the installed packages are stored.
Saves having to download again if you have to re-install the system,but probably only worth it if you have bandwidth restrictions.

Good Luck

---

### Post by HermanAB on 2010-04-14
Howdy,

Backing up the whole gawddamm system is a very Windowsy way of doing things.

The only system stuff I ever bother backing up is /etc:
$ sudo tar -zcvf etc.tgz /etc

and I only do that for future reference in case there is some special server settings (like Samba, Postfix or Apache) which I may need to refer to again. I never actually untar the whole ball of wax again.

Installing the whole system from scratch only takes about 30 minutes, so spending hours backing up the whole system is a total waste of time.  Only backup your data.  You don't need to backup anything else really.

---

### Post by Achilles124 on 2010-04-14
Thank you for your replies.:)

---

