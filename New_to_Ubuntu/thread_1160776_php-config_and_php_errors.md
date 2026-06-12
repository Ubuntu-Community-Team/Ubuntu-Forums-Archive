---
title: "php-config and php errors?"
date: 2009-05-16
forum: New to Ubuntu
---

### Post by disappearedng on 2009-05-16
Hey everyone
I did a apt-get install php-config only to find that php-config doesn't exist in my paths. 

```

$whereis phpconfig
php-config: 

```

What's going on? 

also I am getting these errors:

```

[disappearedng@disappearedng-desktop:/]$ php
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20060613+lfs/gd.so' - /usr/lib/php5/20060613+lfs/gd.so: cannot open shared object file: No such file or directory in Unknown on line 0
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20060613+lfs/pdo_pgsql.so' - /usr/lib/php5/20060613+lfs/pdo_pgsql.so: cannot open shared object file: No such file or directory in Unknown on line 0
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20060613+lfs/pdo_sqlite.so' - /usr/lib/php5/20060613+lfs/pdo_sqlite.so: cannot open shared object file: No such file or directory in Unknown on line 0
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20060613+lfs/pgsql.so' - /usr/lib/php5/20060613+lfs/pgsql.so: cannot open shared object file: No such file or directory in Unknown on line 0
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20060613+lfs/sqlite.so' - /usr/lib/php5/20060613+lfs/sqlite.so: cannot open shared object file: No such file or directory in Unknown on line 0

```

any idea how to fix this?

---

### Post by disappearedng on 2009-05-16
please note that I am using this with another application which requires a path to the php-config binary

---

### Post by disappearedng on 2009-05-16
bump?

---

### Post by Veerappan on 2009-06-10
I had this same problem, and tracked it down to leftover files in /etc/php5/conf.d

I used to have apache/php running together on this machine, along with sqlite*, but then I removed them later.  The config files weren't cleaned up when I removed these packages.

I removed the php5* packages, and then nuked /etc/php5, and then reinstalled php5-cli.  Error messages are gone now.  It's probably not a correct solution (dpkg probably hates me now), but it worked.

---

### Post by bodhi.zazen on 2009-06-10
There are several potential sources of those errors. In general your php (php.ini) is misconfigured.

This ranges from improper path to improper config to improper permissions.

To solve the problem we need to know how you installed php and what extensions you are using.

@Veerappan

usually better to :

```
apt-get remove --purge php
sudo apt-get install php5-cli
```

Rather then manually deleting the configuration files manually.

---

### Post by Veerappan on 2009-06-10
> **bodhi.zazen said:**
> 
usually better to :

```
apt-get remove --purge php
sudo apt-get install php5-cli
```

Rather then manually deleting the configuration files manually.

Yeah, I realize that deleting them by hand is not the proper removal method.  I thought I remembered purging php* and those files still sticking around, which is why I deleted them by hand, but my memory could be flawed...

---

### Post by bodhi.zazen on 2009-06-10
Ah.

When removing a package, foo

```
apt-get remove foo
```

leaves all the config files in place, and sometimes .foo in home.

```
apt-get remove --purge foo
```

removes the config files too (well at least in theory). Files in $HOME often need to be deleted manually.

At any rate, my advice so that you do not break dpkg (apt) is to try purging and re-installing next time this comes up.

After purging you should be able to manually remove files at will (in theory at least).

---

