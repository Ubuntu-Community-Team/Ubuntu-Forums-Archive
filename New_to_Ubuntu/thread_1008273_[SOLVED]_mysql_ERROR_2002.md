---
title: "[SOLVED] mysql ERROR 2002"
date: 2008-12-11
forum: New to Ubuntu
---

### Post by Papa_Bear on 2008-12-11
Hello. I've just installed mysql using apt-get but when I type *mysql -u root* the terminal says: 
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

I've checked the /var/run/mysqld/ and nothing is in there.

What should I do?

---

### Post by bluefrog on 2008-12-11
is mysql-server installed?

what's the output of
dpkg -l mysql* | grep ii | awk '{ print $2 }'

---

### Post by albandy on 2008-12-11
type mysql -u root -p
and like said bluefrog, are you sure you've installed mysql-server package?

---

### Post by Papa_Bear on 2008-12-11
Hey, thanks for replying.

The output of dpkg -l mysql* | grep ii | awk '{ print $2 }' is:

mysql-client-5.0
mysql-common
mysql-server
mysql-server-5.0

When I type mysql -u root -p the terminal asks me for a password, but I still haven't entered a password for mysql. When I type a random password I get the same ERROR 2002 message...

---

### Post by bluefrog on 2008-12-11
sudo invoke-rc.d mysql restart

and what's the output of that? any errors?

---

### Post by Papa_Bear on 2008-12-11
I don't know if it is worth mentioning but I changed the bind-address in the my.cnf file into my ip address.:confused:

---

### Post by Papa_Bear on 2008-12-11
Thanks for helping man.. This is it's output:

 * Stopping MySQL database server mysqld                         [ OK ] 
 * Starting MySQL database server mysqld                         [fail] 
invoke-rc.d: initscript mysql, action "restart" failed.

---

### Post by albandy on 2008-12-11
If there's no data reinstall it

---

### Post by bluefrog on 2008-12-11
then change it back to 127.0.0.1 and see what it does from there.

---

### Post by Papa_Bear on 2008-12-11
I've tried reinstalling it but I got the same results.
I've changed the bind-address back but I still get the same error.

Isn't there something I should put in the /var/run/mysqld ?

---

### Post by bluefrog on 2008-12-11
dpkg -l mysql* | grep ii | awk '{ print $2 }' | sudo xargs apt-get remove --purge -y && sudo apt-get install mysql-server

---

### Post by Papa_Bear on 2008-12-11
Alright! Thanks bluefrog! I've got it running now. Hehehe.:guitar:

---

### Post by peternz on 2008-12-16
Bluefrog, worked for me too.

Genius.

SLightly worried that I don't understand the commands I just put my server through, but it's a small price to pay.  :)

---

### Post by bennis on 2009-03-15
Never mind, forgot about page two...

---

