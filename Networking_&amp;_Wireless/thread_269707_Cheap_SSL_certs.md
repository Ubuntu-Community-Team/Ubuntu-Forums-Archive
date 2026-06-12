---
title: "Cheap SSL certs?"
date: 2006-10-02
forum: Networking &amp; Wireless
---

### Post by Bjoeboo on 2006-10-02
I am installing a home email server (Zimbra) mainly just for fun and learning.  But I heard that if I want to configure encrypted smtp connections to other mailservers I need an SSL cert? Verisign charges like $500 a month!!  I guess I could make my own CA and issue myself one...  But if I tryed to send mail to other people would their mail-servers trust mine?  Or just bounceback? Is this why people don't make their own mailservers?:-k

---

### Post by thingy on 2006-10-02
How about giving [cacert]("http://www.cacert.org/") a try. <-- Free SSL Certs.

If you follow their procedures and get yourself verified you can have your own domain name in the certificate.

---

### Post by NorthCoast on 2006-11-12
At the SMTP level you don't need an expensive cert.  Self signed cert is plenty good enough.  Browsers aren't doing SMTP, the servers are.  It isn't verifying who you are but simply setting up an SSL transfer and even the big name servers have certs that don't match the actual hostname.

Client access under SSL is a different story (browsers, email client etc).  But I never heard of a simple cert costing $500 month. More like ~250 per year.  If you already have one for a website and can use that hostname for the mail server then that cert can be used although the rules say one cert, one server.

But for testing you can just use a free or self signed cert and click to accept that cert one time.

---

