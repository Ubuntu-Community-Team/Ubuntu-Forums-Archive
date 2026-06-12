---
title: "blocked port 80 work around apache2"
date: 2011-01-06
forum: New to Ubuntu
---

### Post by Gluebuntu on 2011-01-06
My ISP blocks port 80. Which is unfortunate because I have a Linux box running Apache2 that I'm using for a web server. To get around this I want to use port 8000 instead.

I have a web hop domain that points to my router but with port 8000 (The router is port forwarding 8000 to my server)

e.g. mydomain.com

which redirects to

myactualdomain.com:8000

But how do I configure Apache? I have done lots of Googling but I haven't found an easy step by step guide to set up Apache to listen on port 8000 instead of port 80. :confused:

Please help, I am very new to Apache and I really want to get this web site up.

Thanks, Gluebuntu

---

### Post by JeffDavidoff on 2011-01-06
Open httpd.conf file in your text editor. Find this line: 
Listen 80 

change it to: 
Listen 8000

Save and restart Apache. 
Always restart Apache after making changes to a conf file and don't forget to make a backup before making any edits.

---

### Post by seawolf167 on 2011-01-06
Try changing

```
/etc/apache2/ports.conf
```

from

```
Listen 80
```

to 

```
Listen 8000
```

Then restart the apache server

```
/etc/inid.d/apache2 restart
```

---

### Post by Gluebuntu on 2011-01-06
@JeffDavidoff

The httpd.conf file doesn't have anything in it :(

Did you get that from the Apache website? I think I remember reading that somewhere.




@seawolf167[U]
[/U] 
O.K, I edited the ports.conf file but in that it said:

```

# If you just change the port or add more ports here, you will likely also
# have to change the VirtualHost statement in
# /etc/apache2/sites-enabled/000-default
# This is also true if you have upgraded from before 2.2.9-3 (i.e. from
# Debian etch). See /usr/share/doc/apache2.2-common/NEWS.Debian.gz and
# README.Debian.gz

```I performed the command but with init.d instead of inid.d ( I assume that was just a mistype ):

```

sudo /etc/init.d/apache2 restart

```Apache's output was:

```

 * Restarting web server apache2                                                apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
 ... waiting apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
                                                                         [ OK ]

```But when I go to my web hop address, it loads for a while and then says the website isn't responding... :(

Do I need to edit this "/etc/apache2/sites-enabled/000-default" file?

---

