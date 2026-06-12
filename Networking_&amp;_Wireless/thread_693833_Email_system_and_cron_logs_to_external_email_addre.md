---
title: "Email system and cron logs to external email address"
date: 2008-02-11
forum: Networking &amp; Wireless
---

### Post by louish on 2008-02-11
Hello all.

I can't seem to find the place to configure email settings for log or cron jobs.   I would like to "re-direct" those logs to an external email address.   How can I go about this?

Regards

Louis

---

### Post by louish on 2008-02-11
Another thing,

On my old fedora box, I had been able to (from the command line) send a quick (test) email to an external address.   I can bring mail up, and type a message, but I can't seem to quit to send it.  I've tried ctrl/D and esc, or just a "." on a blank line.  But nothing seems to work.   Any ideas?

Regards,
Louis

---

### Post by ruy_lopez on 2008-02-11
You can pipe the message to mail like this:

```
cat message.txt | mail -s "subject" someone@someaddress.com
```

If you have a gmail account, you can use it as a relay, using the instructions [here]("http://souptonuts.sourceforge.net/postfix_tutorial.html").

---

