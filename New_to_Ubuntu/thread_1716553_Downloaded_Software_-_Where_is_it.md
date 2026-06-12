---
title: "Downloaded Software - Where is it?"
date: 2011-03-28
forum: New to Ubuntu
---

### Post by paulmr1968 on 2011-03-28
Hi all,

I'm using the LTS Desktop on VMWare Workstation.  I downloaded a Virtual Appliance, uploaded it and everything seems to work.

So I head over to the Software Center.  I'm trying to create a LAMP.  My project is to create a database/website.  It seems that if I installed the Server version, I could download a LAMP all at once via taskell.  But I'm on a Desktop at the moment and figured I'd learn something anyway, so I plowed ahead.

I've downloaded Apache HTTP Server metapackage, MySQL database server/client metapackages, server-side HTML embedded scripting language (PHP5) metapackage.

So my question is: Where are they?

They aren't listed in Applications, Places or System.  And I can barely find their folders in File Browser.

---

### Post by r-senior on 2011-03-28
> **paulmr1968 said:**
> I've downloaded Apache HTTP Server metapackage, MySQL database server/client metapackages, server-side HTML embedded scripting language (PHP5) metapackage.

So my question is: Where are they?
If you used Software Centre, you didn't download the package, you installed it. There's no .exe to run, no zip file to unzip. It's installed in various parts of the filesystem. Typically a lot of the programs will be under /usr/share, config under /etc and logs in /var/log.

What happens if you open up a web browser and navigate to here?

```
http://localhost
```

Do you get a page that says Apache is running?

Generally speaking, if you are interested, you can find which files a package installs by looking at pages like this [http://packages.ubuntu.com/maverick/amd64/apache2.2-common/filelist](http://packages.ubuntu.com/maverick/amd64/apache2.2-common/filelist). But most of the time you just need to know how to configure it:

[https://help.ubuntu.com/10.10/serverguide/C/httpd.html](https://help.ubuntu.com/10.10/serverguide/C/httpd.html)

Same idea for MySQL: 

[https://help.ubuntu.com/10.10/serverguide/C/mysql.html](https://help.ubuntu.com/10.10/serverguide/C/mysql.html)

---

### Post by Crazedpsyc on 2011-03-28
Because apache is a server daemon, and has no GUI, it could not be put in a menu. 
The other things are modules for apache.
In windows, there is probaly a gui for configuring and running apache, but people assume that linux users who will be running a server actually know what they are doing in a terminal, and what the /etc/init.d folder is. 
This guide might help: [http://www.howtoforge.com/ubuntu_lamp_for_newbies](http://www.howtoforge.com/ubuntu_lamp_for_newbies)

---

### Post by paulmr1968 on 2011-03-28
It works!

This is the default web page for this server.

The web server software is running but no content has been added, yet.

---

