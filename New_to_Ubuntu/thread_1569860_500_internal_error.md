---
title: "500 internal error"
date: 2010-09-07
forum: New to Ubuntu
---

### Post by duceduc on 2010-09-07
I followed a guide on how to setup [multiple ssl vhost]("http://blog.revolunet.com/index.php/reseau/administration/hosting-multiple-ssl-vhosts-on-a-single-ipportcertificate-with-apache2#comment-258199"). But after enabling the second site, I get a 500 internal error with this error.
> Request exceeded the limit of 10 internal redirects due to probable configuration error. Use 'LimitInternalRecursion' to increase the limit if necessary. Use 'LogLevel debug' to get a backtrace.

The error may have been cause by this script. The RewriteRule may need to be tweaked; however, I do not know how.
```
### Mass SSL Vhosts ###
RewriteEngine on

#   define two maps: one for fixing the URL and one which defines
#   the available virtual hosts with their corresponding
#   DocumentRoot.
RewriteMap    lowercase    int:tolower
RewriteMap    vhost        txt:/etc/apache2/ssl.map

#   1. make sure we don't map for common locations
RewriteCond   %{REQUEST_URI}  !^/cgi-bin/.*
RewriteCond   %{REQUEST_URI}  !^/icons/.*

#   2. make sure we have a Host header
RewriteCond   %{HTTP_HOST}  !^$

#   3. lowercase the hostname
RewriteCond   ${lowercase:%{HTTP_HOST}|NONE}  ^(.+)$
#
#   4. lookup this hostname in vhost.map and
#      remember it only when it is a path
#      (and not "NONE" from above)
RewriteCond   ${vhost:%1}  ^(/.*)$

#   5. finally we can map the URL to its docroot location
#      and remember the virtual host for logging puposes
RewriteRule   ^/(.*)$   %1/$1  [E=VHOST:${lowercase:%{HTTP_HOST}}]

```

---

### Post by duceduc on 2010-09-08
After searching for some time, I've fix my issue. For one of my rewrites in .htaccess, I need to add this RewriteBase

```
RewriteBase /
```

---

