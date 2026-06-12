---
title: "Vanilla Postfix Installation (hopefully *without* authentication)...?"
date: 2008-06-24
forum: Networking &amp; Wireless
---

### Post by michwill on 2008-06-24
Hi All,

Having an issue with my new Postfix installation.  Basically I need a vanilla setup with no authentication, etc.  I just want it to pass the email on and let that be.  It currently keeps rejecting me with a message saying that each attempt is coming from an "unknown host".

How exactly do I resolve this?

I need this because I have a client that has a ServiceCEO installation that has hosed up SMTP on his windows box, so he needs to reroute SMTP traffic to something local in the meantime.  I suggested he use his hosting company, however, ServiceCEO requires port 25 and makes no adjustments available -- and, of course, many hosting companies change port 25 to something else.

If it's simply a Postfix authentication issue, then I'd appreciate something less convoluted than "https://help.ubuntu.com/community/Postfix" to take care of it as I'll need to guide him through it over the phone as he performs the tasks.

Anyway, any help is appreciated.

Regards!

---

### Post by michwill on 2008-07-05
I've found this ([https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix)), but it pretty much assumes you want Authentication, which I don't.  As I've stated, I have an internal machine that needs to connect to a mail server on port 25 without authentication, and rather than set one up offsite somewhere, I figured we'd simply set up a "dummy" POSTFIX box locally.

Thoughts?

---

