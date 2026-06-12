---
title: "Want apache to list files if no index.php or index.html"
date: 2009-07-05
forum: New to Ubuntu
---

### Post by ltwinner on 2009-07-05
I have enabled all permissions in all files in my /var/www (localhost) directory. When I browse to a directory inside it such as [http://localhost/testing](http://localhost/testing) the browser say 'You don't have permission to access /testing/ on this server.' But if I create a index.php file inside the testing folder, the index.php will load fine.

What I would like though, is if I browsed to [http://localhost/testing/](http://localhost/testing/) and there was no index.php, that the browser would display the directory listing instead of saying I don't have permission to access /testing/. When I was using wampserver on windows and I went to a directory without and index file, the browser always displayed the directory listing.

So how can I make this happen?

---

### Post by ltwinner on 2009-07-05
Ok, here's my error log when I tried to log into the testing directory

[Sun Jul 05 18:02:37 2009] [error] [client 127.0.0.1] Directory index forbidden by Options directive: /var/www/testing/, referer: [http://localhost/](http://localhost/)

---

### Post by credobyte on 2009-07-05
```
    <Directory /var/www/>
        Options Indexes FollowSymLinks MultiViews
        AllowOverride None
        Order allow,deny
        allow from all
    </Directory>
```

Open [COLOR=Blue]/etc/apache2/sites-available/default[/COLOR] and check if your settings match with what I've posted above.

---

### Post by ltwinner on 2009-07-05
found the problem, I had a hidden .htaccess file, that should have been in my drupal directory, in the /var/www/ directory.

---

