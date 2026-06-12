---
title: "Apache's environment variables not updating"
date: 2015-01-26
forum: Networking &amp; Wireless
---

### Post by christian52 on 2015-01-26
I'm trying to update the PATH environment variable for Apache so that my www-data user knows where a specific binary is.

I've done a lot of reading and I've added this line to my /etc/apache2/envvars file :```
 export PATH=$PATH:/var/www/html/DITA-OT2.0/bin
```

I then perform : 
```
sudo service apache2 restart
 * Restarting web server apache2                                         [ OK ]
``` 

But here's the output of :
```
sudo -u www-data env

PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin

```

What am I doing wrong?

---

### Post by SeijiSensei on 2015-01-26
That only changes the path for the Apache server instance.  The user www-data's path remains unchanged.  To change that user's path, create a file named .profile in /var/www/html, www-data's home directory, and have it contain this line::
```

PATH="$PATH:/var/www/html/DITA-OT2.0/bin"

```
However is there a reason this file needs to reside below the /var/www/html directory?  You could just put it in /usr/local/bin where it is available to all users without any change to their profiles.

---

### Post by christian52 on 2015-01-27
Thank you. I didn't realize I needed to make a .profile file.

But I'm confident that the executable relies on files within the same folder so would it be possible to create a symbolic link between an executable in my /usr/local/bin and the DITA-OT2.0/bin?

---

### Post by SeijiSensei on 2015-01-27
Well, if the file needs to be there, then just leave it there.  But yes, in general, you can use a symbolic link.

Is this a "cgi-bin" program, one that directly handles HTTP requests?  If so, you might want to read this: [http://httpd.apache.org/docs/2.4/howto/cgi.html](http://httpd.apache.org/docs/2.4/howto/cgi.html).  Using a ScriptAlias directive might be a better choice than a symbolic link.

---

