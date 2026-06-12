---
title: "configure Apache2"
date: 2008-06-24
forum: Networking &amp; Wireless
---

### Post by climb.colorado on 2008-06-24
Hey,

Just wanted to say I'm Linux illiterate but working on it.  I'm running Ubuntu 8.04 and having problems with Apache2.  I cannot access the config files - 

/etc/apache2/apache.conf - command not found

I apparently have installed it.  [http://localhost](http://localhost) say "It works!"

I also get the error:  Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName

Could someone steer me in the right direction?  THANKS!

---

### Post by Thirtysixway on 2008-06-24
If you're in terminal, you need to use a command.  If you want to edit the file, you will need to do something like

```
sudo gedit /etc/apache2/apache.conf
```

By default the apache config files need to be edited by root/privileged user so use sudo

---

### Post by climb.colorado on 2008-06-24
I have tried that but the page comes up blank - no info on it.  Any suggestions?

---

### Post by superprash2003 on 2008-06-25
i dont think there is a apache.conf file.. but there sure is a httpd.conf file sudo gedit /etc/apache2/httpd.conf

---

### Post by webweaver on 2008-06-26
Hi there,

If you're still having troubles, I'd suggest the following:
```
sudo nano /etc/apache2/apache2.conf
``` *(The httpd.conf file is in there too, but is not used on Ubuntu installations, in favour of using the apache2.conf instead.)*

Look for the line that says:
```
ServerRoot "/etc/apache2"
```

And add a line so it looks like this:
```
ServerRoot "/etc/apache2"
ServerName "localhost"
```

Then run:
```
sudo /etc/init.d/apache2 reload
``` *('reload' should work, it just reloads the config without restarting the Apache server. You can try replacing 'reload' with 'restart' if it doesn't work.)*

You shouldn't get that error message anymore, you should be able to browse to [http://localhost](http://localhost) and see "It works!", and you should be able to build your website in /var/www/ and see it  :)

Hope that was helpful!

---

