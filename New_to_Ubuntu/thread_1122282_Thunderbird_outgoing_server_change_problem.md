---
title: "Thunderbird outgoing server change problem"
date: 2009-04-10
forum: New to Ubuntu
---

### Post by David Oxland on 2009-04-10
When trying to add a new outgoing server setting in Thunderbird and then choosing it as a default I find that Thunderbird won't use that new setting.  The only way that I can get it to happen is to delete the  now unneeded server. I had expected to have a list of outgoing servers and to have only one set as default and have them changeable as necessary when moving laptop from location to location.
Is there something that I'm missing here?
  This has happened a couple of times in the last year whenever a change was necessary and the only way to make it work was to delete the non default server.
Thanks for any hints








Using Ubuntu Thunderbird version 2.0.0.21 (20090318)

---

### Post by aaronp on 2009-04-13
I don't think you need to delete the old SMTP server but when you create a new SMTP server, it would seem that all incoming accounts you create still want to use the old one.
I believe you need to change it at the individual mail account level to use the desired SMTP server, otherwise each account will receive mail via it's own specified server but will just send mail via the default SMTP server.

Aaron

---

