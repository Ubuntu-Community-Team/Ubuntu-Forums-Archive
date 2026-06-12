---
title: "mail and postfix"
date: 2011-06-21
forum: New to Ubuntu
---

### Post by davidgutu on 2011-06-21
Hi, 
I am a little confused about the two terms:mail ans postfix and will be happy if someone could help me out. 
Is the mail command in ubuntu (and other unix systems) using postfix? Thanks

---

### Post by gmargo on 2011-06-21
Perhaps not exact, but generically, it's Client vs. Server
"mail" is a client, "postfix" is a server.

A "Mail User Agent" or "EMail Client" provides the user interface.
[http://en.wikipedia.org/wiki/Mail_user_agent](http://en.wikipedia.org/wiki/Mail_user_agent)
Examples of an MUA include "mail" (from the bsd-mailx package) or "mutt" or "thunderbird" or "evolution".

A "Message Transfer Agent" provides the mail send/receive server.
[http://en.wikipedia.org/wiki/Message_transfer_agent](http://en.wikipedia.org/wiki/Message_transfer_agent)
Examples of an MTA include "postfix" and "exim4".


[https://help.ubuntu.com/community/MailServer](https://help.ubuntu.com/community/MailServer)
[https://help.ubuntu.com/11.04/serverguide/C/email-services.html](https://help.ubuntu.com/11.04/serverguide/C/email-services.html)

---

### Post by davidgutu on 2011-06-21
> **gmargo said:**
> Perhaps not exact, but generically, it's Client vs. Server
"mail" is a client, "postfix" is a server.

A "Mail User Agent" or "EMail Client" provides the user interface.
[http://en.wikipedia.org/wiki/Mail_user_agent](http://en.wikipedia.org/wiki/Mail_user_agent)
Examples of an MUA include "mail" (from the bsd-mailx package) or "mutt" or "thunderbird".

A "Message Transfer Agent" provides the mail send/receive server.
[http://en.wikipedia.org/wiki/Message_transfer_agent](http://en.wikipedia.org/wiki/Message_transfer_agent)
Examples of an MTA include "postfix" and "exim4".


[https://help.ubuntu.com/community/MailServer](https://help.ubuntu.com/community/MailServer)
[https://help.ubuntu.com/11.04/serverguide/C/email-services.html](https://help.ubuntu.com/11.04/serverguide/C/email-services.html)

Thanks !!

---

