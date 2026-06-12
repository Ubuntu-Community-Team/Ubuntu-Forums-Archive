---
title: "I installed wordpress from synaptic where is it?"
date: 2009-06-01
forum: New to Ubuntu
---

### Post by Duke Togo on 2009-06-01
the title pretty much says it all
its not on the menu or in my home folder
where is it?

---

### Post by argail1980 on 2009-06-01
did you try typing "wordpress" in a terminal?

---

### Post by slimx3m on 2009-06-01
wordpress should be run on a apache server.  so you probably want to try to go to your local host connection.

in order to do that go to your web browser and type
```
http://localhost
```

---

### Post by Duke Togo on 2009-06-02
slimx3m
I did that and got the reply

It works!

in big letters, what next

if I type wordpress into the terminal I get command not found

---

### Post by ad_267 on 2009-06-02
What do you get with the command: 

ls /var/www

---

### Post by kellemes on 2009-06-02
> **Duke Togo said:**
> slimx3m
I did that and got the reply

It works!

in big letters, what next

if I type wordpress into the terminal I get command not found

You got a little reading to do if you want to run Wordpress on your server.
[https://help.ubuntu.com/community/ApacheMySQLPHP]("https://help.ubuntu.com/community/ApacheMySQLPHP")

---

### Post by Celauran on 2009-06-02
The whereis command can be handy in cases like this, too.

---

### Post by Cypher on 2009-06-02
Assuming you have Apache/PHP/MySQL installed. You at least of Apahce installed if you get the "It works!" message, then check out these two files from the wordpress package to get further details:
```

/usr/share/doc/wordpress/examples/apache.conf
/usr/share/doc/wordpress/examples/setup-mysql

```

---

### Post by ragdoll69 on 2009-12-26
I have the same problem. Installed Wordpress as a package through synaptic.
the apache server is definately there, but there's nothing in the /var/www/ directory.
no meny entries where made at all.

---

