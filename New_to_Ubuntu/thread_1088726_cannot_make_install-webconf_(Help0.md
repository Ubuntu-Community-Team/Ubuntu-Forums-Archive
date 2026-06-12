---
title: "cannot make install-webconf (Help0"
date: 2009-03-06
forum: New to Ubuntu
---

### Post by sunnywavez on 2009-03-06
I am trying to install, webconf, but below is the error.
make install-webconf
/usr/bin/install -c -m 644 sample-config/httpd.conf /etc/httpd/conf.d/nagios.conf
/usr/bin/install: cannot create regular file `/etc/httpd/conf.d/nagios.conf': No such file or directory
make: *** [install-webconf] Error 1

Please help to solve this problem, my apache2 is installed in default location "/usr/loca/apache2", and the httpd.conf is in directory "/usr/local/apache2/conf"

Can any one provide alternative steb by step installation. Please do help... !!

Best Regards,
Sundar

---

### Post by sunnywavez on 2009-03-06
There is one solution posted in one of the Forum Site, but it is chinese linux forum, but please developers, you can interpret the codes given, can anybody explain how to use it!!!!???

&#21518;&#26469;&#26597;&#30475;Makefile&#21518;&#21457;&#29616;&#26159;&#33050;&#26412;&#37324;&#38754;&#30340;&#19968;&#20010;
$(INSTALL) -m 644 sample-config/httpd.conf $(DESTDIR)$(HTTPD_CONF)/nagio
s.conf&#20013;$(DESTDIR)$(HTTPD_CONF)&#21464;&#37327;&#38169;&#35823;&#12290;
&#25152;&#20197;&#25105;&#23601;&#27809;&#31649;&#36825;&#19968;&#27493;&#39588;&#65292;&#30452;&#25509;&#25163;&#21160;&#25191;&#34892;&#20102;&#19968;&#36941;&#21629;&#20196;&#12290;

/usr/bin/install -c -m 644 sample-config/httpd.conf /usr/local/apache2/conf/conf.d/nagios.conf
&#28982;&#21518;&#20462;&#25913;apache&#30340;httpd.conf&#25991;&#20214;&#12290;&#22312;&#26368;&#21518;&#38754;&#28155;&#21152;&#19968;&#26465;&#65306;

Include conf/conf.d/*.conf 


this is wat was posted.

---

