---
title: "Missing &quot;Services&quot; under &quot;System - Administration&quot;"
date: 2011-01-19
forum: New to Ubuntu
---

### Post by ppwhite on 2011-01-19
I am an extreme new user.  I'm  setting up Apache and PHP on a computer running Ubuntu 10.10.  I've tested both the web server and PHP and they seem to be working.

I have no master value for date.timezone when I look at [http://localhost/testing.php](http://localhost/testing.php).  I modified the "Loaded configuration file" and changed the line ;date.timezone line (from a PHP book and looked up America/Detroit at looked this up at [http://www.php.net/timezones](http://www.php.net/timezones))

I need to restart Apache using "System - Administration - Services".  System and Administration I have.  Services is not there.

Do I need to just restart?, or is Services somewhere I'm missing?

Any help will be much appreciated!  Thanks in advance.

---

### Post by sisco311 on 2011-01-19
You don't really need a GUI for restarting services. Just use the service utility, e.g.:
```
sudo service apache2 restart
```

But, if you are using Ubuntu 10.10 and want a GUI tool, you can install jobs-admin from the repos.

EDIT:

Welcome to the forums!

---

### Post by cariboo on 2011-01-19
There are no menu commands for apache2 the way to restart it is to open a terminal and type:

```
sudo service apache2 restart
```

if you are using 10.04 or newer and:

```
sudo /etc/init.d/apache2 restart
``` 

for older versions.

---

### Post by ppwhite on 2011-01-19
Thanks!

sudo service apache 2 restart gives me a message (shortening it) "couldn't reliably determine server's fully qualified domain name), so maybe I've messed something up.  I just may start over in the morning; too late to think that much about it tonight!  :)

---

