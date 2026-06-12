---
title: "ubuntu1804 squidguard not blocking"
date: 2019-02-03
forum: Networking &amp; Wireless
---

### Post by lance bermudez on 2019-02-03
I seem to have done something wrong. SquidGuard is not blocking porn. I have the browser set for ipaddress port 3128 of the computer that has squid and squidguard on it.

/var/lib/squidguard/db
```

tardis:/var/lib/squidguard/db# ls -al
total 20
drwxr-xr-x  5 proxy proxy 4096 Feb  1 12:31 .
drwxr-xr-x  3 root  root  4096 Dec 13  2017 ..
drwxr-xr-x 60 proxy proxy 4096 Feb  1 12:31 frblacklists
drwxr-xr-x 16 proxy proxy 4096 Feb  1 12:30 mesdblacklists
drwxr-xr-x 57 proxy proxy 4096 Jan  6  2017 shallalist

```

did tardis:/var/lib/squidguard/db# sudo -u proxy squidGuard -b -d -C all
/etc/squidguard/squidGuard.conf
```

#
# CONFIG FILE FOR SQUIDGUARD
#
# Caution: do NOT use comments inside { }
#

dbhome /var/lib/squidguard/db
logdir /var/log/squidguard

dest adv {
domainlist shallalist/adv/domains
domainlist mesdblacklists/ads/domains
domainlist frblacklists/publicite/domains
domainlist shallalist/dating/domains
domainlist frblacklists/dating/domains
urllist shallalist/adv/urls
urllist mesdblacklists/ads/urls
urllist frblacklists/publicite/urls
urllist shallalist/dating/urls
urllist frblacklists/dating/urls
expressionlist frblacklists/publicite/expressions
}

dest malware {
domainlist frblacklists/malware/domains
domainlist frblacklists/phishing/domains
urllist frblacklists/malware/urls
urllist frblacklists/phishing/urls
expressionlist frblacklists/malware/expressions
}

dest porn {
	            domainlist shallalist/porn/domains
	            domainlist mesdblacklists/porn/domains
	            domainlist frblacklists/adult/domains
	            domainlist frblacklists/lingerie/domains
	            domainlist shallalist/models/domains
	            domainlist frblacklists/mixed_adult/domains
	            urllist shallalist/porn/urls
	            urllist mesdblacklists/porn/urls
	            urllist frblacklists/adult/urls
	            urllist frblacklists/lingerie/urls
	            urllist shallalist/models/domains
	            urllist frblacklists/mixed_adult/urls
	            expressionlist frblacklists/adult/expressions
	            expressionlist frblacklists/adult/very_restrictive_expression
#	redirect http://help.ubuntu.com/
}

dest redirector {
domainlist shallalist/redirector/domains
domainlist mesdblacklists/redirector/domains
domainlist frblacklists/redirector/domains
urllist shallalist/redirector/urls
urllist mesdblacklists/redirector/urls
urllist frblacklists/redirector/urls
}

dest sex {
domainlist shallalist/sex/education/domains
domainlist shallalist/sex/lingerie/domains
domainlist frblacklists/sexual_education/domains
urllist shallalist/sex/education/urls
urllist shallalist/sex/lingerie/urls
urllist frblacklists/sexual_education/urls
}

dest spyware {
domainlist shallalist/spyware/domains
domainlist mesdblacklists/spyware/domains
urllist shallalist/spyware/urls
urllist mesdblacklists/spyware/urls
}

dest tracker {
domainlist shallalist/tracker/domains
urllist shallalist/tracker/urls
}

acl {
        default {
                        pass !porn all
                        redirect http://www.google.com
        }
}

```

have attached squid config file[ATTACH]282398[/ATTACH]

---

