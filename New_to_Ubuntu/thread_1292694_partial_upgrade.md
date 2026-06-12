---
title: "partial upgrade"
date: 2009-10-16
forum: New to Ubuntu
---

### Post by DarinB on 2009-10-16
I have a clean install of jaunty, everything seems to be running ok for the last few weeks. 
when i get the security updates i also get a window that says partial upgrade i usually close it and add the security updates then click the partial upgrade and it comes back you are up to date. what is this anoying extra window, i do use .11 kernel had problems with .15 on my computer. is that why i get that? or another thing going on??

---

### Post by dvlchd3 on 2009-10-16
I know I received that message for certain updates coming from the Backports repo.  Even when I allowed it to do the partial upgrade, the upgrade always failed.

To get rid of it, I simply upgraded from the command line:

```

sudo apt-get upgrade

```

---

### Post by DarinB on 2009-10-19
If i do an upgrade with the command line it will upgrade my firefox and i had major problems with 3.52 i want to stay with 3.014.

---

### Post by Nesaskewatch on 2009-10-19
See here;

[http://ubuntuforums.org/showthread.php?t=1286309](http://ubuntuforums.org/showthread.php?t=1286309)

Not sure if this applies to Karmic only, but safe is as safe does...

---

### Post by CaptainMark on 2009-10-19
sudo apt-get upgrade shouldnt update firefox on jaunty unless you specify you want it to or youve added firefox repos, ive just run this command and im in firefox 3.0.14, why dont you run the command and see what it tells you will be upgraded because you can always pullout once it tells you which packages are about to be upgraded

---

