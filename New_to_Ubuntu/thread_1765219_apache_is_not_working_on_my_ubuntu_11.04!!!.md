---
title: "apache is not working on my ubuntu 11.04!!!"
date: 2011-05-22
forum: New to Ubuntu
---

### Post by AEllerbrock on 2011-05-22
Hi, i've installed about 10 times apache 2 from the console, and each time i try to access localhost, the browser says that the adress doesn't exist. After that i tried to install lamp, and everything was fine, mysql and php were fine, but the localhost proble is still insolved.

Please help me with this issue, i cannot try my php programs (i'm a begginer with that also) :D

---

### Post by antmenj on 2011-05-22
What happens if you enter your own IP address in your browser?

You can find out your IP address by RIGHT clicking the network connection icon at the top of the screen and selecting connection information.

---

### Post by AEllerbrock on 2011-05-22
The same thing....it tells me to check the conection

---

### Post by antmenj on 2011-05-23
I'm not sure if some of the commands in this thread my help:

[http://ubuntuforums.org/showthread.php?t=1762290](http://ubuntuforums.org/showthread.php?t=1762290)

What is the result of the status one for example?

---

### Post by AEllerbrock on 2011-05-24
i typed sudo /etc/init.d/apache2 start and this came out in the console

apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName

when i typed 127.0.1.1 on my browser it showed me the "it works!" message, but my php files are still unavailable on the browser

---

### Post by alphacrucis2 on 2011-05-24
> **AEllerbrock said:**
> i typed sudo /etc/init.d/apache2 start and this came out in the console

apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName

when i typed 127.0.1.1 on my browser it showed me the "it works!" message, but my php files are still unavailable on the browser

Where did you put the files. Also you need to configure apache.

---

### Post by webofunni on 2011-05-24
Try

```

sudo apt-get install apache2
sudo apt-get install php5
sudo /etc/init.d/apache2 restart
sudo vi /var/www/index.php

```


Then press "i" to insert data. Put this in that file. 

```

<?php
phpinfo()
?>

```

You said the page works with IP 127.0.1.1, correct ? 

Then type 127.0.1.1/index.php in browser, That should work.

---

### Post by acetace on 2011-06-08
I am actually experiencing the same thing although I have more information here.

I did do the phpinfo() but when accessing the page the page shows up blank. Looking at the source of the page I see the whole <?php phpinfo() ?> un-parsed.

I did install via 

```
sudo apt-get install lamp-server^
```

I suspect it has something to do with php files not getting parsed in Apache but I am not sure where else to check. Please advise.

---

### Post by webofunni on 2011-06-09
I am not sure, how exactly that package configures apache and php. If that is same as default apache/php in ubuntu then do it

```

grep -ir "mods" /etc/apache2/*
ls -l /etc/apache2/mods-enabled/

```

---

### Post by mrhhug on 2011-06-10
localhost worked for me on opera and firefox, but Google Chrome made me type in 127.0.1.1 OR 127.0.0.1 however your setup. just a little insight for everyone

---

### Post by webofunni on 2011-06-10
> **mrhhug said:**
> localhost worked for me on opera and firefox, but Google Chrome made me type in 127.0.1.1 OR 127.0.0.1 however your setup. just a little insight for everyone

Thats weird. If you are able to ping localhost then that should come up in all browsers. Try it after clearing the browser cache.

---

