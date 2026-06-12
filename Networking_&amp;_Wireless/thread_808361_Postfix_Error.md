---
title: "Postfix Error"
date: 2008-05-26
forum: Networking &amp; Wireless
---

### Post by Black Mage on 2008-05-26
I am getting this error in postfix and I was wondering if anyone could help or know what the problem is?

The Error:
May 26 13:45:51 mainserver postfix/smtpd[6349]: fatal: bad net/mask pattern: "192.168.1.0/202"

And I have two servers on my network. The mainserver ip being 192.168.1.201 and the web server ip of 192.168.1.202

---

### Post by Mr. C. on 2008-06-03
> **Black Mage said:**
> I am getting this error in postfix and I was wondering if anyone could help or know what the problem is?

The Error:
May 26 13:45:51 mainserver postfix/smtpd[6349]: fatal: bad net/mask pattern: "192.168.1.0/202"

And I have two servers on my network. The mainserver ip being 192.168.1.201 and the web server ip of 192.168.1.202

I presume this is for your mynetworks paramenter.

/202 is not a valid network mask.  Are you trying to say from 0 to 202 ?   If so, specifying this set of networks is done with this list:

192.168.1.0/25, 192.168.1.128/26, 192.168.1.192/29, 192.168.1.200/31, 192.168.1.202/32

but I don't think that is what you want/mean.  I'm assuming you just want the entire 192.168.1.x network; then you'd use:

192.168.1.0/24

---

