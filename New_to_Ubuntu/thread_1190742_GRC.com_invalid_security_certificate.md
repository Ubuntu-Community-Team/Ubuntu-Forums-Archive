---
title: "GRC.com invalid security certificate?"
date: 2009-06-18
forum: New to Ubuntu
---

### Post by r3cht3r on 2009-06-18
> Secure Connection Failed

[www.grc.com]("http://www.grc.com") uses an invalid security certificate.

The certificate expired on 06/17/2009 03:59 PM.

Error code: sec_error_expired_certificate)

   * This could be a problem with the server's configuration, or it could be someone trying to impersonate the server.

   * If you have connected to this server successfully in the past, the error may be temporary, and you can try again later.

Or you can add an exception...What seem to be the problem? Is this on the site's server or on my box? 

EDIT. I can connect fine through [www.grc.com/intro.htm](www.grc.com/intro.htm) but when I tried using ShieldsUp this error comes up. When a security certificate expires, does it invalidates the whole site (or you cannot browse anymore) or just a portion of it? coz it seems that's what's happening to me.

I have connected to this server successfully in the past, in fact, just about 2-3 days ago and it was fine and it checked out right.

---

### Post by Trebaruna on 2009-06-18
The error message explains it all. The site has a security certificate that expired. It's their fault. They need to go and install a new certificate. Email them about it or wait until they do so.

EDIT. The reason you could connect in the past is that the certificate only expired yesterday. Before that it was perfectly valid and you could connect without a hitch. Now, however, it's not worth anything anymore.

---

### Post by LewRockwell on 2009-06-18
Yes, you can either add an exception(potentially dangerous in the long-term) or you can attempt to contact Steve Gibson regarding this issue.

Unless something has happened to Steve, I would say he already knows about this issue and is attempting to resolve it quickly as his website has tens of thousands of visits per day.

Oh, and if you do send correspondence...please don't expect a personal reply as Steve is unable, timewise, to do that.

---

### Post by kwacka on 2009-06-18
Seems to have an updated certificate now - no error message at least.

---

