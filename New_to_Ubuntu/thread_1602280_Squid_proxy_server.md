---
title: "Squid proxy server"
date: 2010-10-21
forum: New to Ubuntu
---

### Post by ofhi on 2010-10-21
I run webmin version 1.510 and i admit and understand that my question maybe a bit stupid, im still new..here i go: on squid proxy server, on the access control sub-menu, how do i block a user on my network from being able to access a unwanted site? or do i have to do it elsewhere on webmin? or is it not possible? please help me, i know that somebody out there knows.

Many thanks

---

### Post by SeijiSensei on 2010-10-21
I don't know how you'd do it in Webmin, but one answer to your question is to add an "ACL" to /etc/squid/squid.conf that blocks the user's IP address.  If you want to block a specific person, you'd need to add [authentication]("http://wiki.squid-cache.org/Features/Authentication") to Squid.  That would probably annoy the hell out of most users.

```
acl BADGUY src 10.10.10.27
http_access deny BADGUY
```

will block traffic from 10.10.10.27.  Make sure these appear above the default http_access rules already in squid.conf.

If all you want is to block access to a specific site, say by domain name, you can use:

```
acl BADSITE dstdom_regex -i ^example\.com$
http_access deny BADSITE
```

will block all sites in the example.com domain.  (This entry is a "[regular expression]("http://www.regular-expressions.info/")" where ^ designates the start of a string and $ the end.  The period is "escaped" with the backslash because that character has a special meaning in a regex.  This expression will match "example.com" but not "newexample.com". The "-i" switch makes the comparison case-insensitive.)

You can even create multiple rules that would block on requests for BADSITE that come from the BADGUY computer.

I've installed Squid at client sites not to implement proxy caching but to employ these controls over browsing.  For instance, we have a long list of blocked filename extensions like 

```
acl NOEXE url_regex -i \.exe$
```

which we use to limit access to remote .exe files.  We typically permit access by IT admins' computers and block everyone else.

---

### Post by ofhi on 2010-10-22
thank you so much, i really appreciate your help.


the problem i still have though, is i still can not get it working, i have googled for long and i still cannot find the solution to my problem, if there is anything else you or anyone else knows, please feel free to save my life.

thanks in advance

---

### Post by ubhi on 2010-10-22
[http://doxfer.webmin.com/Webmin/SquidProxyServer](http://doxfer.webmin.com/Webmin/SquidProxyServer)

dear,

might above link help you... 
you just login to webmin & then go to squid proxy server
create new client address list for which you want to block
then on right side of the pane click on add proxy restriction then add your client address corresponding to website to black & give him denied access

apply squid configuration by restarting it..

---

