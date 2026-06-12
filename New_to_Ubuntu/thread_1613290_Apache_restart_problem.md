---
title: "Apache restart problem"
date: 2010-11-04
forum: New to Ubuntu
---

### Post by arju305 on 2010-11-04
Guys. When ever i restart the apache server, I get an error message.

$sudo /etc/init.d/apache2 restartapache2:

Syntax error on line 227 of /etc/apache2/apache2.conf: Syntax error on line 1 of /etc/apache2/conf.d/aegir.conf: Could not open configuration file /etc/aegir/vhost.d/: No such file or directory
Action 'configtest' failed.
The Apache error log may have more information.
   ...fail!

Can you tell me how this can be solved.

---

### Post by ubudog on 2010-11-04
Can you try this and see if it works?

```
sudo service apache2 restart
```

---

### Post by arju305 on 2010-11-04
> **ubudog said:**
> Can you try this and see if it works?

```
sudo service apache2 restart
```


Both the command are same. And I have the same problem. Same error repeated. I have never faced such a thing.

---

### Post by yargy on 2011-01-19
Hey I had the same issue and it I believe is caused when Aegir(for drupal) has not been fully installed.

In the Aegir installation you are supposed to create a symbolic link to that file but if the installation doesn't finish then the file to be linked to never is created.

I just removed the /etc/apache2/conf.d/aegir.conf since it points to a non existant file anyway.

---

### Post by ubudog on 2011-01-19
> **yargy said:**
> Hey I had the same issue and it I believe is caused when Aegir(for drupal) has not been fully installed.

In the Aegir installation you are supposed to create a symbolic link to that file but if the installation doesn't finish then the file to be linked to never is created.

I just removed the /etc/apache2/conf.d/aegir.conf since it points to a non existant file anyway.

So did that work?

---

### Post by JoshuaDrama on 2011-06-23
Hi, 
I am new to the forum and quite new to ubuntu/linux as well. I love it so far. I am posting here because i am receiving the same error(when trying to restart apache) as above in the first post.  
 
Syntax error on line 227 of /etc/apache2/apache2.conf: Could not open configuration file /etc/apache2/conf.d/phpmyadmin.conf: No such file or directory
Action 'configtest' failed.
The Apache error log may have more information.
   ...fail!

So any help is much appreciated!

---

### Post by ubudog on 2011-06-23
Hi, welcome to Ubuntu and the forums.

Do you have phpmyadmin installed correctly?  I believe the error there is saying it can't find phpmyadmins' configuration file.

Also, did you make any modifications to /etc/apache2/apache2.conf?

To install PhpMyAdmin:
```
sudo apt-get install phpmyadmin
```

---

### Post by regomen on 2011-08-25
What was my experience was :

I typed: ```
#ln -s /etc/phpmyadmin/apache.conf /etc/apache2/conf.d/phpmyadmin.conf
``` 
to fix phpmyadmin reload issue after installing phpmyadmin

now after this i needed to restart apache
so i typed this:
```
# /etc/init.d/apache2 restart
```

I got this error: 
```
Syntax error on line 227 of /etc/apache2/apache2.conf: Could not open configuration file /etc/apache2/conf.d/phpmyadmin.conf: No such file or directory
Action 'configtest' failed.
The Apache error log may have more information.
failed!
```

The fix is simple :
firstly,delete phpmyamdin.conf using:
```
#cd /etc/apache2/conf.d
#rm phpmyadmin.conf
```

then edit using :
```
#nano /etc/apache2/apache2.conf
```
move to line 227 as mentioned using nano command ^C
u will see command : Include conf.d
edit it to : Include /etc/phpmyadmin/apache.conf 
save and exit

after then try : 
```
#ln -s /etc/phpmyadmin/apache.conf /etc/apache2/conf.d/phpmyadmin.conf
```

and after again restart apache
```
#/etc/init.d/restart
Restarting web server: apache2.
```

Hope this may help u

---

### Post by anakberuang on 2012-07-23
thanks verry muchhhh:popcorn:

---

