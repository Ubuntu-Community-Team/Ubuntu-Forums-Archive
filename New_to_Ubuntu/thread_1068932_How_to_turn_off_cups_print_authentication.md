---
title: "How to turn off cups print authentication?"
date: 2009-02-13
forum: New to Ubuntu
---

### Post by bhold on 2009-02-13
I have a Win/XP system with HP4200 printer. I use it to print remotely from my Ubuntu 8.10 desktop system over my small office network.

Can someone please tell me how to turn off cups print authentication - forever and permanently???

For a while I could do this by tweaking the /etc/cups/printers.conf file. But this no longer works - the file continues to get over-written every day or two and authentication gets re-enabled.  cups version is 1.3.9-2

---

### Post by bhold on 2009-02-18
In file /etc/cups/cupsd.conf

changed DefaultAuthType to none.

changed AuthType to none in the printer operations block.

Then re-started /usr/sbin/cupsd

This seems to have shut off the annoying authentication prompts - for now anyway and I hope this will persist as new cups updates roll out.

---

