---
title: "SquidGaurd non filtering on squid3"
date: 2014-04-06
forum: Networking &amp; Wireless
---

### Post by Cybergatto on 2014-04-06
Hello,

i've installed Squid3 and all works fine, so i've installed  quidguard for do the content filtering, i've downloaded the shalla  balacklist and i've modified my squidguard.conf file:

  ```
root@squid:/root/bin# cat /etc/squid/squidGuard.conf
#
# CONFIG FILE FOR SQUIDGUARD
#
# Caution: do NOT use comments inside { }
#

dbhome /var/lib/squidguard/db
logdir /var/log/squid

#
# TIME RULES:
# abbrev for weekdays:
# s = sun, m = mon, t =tue, w = wed, h = thu, f = fri, a = sat

ldapbinddn     CN=Squid Proxy,OU=Users,OU=Moncalieri,DC=******,DC=com
ldapbindpass   ****.123

ldapcachetime  300
ldapprotover 2

#src stdusers {
#     ldapusersearch  ldap://server02.******.com/CN=Proxy-Std,OU=Groups,OU=Moncalieri,DC=*********,DC=com?memberUid?sub?(&(objectclass=posixGroup)(memberUid=%s))
#  }


#src stdusers {
#     ldapusersearch ldap://server02.******.com:3268/DC=************,DC=com?sAMAccountName?sub?(&(sAMAccountName=%s)(memberOf=CN=Proxy-Std%2cOU=Groups%2cOU=Moncalieri%2cDC=****%2cDC=com))
#     ldapusersearch ldap://server02.*******.com:3268/DC=********,DC=com?userPrincipalName?sub?(&(userPrincipalName=%s)(memberOf=CN=Proxy-Std%2cOU=Groups%2cOU=Moncalieri%2cDC=*********%2cDC=com))
#  }

src stdusers {
user maol
}

src fullusers {
     ldapusersearch ldap://server02.******.com:3268/DC=**********,DC=com?sAMAccountName?sub?(&(sAMAccountName=%s)(memberOf=CN=Proxy-Full%2cOU=Groups%2cOU=Moncalieri%2cDC=*******%2cDC=com))
     ldapusersearch ldap://server02.*******.com:3268/DC=********,DC=com?userPrincipalName?sub?(&(userPrincipalName=%s)(memberOf=CN=Proxy-Full%2cOU=Groups%2cOU=Moncalieri%2cDC=*****%2cDC=com))
  }

src denyusers {
     ldapusersearch ldap://server02.***********.com:3268/DC=*******,DC=com?sAMAccountName?sub?(&(sAMAccountName=%s)(memberOf=CN=Proxy-deny%2cOU=Groups%2cOU=Moncalieri%2cDC=*******%2cDC=com))
        ldapusersearch ldap://server02.********.com:3268/DC=*********,DC=com?userPrincipalName?sub?(&(userPrincipalName=%s)(memberOf=CN=Proxy-deny%2cOU=Groups%2cOU=Moncalieri%2cDC=********%2cDC=com))
  }


time workhours {
        weekly mtwhf 08:00 - 16:30
        date *-*-01  08:00 - 16:30
}


#
# DESTINATION CLASSES:
#

dest good {
        urllist         updatesites/urls
        domainlist      updatesites/domains
}

dest locked {
        urllist         gamble/urls
        urllist         porn/urls
        urllist         remotecontrol/urls
        urllist         socialnet/urls
        urllist         spyware/urls
        domainlist      gamble/domains
        domainlist      porn/domains
        domainlist      remotecontrol/domains
        domainlist      socialnet/domains
        domainlist      spyware/domains
}

#dest adult {
#       domainlist      BL/adult/domains
#       urllist         BL/adult/urls
#       expressionlist  BL/adult/expressions
#       redirect [http://admin.foo.bar.de/cgi-bin/blocked.cgi?clientaddr=%a&clientname=%n&clientuser=%i&clientgroup=%s&targetgroup=%t&url=%u](http://admin.foo.bar.de/cgi-bin/blocked.cgi?clientaddr=%a&clientname=%n&clientuser=%i&clientgroup=%s&targetgroup=%t&url=%u)
#}

#
# ACL RULES:
#

acl {

        fullusers {
                pass       all
                redirect [http://squid.******.com/block.html](http://squid.******.com/block.html)
        }

        stdusers {
                pass      !locked all
                redirect [http://squid.*******.com/block.html](http://squid.*******.com/block.html)
        }

        denyusers {
                pass     good none
                redirect [http://squid.******.com/block.html](http://squid.******.com/block.html)
        }

        default {
                pass     good none
                redirect [http://squid.********.com/block.html](http://squid.********.com/block.html)

        }
}
  
```

as you can see for the user maol the socialnet are not allowed, but if i try to access it the request was not redirected.
  ```
root@squid:/root/bin# echo "https://www.facebook.com 192.168.0.134/ maol - GET" | squidGuard -d 10                           2014-04-06 10:31:38 [5343] New setting: dbhome: /var/lib/squidguard/db
2014-04-06 10:31:38 [5343] New setting: logdir: /var/log/squid
2014-04-06 10:31:38 [5343] New setting: ldapbinddn: CN=Squid Proxy,OU=Users,OU=Moncalieri,DC=**********,DC=com
2014-04-06 10:31:38 [5343] New setting: ldapbindpass: ******.123
2014-04-06 10:31:38 [5343] New setting: ldapcachetime: 300
2014-04-06 10:31:38 [5343] New setting: ldapprotover: 2
2014-04-06 10:31:38 [5343] Added User: maol
2014-04-06 10:31:38 [5343] init urllist /var/lib/squidguard/db/updatesites/urls
2014-04-06 10:31:38 [5343] loading dbfile /var/lib/squidguard/db/updatesites/urls.db
2014-04-06 10:31:38 [5343] init domainlist /var/lib/squidguard/db/updatesites/domains
2014-04-06 10:31:38 [5343] loading dbfile /var/lib/squidguard/db/updatesites/domains.db
2014-04-06 10:31:38 [5343] init urllist /var/lib/squidguard/db/gamble/urls
2014-04-06 10:31:38 [5343] loading dbfile /var/lib/squidguard/db/gamble/urls.db
2014-04-06 10:31:38 [5343] init urllist /var/lib/squidguard/db/porn/urls
2014-04-06 10:31:38 [5343] loading dbfile /var/lib/squidguard/db/porn/urls.db
2014-04-06 10:31:38 [5343] init urllist /var/lib/squidguard/db/remotecontrol/urls
2014-04-06 10:31:38 [5343] loading dbfile /var/lib/squidguard/db/remotecontrol/urls.db
2014-04-06 10:31:38 [5343] init urllist /var/lib/squidguard/db/socialnet/urls
2014-04-06 10:31:38 [5343] loading dbfile /var/lib/squidguard/db/socialnet/urls.db
2014-04-06 10:31:38 [5343] init urllist /var/lib/squidguard/db/spyware/urls
2014-04-06 10:31:38 [5343] loading dbfile /var/lib/squidguard/db/spyware/urls.db
2014-04-06 10:31:38 [5343] init domainlist /var/lib/squidguard/db/gamble/domains
2014-04-06 10:31:38 [5343] loading dbfile /var/lib/squidguard/db/gamble/domains.db
2014-04-06 10:31:38 [5343] init domainlist /var/lib/squidguard/db/porn/domains
2014-04-06 10:31:38 [5343] loading dbfile /var/lib/squidguard/db/porn/domains.db
2014-04-06 10:31:38 [5343] init domainlist /var/lib/squidguard/db/remotecontrol/domains
2014-04-06 10:31:38 [5343] loading dbfile /var/lib/squidguard/db/remotecontrol/domains.db
2014-04-06 10:31:38 [5343] init domainlist /var/lib/squidguard/db/socialnet/domains
2014-04-06 10:31:38 [5343] loading dbfile /var/lib/squidguard/db/socialnet/domains.db
2014-04-06 10:31:38 [5343] init domainlist /var/lib/squidguard/db/spyware/domains
2014-04-06 10:31:38 [5343] loading dbfile /var/lib/squidguard/db/spyware/domains.db
2014-04-06 10:31:38 [5343] squidGuard 1.4 started (1396773098.335)
2014-04-06 10:31:38 [5343] Info: recalculating alarm in 21502 seconds
2014-04-06 10:31:38 [5343] squidGuard ready for requests (1396773098.338)

2014-04-06 10:31:38 [5343] squidGuard stopped (1396773098.338)
```

---

