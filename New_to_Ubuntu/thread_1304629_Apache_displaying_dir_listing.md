---
title: "Apache displaying dir listing"
date: 2009-10-29
forum: New to Ubuntu
---

### Post by jba6511 on 2009-10-29
I have installed apache with php5 from synaptic. Everything seems to be working as I created a few example php files and can view them by browsing to [http://localhost/app1/index.php](http://localhost/app1/index.php). However, if I just browse to [http://localhost/app1/](http://localhost/app1/) I am presented with a directory listing instead of being redirected to the index.php page. I have checked the mods-enabled dir.conf for DirectoryIndex index.html index.htm index.php. Can someone point me in the right direction for fixing this issue?

---

### Post by OffAxis on 2009-10-29
Does the same directory listing show if there's an
index.html
file in there?

---

### Post by jba6511 on 2009-10-29
Created an index.html and I get the same behavior.

---

### Post by OffAxis on 2009-10-29
Then the most likely causes are your *dir *mod not being processed correctly or a directive in your site's .conf file over-riding that.
Did you manually edit the .conf or .load files at all?

You could try disabling/re-enabling your dir mod with
```
sudo a2dismod dir
sudo /etc/init.d/apache2 restart
sudo a2enmod dir
sudo /etc/init.d/apache2 restart
```

If that doesn't do it I'd try scaling back my site's .conf to the bare minimum (Just a DirectoryRoot and ServerName)
and reloading the server.
```

sudo /etc/init.d/apache2 reload
```

---

### Post by jba6511 on 2009-10-29
Thanks, looks like that did the trick.

---

