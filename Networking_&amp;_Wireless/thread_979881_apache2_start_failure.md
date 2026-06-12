---
title: "apache2 start failure"
date: 2008-11-12
forum: Networking &amp; Wireless
---

### Post by porteclefs on 2008-11-12
hi.

I'm not really sure what's wrong here.

If I run ```
 /etc/init.d/apache2 start 
``` my server returns this >  * Starting web server apache2                                                        apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
(13)Permission denied: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs
                                                                               [fail]


What do I do??

---

### Post by porteclefs on 2008-11-12
I'm not sure why it is using 127.0.1.1 for ServerName. the localhost is 192.168.24.200 and static... Could this be the problem?

---

### Post by eighto2 on 2008-11-12
```
sudo /etc/init.d/apache2 start
```

Can you post your apache2.conf file?

---

### Post by Iowan on 2008-11-12
While you're posting...
 Post /etc/hosts - or at least look at it.  If the line for 127.0.1.1 doesn't have a reference for your hostname, add one. [This]("https://help.ubuntu.com/community/ApacheMySQLPHP#Troubleshooting%20Apache") help page mentions:> Troubleshooting Apache
If you get this error:
apache2: Could not determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
then use a text editor such as "sudo nano" at the command line or "gksudo gedit" on the desktop to create a new file...
 This doesn't seem to be the cleanest way to do it, though. You *should* be able to add it to a config file - but I can't say which one...

[This]("https://help.ubuntu.com/community/ApacheMySQLPHP#Securing%20Apache") section *might* touch on your other error.

---

### Post by porteclefs on 2008-11-13
Ok, ran ```
nano /etc/hosts
```

returns

> 
127.0.0.1       localhost
127.0.1.1       GREENLANTERN

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts


everything appears to be in order here.

moved into my apache2 directory

ran ```
nano apache2.conf
```

returns (i'll edit out all #)

> 
ServerRoot "/etc/apache2"


LockFile /var/lock/apache2/accept.lock

PidFile ${APACHE_PID_FILE}

TimeOut 300

KeepAlive on

MaxKeepAliveRequests 100

KeepAliveTimeout 15

<IfModule mpm_prefork_module>
    StartServers          5
    MinSpareServers       5
    MaxSpareServers      10
    MaxClients          150
    MaxRequestsPerChild   0
</IfModule>

<IfModule mpm_worker_module>
    StartServers          2
    MaxClients          150
    MinSpareThreads      25
    MaxSpareThreads      75
    ThreadsPerChild      25
    MaxRequestsPerChild   0
</IfModule>

User ${APACHE_RUN_USER}
Group ${APACHE_RUN_GROUP}

AccessFileName .htaccess

<Files ~ "^\.ht">
    Order allow,deny
    Deny from all
</Files>

HostNameLookups off

ErrorLog /var/log/apache2/error.log

LogLevel warn

Include /etc/apache2/mods-enabled/*.load
Include /etc/apache2/mods-enabled/*.conf

Include /etc/apache2/httpd.conf

Include /etc/apache2/ports.conf

LogFormat "%h %l %u %t \"%r\" %>s %b \"%{Referer}i\" \"%{User-Agent}i\"" combin$
LogFormat "%h %l %u %t \"%r\" %>s %b" common
LogFormat "%{Referer}i -> %U" referer
LogFormat "%{User-agent}i" agent

ServerTokens Full

ServerSignature On

Include /etc/apache2/conf.d/

Include /etc/apache2/sites-enabled/


so?

---

### Post by eighto2 on 2008-11-13
Your apache2.conf file looks fine...

Check your /etc/apache2/httpd.conf file

It should look like this
```
ServerName GREENLANTERN

```

Then just make sure your sites in the sites-enabled folder look something like this:

```
<VirtualHost *:80>
ServerName yourwebsite.com
ServerAlias www.yourwebsite.com
DocumentRoot /your/folder/path/
DirectoryIndex index.html index.htm index.php index.php4 index.php5
</VirtualHost>

```

---

### Post by Iowan on 2008-11-13
A Slicehost [article]("http://articles.slicehost.com/2008/4/25/ubuntu-hardy-installing-apache-and-php5") suggests > Open the main apache config:
sudo nano /etc/apache2/apache2.conf
At the bottom of the file add the following:
ServerName demo Of course you'd use GREENLANTERN.

---

### Post by eighto2 on 2008-11-14
> **Iowan said:**
> A Slicehost [article]("http://articles.slicehost.com/2008/4/25/ubuntu-hardy-installing-apache-and-php5") suggests  Of course you'd use GREENLANTERN.

Yeah, that setting will work in either file, but now that you mention it, its probably a better place to just keep all the settings in 1 place

---

### Post by y@w on 2008-11-14
I get that if Apache is zombied. Check that the Apache process isn't still bound to that port.

```
ps aux | grep apache
```

If it's still running, run:

```
sudo killall apache2
```

Check that Apache's not still running by using the first command. If not, then you can start Apache again:

```
sudo /etc/init.d/apache2 start
```

If it wasn't running... did you sudo your start command?


UPDATE: I'm pretty sure that's a problem with not sudo'ing...

```
user@host:~$ /etc/init.d/apache2 start
open: Permission denied
 * Starting web server apache2
(13)Permission denied: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs
open: Permission denied
   ...fail!
user@host:~$ sudo !!
sudo /etc/init.d/apache2 start
[sudo] password for user: 
 * Starting web server apache2
   ...done.

```

---

### Post by y@w on 2008-11-14
I forgot to mention.. "* Starting web server apache2 apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName" isn't fatal. It won't cause the server to not start. You'll have to fix it before using virtual servers in Apache, but it won't cause any real problems with just starting it.

---

### Post by stephenmac7 on 2010-05-25
Run:
```

su -
killall apache2
/etc/inid.d/apache2 start

```
Permissions are important!:) I had this problem too!

---

### Post by Iowan on 2010-05-25
Thanks for the input - but OP hasn't posted since December 29th, 2008.

---

