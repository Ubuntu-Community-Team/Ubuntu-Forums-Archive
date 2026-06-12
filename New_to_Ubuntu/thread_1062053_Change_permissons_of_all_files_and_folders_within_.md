---
title: "Change permissons of all files and folders within folder (/var/www/phpmyadmin)"
date: 2009-02-06
forum: New to Ubuntu
---

### Post by makescents on 2009-02-06
Hello,

I've recently installed Ubuntu Desktop edition with the hope of testing SSL on a site I have created.

I followed this guide ([http://www.drakefire.com/?p=39](http://www.drakefire.com/?p=39)) but problems started at the permissions stage.

I found a thread that told me to run this in the terminal

```
sudo chown your-user-name /var/www/
```

I did and it worked however when I run this

```
sudo chown your-user-name /var/www/phpmyadmin/
```

It unlocks write permissions to the folder but not to any of the files inside.

Also while I am here, is there a newbie guide to installing, self signing and testing SSL certificates?

Thanks in advanced :)

---

### Post by taurus on 2009-02-06
```
sudo chown -R *your-user-name* /var/www/phpmyadmin
```

That would change the ownership of all files/directories under /var/www/phpmyadmin to whatever you put in for *your-user-name*.

---

### Post by ilovesocks on 2009-02-06
In order for chown to descend into a folder, you need to give it the -R (recursive) option. So your command becomes
```
sudo chown -R your-user-name /var/www/phpmyadmin/
```

---

### Post by GMachine_24 on 2009-02-06
Technically speaking

chown changes ownership of a file/folder (which can indirectly change your permissions or the permissions of whichever user you choose)

chmod changes permissions

More information is available on each by using

```


man chown

man chmod


```

---

