---
title: "Apache2 virtual host problem"
date: 2008-01-04
forum: Networking &amp; Wireless
---

### Post by danifodor on 2008-01-04
Hi! 

I have quite a strange problem with my apache2 server. I made 2 virtual hosts. They have the same configuration file in sites-available:
```

<VirtualHost *>
ServerName user1.something.homelinux.com
DocumentRoot /var/www/user1
<Directory /var/www/user1>
	Options Indexes FollowSymLinks MultiViews
	AllowOverride AuthConfig
	Order allow,deny
	allow from all
</Directory>
ErrorLog /var/log/apache2/error-user1.log
LogLevel warn
CustomLog /var/log/apache2/access-user1.log combined
ServerSignature On
</VirtualHost>

```
I made a symlink to sites-enabled from /var/www to the according directory. They worked fine. But today I wanted to make a third virtual host with the same method but since that time I am unable to reach any of them. I get the error message:
```

You don't have permission to access / on this server.

```
and every time I want to access to my virtual host the following entry is created in the log file:
```

Symbolic link not allowed or link target not accessible: /var/www/user1

```
I did not change the permissions. /var/www is owned by root.root and permissions are 755. But even if I set it to user1.user1 I meet the same problem. All the files contain FollowSymLinks of Options directive. Restarts run without error message. Furthermore if type ANY hostname (e.g., sadfasfgagv.something.homelinux.com) the index file of /var/www is displayed. I removed (with remove --purge swithes) apache2 and reinstalled it but it had no effect. When I first met this problem I wanted to protect one of the hosts with htpasswd but I already deleted this file (and htaccess also).

I spent the half day with trying to find a solution with google. There are many results but none of them was appropriate for me. 

Does anyone have an idea what the problem could be?

Cheers 

Daniel

---

