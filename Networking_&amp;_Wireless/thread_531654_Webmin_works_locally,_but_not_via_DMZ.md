---
title: "Webmin works locally, but not via DMZ?"
date: 2007-08-21
forum: Networking &amp; Wireless
---

### Post by digitallyhip on 2007-08-21
Disclaimer: I am very Windows-capable, but am totally green with Linux.

I have setup 7.04 and installed webmin. From other PCs inside the LAN, I can access Webmin by going to [https://10.0.0.139:10000](https://10.0.0.139:10000).

I have placed 10.0.0.139 in the DMZ (Linksys WRT54GL), but anyone going to [https://external](https://external) IP:10000 gets a "unable to connect" error.

Can someone smarter than me please enlighten me?

Many thanks

---

### Post by Nifty360 on 2008-06-05
I hate to dig up the past, but I am currently running into this same issue.  Was this ever resolved?  Any ideas?

Using my local network IP (192.168.1.XXX) I can log in to the default port 10000 after accepting the security certificate.  I can not log in using my IP from my ISP nor can a friend of mine.  I have scanned through the install documents and found nothing. This issue sounded like the closest thing to my problem, so I was forced to bump this.

Thank you in advance.

Nifty360

---

### Post by Nifty360 on 2008-06-05
I am sooo, sorry.  I fixed it.  I did not complete the port forward on my router.  I forgot to check the "on" box.  Man I feel stupid.  Words of wisdom, always double check your settings.

Thank you anyway.

Nifty360

---

