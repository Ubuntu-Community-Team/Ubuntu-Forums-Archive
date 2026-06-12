---
title: "need help with squidGuard times"
date: 2019-05-26
forum: Networking &amp; Wireless
---

### Post by lance bermudez on 2019-05-26
I want squidguard to allow every thing only during 6am-12pm noon but block all the other stuff in the squidguard file.

squidGuard file
```

#
# CONFIG FILE FOR SQUIDGUARD
#
# Caution: do NOT use comments inside { }
#

dbhome /var/lib/squidguard/db
logdir /var/log/squidguard

#
# TIME RULES:
# abbrev for weekdays: 
# s = sun, m = mon, t =tue, w = wed, h = thu, f = fri, a = sat

time workhours {
	weekly mtwhf 00:00-06:00 12:00-00:00 
}

#
# SOURCE ADDRESSES:
#
dest porn {
	            domainlist shallalist/porn/domains
	            domainlist shallalist/models/domains
	            urllist shallalist/porn/urls
	            urllist shallalist/models/domains
	redirect http://help.ubuntu.com/
}
dest mshopping {
domainlist leanne/shoppingdomains
domainlist shallalist/shopping/domains
urllist shallalist/shopping/urls
}
acl {
        all within workhours {
                pass all
        }
        else {
                pass    !adv !porn !momshopping all
        }
        default {
                pass    none
                redirect http://www.google.com
                }
}

```
what did I do wrong?

---

