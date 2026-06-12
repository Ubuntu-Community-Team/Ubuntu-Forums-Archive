---
title: "Pidgin - Unable to authenticate: Unable to connect"
date: 2009-08-10
forum: New to Ubuntu
---

### Post by AlistairH on 2009-08-10
Recently, I've started getting this message in pidgin when trying to connect to my msn account.

> Unable to authenticate: Unable to connect

Pidgin will not attempt to reconnect the account until you correct the error and re-enable the account.

I can connect using aMSN but I'd rather use Pidgin. I've removed and reinstalled it, but to no avail.

Any suggestions?

---

### Post by Tibuda on 2009-08-10
I would try to [update Pidgin]("http://www.pidgin.im/download/ubuntu/") or to install the [alternate WLM protocol for Pidgin]("apt:msn-pecan").

---

### Post by colau on 2009-08-15
> **AlistairH said:**
> Recently, I've started getting this message in pidgin when trying to connect to my msn account.



I can connect using aMSN but I'd rather use Pidgin. I've removed and reinstalled it, but to no avail.

Any suggestions?
Is your problem solved?

---

### Post by starbityop on 2010-11-19
try this

[http://blog.andreineculau.com/2010/11/pidgin-and-msn-certificate-error-for-omega-contacts-msn-com/](http://blog.andreineculau.com/2010/11/pidgin-and-msn-certificate-error-for-omega-contacts-msn-com/)

---

### Post by spillage2 on 2010-11-19
make sure you untick the http connection in preferences

---

### Post by KIAaze on 2011-02-09
Pidgin - Unable to authenticate: Unable to connect
but no certificate error!

I had the same problem recently and it was in fact because I had the wrong credentials.
The reason I didn't notice it is because I used [https://login.live-INT.com](https://login.live-INT.com) to reset my password (I suppose MSN stopped working because I had selected the automatic password reset after 72 days) instead of [https://login.live.com](https://login.live.com)
So I was convinced I had the right credentials since they worked on [https://login.live-INT.com](https://login.live-INT.com), while those are actually not the MSN credentials. Both websites looking pretty much the same, it wasn't obvious at all.

> The Windows Live ID INT environment is separate from the main Production environment, and is for testing purposes only. If you have not already created a Windows Live ID user account for testing in INT, you can do so at [https://login.live-INT.com/](https://login.live-INT.com/)

source: [http://winliveid.spaces.live.com/?_c11_BlogPart_BlogPart=blogview&_c=BlogPart&partqs=amonth%3d10%26ayear%3d2008](http://winliveid.spaces.live.com/?_c11_BlogPart_BlogPart=blogview&_c=BlogPart&partqs=amonth%3d10%26ayear%3d2008)

Just in case someone else is having the same issues. ;)

---

