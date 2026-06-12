---
title: "how will i know if apache-php-mysql have been configured properly"
date: 2009-01-24
forum: New to Ubuntu
---

### Post by fuser312 on 2009-01-24
i did some googling & foolowed some tutorial (copy-paste). but now how coild i know if all of theese have been configured.

i have no experience of apache but just trying to learn it.
and yes i get the expected messages for php and apache (like "it works" for apache) but i am not sure about mysql if it has been configured properly or not.

when i run this command at terminal (as a root)  sudo /etc/init.d/apache2 start
i get this message:
 * Starting web server apache2                                                  apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
                                                                         [ OK ]
What could be the possible reason??

---

### Post by Cypher on 2009-01-24
Since you've gotten the "It works" message from Apache, that is configured. The next step is to check to see if PHP is configured and the easiest way to do that is
```

cd /var/www
sudo echo "<? phpinfo(); ?>" > test.php

```
Now point your browser to [http://localhost/test.php](http://localhost/test.php) and you should see information about your PHP installation like version, configured variables.

To check on MySQL you either need to write some code that will test it or use a software (blogging software for example) that uses it.

---

### Post by fuser312 on 2009-01-24
i know php and apache are working.
but what about the error message

---

### Post by Cypher on 2009-01-24
That error message can be ignored as long as you are testing your Apache setup on a local machine. The problem is that your machine has a name but it isn't one that is addressable from the Internet.

---

### Post by fuser312 on 2009-01-24
thanx

---

### Post by stussy on 2009-02-04
I'm new to php, mysql and apache too.  I also had the same error message but found a thread on this forum which said that I could just add the following line in apache2.conf:

```

ServerName http://127.0.0.1

```

I added the line under this line:

```

ServerRoot "/etc/apache2"

```

And it doesn't show the error anymore

---

