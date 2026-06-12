---
title: "change apache error pages"
date: 2007-06-14
forum: Networking &amp; Wireless
---

### Post by jcolo on 2007-06-14
Hi,

I wanto to prevent showing apacher version, php version ports info etc in the error pages. (404 not found etc).

I have made changes in /usr/share/apache/error  .. and in include...

no luck.

I changed /etc/apache2.cof ( delete commented all related lines )
##<IfModule mod_negotiation.c>
#<IfModule mod_include.c>
#    Alias /error/ "/usr/share/apache2/error/"
#
#    <Directory "/usr/share/apache2/error">
#        AllowOverride None
#        Options IncludesNoExec
#        AddOutputFilter Includes html
#        AddHandler type-map var
#        Order allow,deny
#        Allow from all
#        LanguagePriority en es de fr
#        ForceLanguagePriority Prefer Fallback
#    </Directory>
#
#    ErrorDocument 400 /error/HTTP_BAD_REQUEST.html.var
#    ErrorDocument 401 /error/HTTP_UNAUTHORIZED.html.var
#    ErrorDocument 403 /error/HTTP_FORBIDDEN.html.var
#    ErrorDocument 404 /error/HTTP_NOT_FOUND.html.var
#    ErrorDocument 405 /error/HTTP_METHOD_NOT_ALLOWED.html.var
#    ErrorDocument 408 /error/HTTP_REQUEST_TIME_OUT.html.var
#    ErrorDocument 410 /error/HTTP_GONE.html.var
#    ErrorDocument 411 /error/HTTP_LENGTH_REQUIRED.html.var
#    ErrorDocument 412 /error/HTTP_PRECONDITION_FAILED.html.var
#    ErrorDocument 413 /error/HTTP_REQUEST_ENTITY_TOO_LARGE.html.var
#    ErrorDocument 414 /error/HTTP_REQUEST_URI_TOO_LARGE.html.var
#    ErrorDocument 415 /error/HTTP_SERVICE_UNAVAILABLE.html.var
#    ErrorDocument 500 /error/HTTP_INTERNAL_SERVER_ERROR.html.var
#    ErrorDocument 501 /error/HTTP_NOT_IMPLEMENTED.html.var
#    ErrorDocument 502 /error/HTTP_BAD_GATEWAY.html.var
#    ErrorDocument 503 /error/HTTP_SERVICE_UNAVAILABLE.html.var
#    ErrorDocument 506 /error/HTTP_VARIANT_ALSO_VARIES.html.var
#
#</IfModule>
#</IfModule>



then restarted apache and still 

Not Found

The requested URL /pp was not found on this server.
Apache/2.0.55 (Ubuntu) PHP/5.1.6 Server at 192.168.1.152 Port 80


any hints ??? I even restarted the server just in case :(

JCG

---

### Post by aphextwin on 2008-04-02
Check this
> 
[http://www.ducea.com/2006/06/15/apache-tips-tricks-hide-apache-software-version/](http://www.ducea.com/2006/06/15/apache-tips-tricks-hide-apache-software-version/)


---

