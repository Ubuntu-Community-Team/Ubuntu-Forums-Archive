---
title: "Zimbra DNS ERROR - none of the MX records"
date: 2008-07-09
forum: Networking &amp; Wireless
---

### Post by reyhan on 2008-07-09
When i want to Install zimbra why is I've 
got this messages? 

```
Operations logged to /tmp/zmsetup.01001900-0000139008780.log
Setting defaults...	MX: mx.reyhan.org (207.7.108.212)

	Interface: 192.168.2.200
	Interface: 127.0.0.1
		207.7.108.212
		207.7.108.212


DNS ERROR - none of the MX records for reyhan.homedns.org
resolve to this host
Change domain name? [Yes] 
```

Can someone Help me?

---

### Post by fivosz on 2008-12-14
Same here.
Anyone?

---

### Post by Bronto on 2008-12-14
[http://ubuntuforums.org/showthread.php?t=643727](http://ubuntuforums.org/showthread.php?t=643727)

---

### Post by joebeasley on 2008-12-17
Zimbra is doing a DNS lookup for the MX record of reyhan.org, which resolves to 207.7.108.212.  The IP address on your server is 192.168.2.200.  That is why you get the error. 

You will have to setup a dns server so that you can use the 192.168.2.200 addresses.

---

### Post by nagileon on 2010-05-18
Check this out: [http://zimbramta.blogspot.com](http://zimbramta.blogspot.com)

---

