---
title: "Squid Proxy Acess list"
date: 2010-10-24
forum: New to Ubuntu
---

### Post by lovelyvik293 on 2010-10-24
I am trying to create a Squid proxy server on Ubuntu. I installed the Squid3 and it's working fine. Now when i want to restrict the access to some sites i add the following lines in acl and http_access part of squid.conf

```

#acl part
acl BadSites  dstdomain "/usr/local/etc/restricted-sites.squid"

#http_access part
http_access deny BadSites

```
and i created /usr/local/etc/restricted-sites.squid this file with following entries:
```

www.google.com
www.facebook.com

```

But it is not working fine i can still open these sites.

How can i sort out this problem?

---

### Post by The Real Dave on 2010-10-24
Have you tried telling Squid to reconfigure?

```
sudo /etc/init.d/squid3 -k reconfigure
```


If that doesn't do it, restart Squid with 

```
sudo /etc/init.d/squid3 restart
```

And if that doesn't work, try listing the sites in squid.conf, rather than pointing to an external file?

```
#acl part
acl BadSites dstdomain www.google.com
acl BadSites dstdomain www.facebook.com

#http_access part
http_access deny BadSites
```

You also had a double space between BadSites and dstdomain, perhaps Squid is fussy.

---

### Post by Gone fishing on 2010-10-24
I'm using squid 2.7 so I hope this helps.

Firstly I used webmin to set most of it up including the ACLs this makes it very easy. I also use squidguard which was OK to setup webmin didn't help much with that.

In my squid.cont I have this section

```
# And finally deny all other access to this proxy
http_access deny abuse
http_access allow nofilter
http_access allow allow_intra
http_access deny nosex
http_access deny time
http_access deny time1
http_access deny no_mail
http_access allow allowlocal
http_access allow localhost
http_access allow manager localhost
http_access deny manager
http_access deny !Safe_ports
http_access deny all
```

and
an ACL section with for example

```
acl nosex dstdomain 123singles123.com addictinggames.com
```(this is much  longer!) Note this is in the squid.conf

However, squidguard is better for blocking than any ACL you or I can think up.

---

### Post by lovelyvik293 on 2010-10-26
Thanks everyone.

---

