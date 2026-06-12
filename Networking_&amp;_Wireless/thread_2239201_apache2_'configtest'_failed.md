---
title: "apache2 'configtest' failed"
date: 2014-08-12
forum: Networking &amp; Wireless
---

### Post by rebeltaz on 2014-08-12
After a lightning strike, I have been trying to get my sever back online for two months! @chili555 helped with a portion of the problem here - [http://ubuntuforums.org/showthread.php?t=2229685](http://ubuntuforums.org/showthread.php?t=2229685)

At his suggestion, I started a new thread here - [http://ubuntuforums.org/showthread.php?t=2236550](http://ubuntuforums.org/showthread.php?t=2236550) - to which I have received no replies after two weeks.

In the meantime, I have attempted to figure this out on my own and I may have gotten SOMEwhere, but I still need help!

I did a release update to 14.04LTS and I noticed that the message stated that apache2 could not be restarted do to configuration errors. So I ran apachectl configtest and received this:

```

apache2: Syntax error on line 140 of /etc/apache2/apache2.conf: Syntax error on line 1 of /etc/apache2/mods-enabled/ruby.load: Cannot load /usr/lib/apache2/modules/mod_ruby.so into server: /usr/lib/apache2/modules/mod_ruby.so: cannot open shared object file: No such file or directory
Action 'configtest' failed.
The Apache error log may have more information.

```

Line 140 of apache2.conf is:
IncludeOptional mods-enabled/*.load

Line 1 of ruby.load is:
LoadModule ruby_module /usr/lib/apache2/modules/mod_ruby.so

The Apache error log is as follows:

```

[Sun Aug 10 06:29:33 2014] [error] python_init: Python version mismatch, expected '2.7.2+', found '2.7.3'.
[Sun Aug 10 06:29:33 2014] [error] python_init: Python executable found '/usr/bin/python'.
[Sun Aug 10 06:29:33 2014] [error] python_init: Python path being used '/usr/lib/python2.7/:/usr/lib/python2.7/plat-linux2:/usr/lib/python2.7/lib-tk:/usr/lib/python2.7/lib-old:/usr/lib/python2.7/lib-dynload'.
[Sun Aug 10 06:29:33 2014] [notice] mod_python: Creating 8 session mutexes based on 150 max processes and 0 max threads.
[Sun Aug 10 06:29:33 2014] [notice] mod_python: using mutex_directory /tmp 
[Sun Aug 10 06:29:35 2014] [warn] RSA server certificate is a CA certificate (BasicConstraints: CA == TRUE !?)
[Sun Aug 10 06:29:35 2014] [notice] Apache/2.2.22 (Ubuntu) mod_fcgid/2.3.6 PHP/5.3.10-1ubuntu3.13 with Suhosin-Patch mod_python/3.3.1 Python/2.7.3 mod_ruby/1.2.6 Ruby/1.8.7(2011-06-30) mod_ssl/2.2.22 OpenSSL/1.0.1 mod_perl/2.0.5 Perl/v5.14.2 configured -- resuming normal operations
[Sun Aug 10 06:29:35 2014] [warn] long lost child came home! (pid 1559)
[Sun Aug 10 14:30:30 2014] [error] [client 192.168.1.216] File does not exist: /var/www/swupdate
[Mon Aug 11 17:28:06 2014] [warn] child process 23566 still did not exit, sending a SIGTERM
[Mon Aug 11 17:28:06 2014] [warn] child process 23567 still did not exit, sending a SIGTERM
[Mon Aug 11 17:28:06 2014] [warn] child process 23568 still did not exit, sending a SIGTERM
[Mon Aug 11 17:28:06 2014] [warn] child process 23569 still did not exit, sending a SIGTERM
[Mon Aug 11 17:28:06 2014] [warn] child process 23570 still did not exit, sending a SIGTERM
[Mon Aug 11 17:28:06 2014] [warn] child process 30874 still did not exit, sending a SIGTERM
[Mon Aug 11 17:28:08 2014] [notice] caught SIGTERM, shutting down
[Mon Aug 11 17:28:10 2014] [warn] RSA server certificate is a CA certificate (BasicConstraints: CA == TRUE !?)
[Mon Aug 11 17:28:10 2014] [notice] suEXEC mechanism enabled (wrapper: /usr/lib/apache2/suexec)
[Mon Aug 11 17:28:12 2014] [error] python_init: Python version mismatch, expected '2.7.2+', found '2.7.3'.
[Mon Aug 11 17:28:12 2014] [error] python_init: Python executable found '/usr/bin/python'.
[Mon Aug 11 17:28:12 2014] [error] python_init: Python path being used '/usr/lib/python2.7/:/usr/lib/python2.7/plat-linux2:/usr/lib/python2.7/lib-tk:/usr/lib/python2.7/lib-old:/usr/lib/python2.7/lib-dynload'.
[Mon Aug 11 17:28:12 2014] [notice] mod_python: Creating 8 session mutexes based on 150 max processes and 0 max threads.
[Mon Aug 11 17:28:12 2014] [notice] mod_python: using mutex_directory /tmp 
[Mon Aug 11 17:28:13 2014] [warn] RSA server certificate is a CA certificate (BasicConstraints: CA == TRUE !?)
[Mon Aug 11 17:28:13 2014] [notice] Apache/2.2.22 (Ubuntu) mod_fcgid/2.3.6 PHP/5.3.10-1ubuntu3.13 with Suhosin-Patch mod_python/3.3.1 Python/2.7.3 mod_ruby/1.2.6 Ruby/1.8.7(2011-06-30) mod_ssl/2.2.22 OpenSSL/1.0.1 mod_perl/2.0.5 Perl/v5.14.2 configured -- resuming normal operations
[Mon Aug 11 17:34:56 2014] [notice] caught SIGTERM, shutting down

```

I don't need ruby, so I commented out Line 1 of ruby.load and attempted to restart apache2. This was the error it threw up:

```

 * Restarting web server apache2                                                AH00548: NameVirtualHost has no effect and will be removed in the next release /etc/apache2/ports.conf:8
(13)Permission denied: AH00072: make_sock: could not bind to address [::]:80
(13)Permission denied: AH00072: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
AH00015: Unable to open logs
Action 'start' failed.
The Apache error log may have more information.
                                                                         [fail]
 * The apache2 instance did not start within 20 seconds. Please read the log files to discover problems

```


I REALLY need to get this server back up. ANY help would be AWESOME! Please and thank you!

---

### Post by JetStorm on 2014-08-12
According to the error something else is using port 80.
Try opening the server ip or domain (if available) in a browser and see what happens

---

### Post by rebeltaz on 2014-08-12
> **JetStorm said:**
> According to the error something else is using port 80.
Try opening the server ip or domain (if available) in a browser and see what happens

Using either robotsandcomputers.com or 68.16.218.4, I get the same "Firefox can't establish a connection to the server at..." error page

Before I did the upgrade to 14.04, I could at least access the server from my local network (I think because the hosts file on my computer specifically pointed to the server), but now I can't even do that.

---

### Post by JetStorm on 2014-08-12
Try 

**netstat -lnptu** 

&#8203;and see if port 80 is open and what is listening on it

---

### Post by rebeltaz on 2014-08-12
> **JetStorm said:**
> Try 

**netstat -lnptu** 

&#8203;and see if port 80 is open and what is listening on it

I assumed that you meant run this command from the server?

```

Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:465             0.0.0.0:*               LISTEN      1582/master     
tcp        0      0 0.0.0.0:21              0.0.0.0:*               LISTEN      1606/pure-ftpd (SER
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      890/sshd        
tcp        0      0 0.0.0.0:25              0.0.0.0:*               LISTEN      1582/master     
tcp        0      0 0.0.0.0:993             0.0.0.0:*               LISTEN      910/dovecot     
tcp        0      0 0.0.0.0:995             0.0.0.0:*               LISTEN      910/dovecot     
tcp        0      0 127.0.0.1:10024         0.0.0.0:*               LISTEN      1468/amavisd-new (m
tcp        0      0 127.0.0.1:10025         0.0.0.0:*               LISTEN      1582/master     
tcp        0      0 0.0.0.0:3306            0.0.0.0:*               LISTEN      1013/mysqld     
tcp        0      0 0.0.0.0:587             0.0.0.0:*               LISTEN      1582/master     
tcp        0      0 0.0.0.0:110             0.0.0.0:*               LISTEN      910/dovecot     
tcp        0      0 127.0.0.1:783           0.0.0.0:*               LISTEN      1474/spamd.pid  
tcp        0      0 0.0.0.0:143             0.0.0.0:*               LISTEN      910/dovecot     
tcp6       0      0 :::465                  :::*                    LISTEN      1582/master     
tcp6       0      0 :::21                   :::*                    LISTEN      1606/pure-ftpd (SER
tcp6       0      0 :::22                   :::*                    LISTEN      890/sshd        
tcp6       0      0 :::25                   :::*                    LISTEN      1582/master     
tcp6       0      0 :::993                  :::*                    LISTEN      910/dovecot     
tcp6       0      0 :::995                  :::*                    LISTEN      910/dovecot     
tcp6       0      0 :::587                  :::*                    LISTEN      1582/master     
tcp6       0      0 :::110                  :::*                    LISTEN      910/dovecot     
tcp6       0      0 ::1:783                 :::*                    LISTEN      1474/spamd.pid  
tcp6       0      0 :::143                  :::*                    LISTEN      910/dovecot     
udp        0      0 192.168.1.13:123        0.0.0.0:*                           1185/ntpd       
udp        0      0 127.0.0.1:123           0.0.0.0:*                           1185/ntpd       
udp        0      0 0.0.0.0:123             0.0.0.0:*                           1185/ntpd       
udp6       0      0 fe80::210:b5ff:fe10:123 :::*                                1185/ntpd       
udp6       0      0 ::1:123                 :::*                                1185/ntpd       
udp6       0      0 :::123                  :::*                                1185/ntpd       

```

I don't see port 80 on the list...

---

### Post by JetStorm on 2014-08-12
I'm running out of ideas. Check the error logs and see if there's anything new, because the one you've posted is from before removing the ruby module.
Also are you starting the server as superuser (adding sudo in front of "service apache2 restart" if logged in as normal user, or starting it directly while logged in as root)?

btw, not much on topic but it might be useful to you in the future - adding and removing apache modules in Ubuntu/Debian is done via the commands a2dismod modname (this one disables the chosen module) and a2enmod modname (does the opposite).

---

### Post by rebeltaz on 2014-08-12
Frick! I don't know why, but I forgot to add sudo to the restart command. OK... so it started, but I still cannot access the web server. I can access ssh and ftp, though? Any other ideas?

---

### Post by JetStorm on 2014-08-12
Yes - check the error log for any new messages and run again the netstat command from above to make sure that apache is running on port 80.
Also you can try to temporary disable the server firewall if there's any.

---

### Post by rebeltaz on 2014-08-12
The error.log shows a LOT of this:

```

[Tue Aug 12 22:25:01.900886 2014] [access_compat:error] [pid 1918] [client 127.0.0.1:43046] AH01797: client denied by server configuration: /var/www/html/
[Tue Aug 12 22:30:02.210096 2014] [access_compat:error] [pid 1693] [client 127.0.0.1:43049] AH01797: client denied by server configuration: /var/www/html/
[Tue Aug 12 22:35:02.502489 2014] [access_compat:error] [pid 1694] [client 127.0.0.1:43052] AH01797: client denied by server configuration: /var/www/html/
[Tue Aug 12 22:40:02.589130 2014] [access_compat:error] [pid 1695] [client 127.0.0.1:43064] AH01797: client denied by server configuration: /var/www/html/
[Tue Aug 12 22:45:02.066103 2014] [access_compat:error] [pid 1696] [client 127.0.0.1:43067] AH01797: client denied by server configuration: /var/www/html/
[Tue Aug 12 22:48:11.898175 2014] [access_compat:error] [pid 1692] [client 192.168.1.5:34206] AH01797: client denied by server configuration: /var/www/html/robots
[Tue Aug 12 22:48:14.180162 2014] [access_compat:error] [pid 1692] [client 192.168.1.5:34206] AH01797: client denied by server configuration: /var/www/html/favicon.ico

```


netstat output:
```

Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:465             0.0.0.0:*               LISTEN      1553/master     
tcp        0      0 0.0.0.0:21              0.0.0.0:*               LISTEN      1577/pure-ftpd (SER
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      793/sshd        
tcp        0      0 0.0.0.0:25              0.0.0.0:*               LISTEN      1553/master     
tcp        0      0 0.0.0.0:993             0.0.0.0:*               LISTEN      806/dovecot     
tcp        0      0 0.0.0.0:995             0.0.0.0:*               LISTEN      806/dovecot     
tcp        0      0 127.0.0.1:10024         0.0.0.0:*               LISTEN      1438/amavisd-new (m
tcp        0      0 127.0.0.1:10025         0.0.0.0:*               LISTEN      1553/master     
tcp        0      0 0.0.0.0:3306            0.0.0.0:*               LISTEN      945/mysqld      
tcp        0      0 0.0.0.0:587             0.0.0.0:*               LISTEN      1553/master     
tcp        0      0 0.0.0.0:110             0.0.0.0:*               LISTEN      806/dovecot     
tcp        0      0 127.0.0.1:783           0.0.0.0:*               LISTEN      1445/spamd.pid  
tcp        0      0 0.0.0.0:143             0.0.0.0:*               LISTEN      806/dovecot     
tcp6       0      0 :::465                  :::*                    LISTEN      1553/master     
tcp6       0      0 :::21                   :::*                    LISTEN      1577/pure-ftpd (SER
tcp6       0      0 :::22                   :::*                    LISTEN      793/sshd        
tcp6       0      0 :::25                   :::*                    LISTEN      1553/master     
tcp6       0      0 :::443                  :::*                    LISTEN      1678/apache2    
tcp6       0      0 :::993                  :::*                    LISTEN      806/dovecot     
tcp6       0      0 :::995                  :::*                    LISTEN      806/dovecot     
tcp6       0      0 :::587                  :::*                    LISTEN      1553/master     
tcp6       0      0 :::110                  :::*                    LISTEN      806/dovecot     
tcp6       0      0 ::1:783                 :::*                    LISTEN      1445/spamd.pid  
tcp6       0      0 :::143                  :::*                    LISTEN      806/dovecot     
tcp6       0      0 :::80                   :::*                    LISTEN      1678/apache2    
udp        0      0 192.168.1.13:123        0.0.0.0:*                           1165/ntpd       
udp        0      0 127.0.0.1:123           0.0.0.0:*                           1165/ntpd       
udp        0      0 0.0.0.0:123             0.0.0.0:*                           1165/ntpd       
udp6       0      0 fe80::210:b5ff:fe10:123 :::*                                1165/ntpd       
udp6       0      0 ::1:123                 :::*                                1165/ntpd       
udp6       0      0 :::123                  :::*                                1165/ntpd       

```

apache does seem to be on port 80...

I ran sudo ufw status earlier, I was going to disable it then, but I got this:

```

WARN: Duplicate profile 'Apache', using last found
WARN: Duplicate profile 'Apache Secure', using last found
WARN: Duplicate profile 'Apache Full', using last found
Status: inactive

```

I've never seen those warnings before?

---

### Post by JetStorm on 2014-08-13
Is it supposed to run only on IPv6? 
Because if not - there might be something wrong in your config files.

---

### Post by rebeltaz on 2014-08-13
> **JetStorm said:**
> Is it supposed to run only on IPv6? 
Because if not - there might be something wrong in your config files.

No... if anything, I would only want IPv4 if it had to be one or the other.....

---

### Post by rebeltaz on 2014-08-13
When you said that, since I can't log into the site, I can't log into ISPConfig either.... this should be fun.

---

### Post by JetStorm on 2014-08-13
Paste the contents of /etc/apache2/ports.conf and /etc/apache2/sites-enabled/000-default.conf (but check for any sensitive data like the public server IP and remove it before posting)

---

### Post by rebeltaz on 2014-08-13
/etc/apache2/ports.conf

```

# If you just change the port or add more ports here, you will likely also
# have to change the VirtualHost statement in
# /etc/apache2/sites-enabled/000-default
# This is also true if you have upgraded from before 2.2.9-3 (i.e. from
# Debian etch). See /usr/share/doc/apache2.2-common/NEWS.Debian.gz and
# README.Debian.gz

NameVirtualHost *:80
Listen 80

<IfModule mod_ssl.c>
    # If you add NameVirtualHost *:443 here, you will also have to change
    # the VirtualHost statement in /etc/apache2/sites-available/default-ssl
    # to <VirtualHost *:443>
    # Server Name Indication for SSL named virtual hosts is currently not
    # supported by MSIE on Windows XP.
Listen 443
</IfModule>

<IfModule mod_gnutls.c>
Listen 443
</IfModule>

```

/etc/apache2/sites-enabled/000-default.conf

```

<VirtualHost *:80>
	# The ServerName directive sets the request scheme, hostname and port that
	# the server uses to identify itself. This is used when creating
	# redirection URLs. In the context of virtual hosts, the ServerName
	# specifies what hostname must appear in the request's Host: header to
	# match this virtual host. For the default virtual host (this file) this
	# value is not decisive as it is used as a last resort host regardless.
	# However, you must set it for any further virtual host explicitly.
	#ServerName www.example.com

	ServerAdmin webmaster@localhost
	DocumentRoot /var/www/html

	# Available loglevels: trace8, ..., trace1, debug, info, notice, warn,
	# error, crit, alert, emerg.
	# It is also possible to configure the loglevel for particular
	# modules, e.g.
	#LogLevel info ssl:warn

	ErrorLog ${APACHE_LOG_DIR}/error.log
	CustomLog ${APACHE_LOG_DIR}/access.log combined

	# For most configuration files from conf-available/, which are
	# enabled or disabled at a global level, it is possible to
	# include a line for only one particular virtual host. For example the
	# following line enables the CGI configuration for this host only
	# after it has been globally disabled with "a2disconf".
	#Include conf-available/serve-cgi-bin.conf
</VirtualHost>

# vim: syntax=apache ts=4 sw=4 sts=4 sr noet

```

I don't know if it makes a difference, but since these look kind of empty, the sites were configured originally with ISPConfig.

---

### Post by JetStorm on 2014-08-13
Nothing out of the ordinary here...
Just looked at the error log entries you posted earlier - something is blocking you from opening the site... check for a .htaccess file in /var/www/html or look in the main config file or inside the .conf files in the /etc/apache2/mods-enabled directory.
You're looking for an order directive like 
" Order Deny,Allow
[FONT=monospace]Deny from all"[/FONT]

---

### Post by rebeltaz on 2014-08-13
OK.. I found that text in the /etc/apache2/mods-enabled/php5.conf file:

```

<FilesMatch ".+\.ph(p[345]?|t|tml)$">
    SetHandler application/x-httpd-php
</FilesMatch>
<FilesMatch ".+\.phps$">
    SetHandler application/x-httpd-php-source
    # Deny access to raw php sources by default
    # To re-enable it's recommended to enable access to the files
    # only in specific virtual host or directory
    Order Deny,Allow
    Deny from all
</FilesMatch>
# Deny access to files without filename (e.g. '.php')
<FilesMatch "^\.ph(p[345]?|t|tml|ps)$">
    Order Deny,Allow
    Deny from all
</FilesMatch>

# Running PHP scripts in user directories is disabled by default
# 
# To re-enable PHP in user directories comment the following lines
# (from <IfModule ...> to </IfModule>.) Do NOT set it to On as it
# prevents .htaccess files from disabling it.
<IfModule mod_userdir.c>
    <Directory /home/*/public_html>
        php_admin_flag engine Off
    </Directory>
</IfModule>

```

---

### Post by rebeltaz on 2014-08-13
not sure why that posted twice....

---

### Post by JetStorm on 2014-08-13
Take a look at this link and see if it will help
[http://stackoverflow.com/questions/12140559/error-with-htaccess-and-mod-rewrite](http://stackoverflow.com/questions/12140559/error-with-htaccess-and-mod-rewrite)

It seems this mod access_compat is new in apache 2.4 and your configuration is probably for apache 2.2.

---

### Post by rebeltaz on 2014-08-13
Just curious... would this affect a site that has NO php component? Because one of my other sites - [www.ShelbyCycle.com](www.ShelbyCycle.com) - has no php component, yet is unaccesable as well..

---

### Post by rebeltaz on 2014-08-13
I also found that tet here - /etc/apache2/sites-enabled/000-ispconfig.conf - which may be more meaningful:


```

################################################
# ISPConfig Logfile configuration for vlogger
################################################

LogFormat "%v %h %l %u %t \"%r\" %>s %B \"%{Referer}i\" \"%{User-Agent}i\"" combined_ispconfig
CustomLog "| /usr/local/ispconfig/server/scripts/vlogger -s access.log -t \"%Y%m%d-access.log\" /var/log/ispconfig/httpd" combined_ispconfig

<Directory /var/www/clients>
    AllowOverride None
    Order Deny,Allow
    Deny from all
</Directory>

# Do not allow access to the root file system of the server for security reasons
<Directory />
    AllowOverride None
    Order Deny,Allow
    Deny from all
</Directory>

<Directory /var/www/conf>
    AllowOverride None
    Order Deny,Allow
    Deny from all
</Directory>

# Except of the following directories that contain website scripts
<Directory /usr/share/phpmyadmin>
        Order allow,deny
        Allow from all
</Directory>

<Directory /usr/share/phpMyAdmin>
        Order allow,deny
        Allow from all
</Directory>

<Directory /usr/share/squirrelmail>
        Order allow,deny
        Allow from all
</Directory>

# Allow access to mailman on OpenSuSE
<Directory /usr/lib/mailman/cgi-bin>
        AllowOverride All
		order allow,deny
        allow from all
</Directory>

<Directory /usr/lib/mailman/icons>
        order allow,deny
        allow from all
</Directory>

<Directory /var/lib/mailman/archives/>
        Options +FollowSymLinks
        order allow,deny
        allow from all
</Directory>

# allow path to awstats and alias for awstats icons
<Directory /usr/share/awstats>
        Order allow,deny
        Allow from all
</Directory>

Alias /awstats-icon "/usr/share/awstats/icon"

NameVirtualHost *:80
NameVirtualHost *:443


```

---

### Post by JetStorm on 2014-08-13
Let's try to start it clean and see if this is the actual problem.
Do the following:
[B]sudo a2dismod php5
sudo a2dissite 000-ispconfig.conf[/B]
Also see what other files you have in /etc/apache2/sites-enabled and disable them with **a2dissite **until the only one left there is 000-default.conf (You can re-enable them later with a2enmod and a2ensite)

**sudo apache2 restart**


Also paste the output from **curl -s -D - [http://127.0.0.1](http://127.0.0.1) -o /dev/null **(run from the server before making the above changes and after making them)

---

### Post by rebeltaz on 2014-08-13
a2dismod worked fine, but when I tried the a2dissite comman, I got:

ERROR: Site 000-ispconfig does not exist!


This is the ls of sites-enabled:

```

derek@shelbyserver:/etc/apache2/sites-enabled$ ls
000-apps.vhost       100-robotsandcomputers.com.vhost
000-default.conf     100-shelbycycle.com.vhost
000-ispconfig.conf   100-shelbytvservice.com.vhost
000-ispconfig.vhost

```

---

### Post by SeijiSensei on 2014-08-13
In 14.04, all the virtual host definition files must have the .conf extension.  That's because they are loaded by this directive in /etc/apache2/apache2.conf:
```

# Include the virtual host configurations:
IncludeOptional sites-enabled/*.conf

```

---

### Post by rebeltaz on 2014-08-13
> **SeijiSensei said:**
> In 14.04, all the virtual host definition files must have the .conf extension.  That's because they are loaded by this directive in /etc/apache2/apache2.conf:
```

# Include the virtual host configurations:
IncludeOptional sites-enabled/*.conf

```

So I need to rename .vhost with .conf?

---

### Post by SeijiSensei on 2014-08-13
Yes.

---

### Post by rebeltaz on 2014-08-13
OK.. I renamed the vhost files conf and I can access the site again on my local network (host file points to it directly) but I still cannot access it from the web.

---

### Post by rebeltaz on 2014-08-13
I don't belive this... just for the heck off it, I took a look at my modem and EVERY port forwarding entry I had added was missing! 

I re-added the port forwarding for the server again and it seems to be working again. Can you double check for me to make sure that you can access it? It's the site in my signature. 

I appreciate ALL of your help - everyone! There were issues other than this and you did help me resolve all of them!

---

### Post by rebeltaz on 2014-08-14
Crap... is there anything that changed in 14.04 to php? I cannot access php pages now. I ran a2enmod php5 but still no.

---

### Post by JetStorm on 2014-08-14
Did you restarted the server after that and if yes - what happens when you open a link containing a php page?
Plus I still can't open the site from your signature.

---

### Post by rebeltaz on 2014-08-14
Yeah, I did restart the server and I even rebooted the computer. That's odd because I can access it through tor, and I couldn't before....

I get an error 500 message:

```


ERROR 500 - Internal Server Error!
The following error occurred:

The requested URL caused an internal server error.

If you get this message repeatedly please contact the webmaster.

```

---

### Post by JetStorm on 2014-08-14
You can see exactly what's wrong in the apache error log.

---

### Post by rebeltaz on 2014-08-14
This is what it says:

```

[Wed Aug 13 23:55:02.278669 2014] [access_compat:error] [pid 2243] [client 127.0.0.1:50250] AH01797: client denied by server configuration: /var/www/html/
PHP Fatal error:  Directive 'register_long_arrays' is no longer available in PHP in Unknown on line 0

```

Can you see the site at all now?

---

### Post by JetStorm on 2014-08-14
Yes, the site is working now.
As for the PHP error - go to your php.ini (/etc/php5/apache2/php.ini) and comment the line [FONT=Ubuntu Mono]register_long_arrays = Off[/FONT] (or On, depending on your config)

---

### Post by rebeltaz on 2014-08-14
> **JetStorm said:**
> Yes, the site is working now.
As for the PHP error - go to your php.ini (/etc/php5/apache2/php.ini) and comment the line [FONT=Ubuntu Mono]register_long_arrays = Off[/FONT] (or On, depending on your config)

That line doesn't appear to be in my php.ini file. I even did a case-insesitive grep on "array" and nothing like that.

---

### Post by JetStorm on 2014-08-14
What about inside an htaccess file or some of the enabled sites config?
It surely has to exist somewhere if it's inside the error log, so your options are to look inside /etc/apache2 , /etc/php5 and /var/www/html
Also it could be used inside a .php file with the ini_set function.

---

### Post by rebeltaz on 2014-08-14
I did however find that in /etc/php/cgi/php.ini and commented that out.

Could you check and see if this link is working from the outside:
[http://www.robotsandcomputers.com/Pez/](http://www.robotsandcomputers.com/Pez/)

Thank you!

---

### Post by JetStorm on 2014-08-14
It works, although the pictures load painfully slow, which i suppose is normal since it's not hosted in a data center

---

### Post by rebeltaz on 2014-08-14
When you say "painfully slow" how long does it take the page to load completely?

---

### Post by JetStorm on 2014-08-14
On a browser with no cache - 1 minute and 50 seconds.

---

### Post by rebeltaz on 2014-08-14
Wow! That IS slow! ... I don't guess there is anything I can do about that , though :(

I really do appreciate all of your help

---

### Post by JetStorm on 2014-08-14
Actually you can do something about it by moving all your images (and maybe javascripts and css files) to a CDN (there are free solutions available) and leaving only the PHP scripts and HTML files on your server.
Of course that would require some extra work on your side, since you have to change the source code to reflect the new path to every moved file.

---

### Post by rebeltaz on 2014-08-14
Oh, I don't mind the work... I'm actually looking into moving my sites to 1and1 (the company that I get the domain name from in the first place) ... Not only is the site slow, as you can see, but it slows the rest of the network down, too... I think they have cheap (under $10 a month) plans, so...

---

### Post by JetStorm on 2014-08-14
If all your sites are static HTML or PHP, you can try a free solution first... For example something like [http://www.000webhost.com/features](http://www.000webhost.com/features) 
Of course you can't expect the best possible speeds or 100% uptime in that case but paid hosting isn't always perfect as well.

---

### Post by rebeltaz on 2014-08-14
Well, I have three sites with almost 10 gigs of data combined, so that one won't work...  but I will look around before I commit to anything :)

---

### Post by SeijiSensei on 2014-08-14
> **rebeltaz said:**
> I think they have cheap (under $10 a month) plans, so...

For $10/month you can get an entire virtual server from [Linode]("http://www.linode.com/").  I have three.

---

