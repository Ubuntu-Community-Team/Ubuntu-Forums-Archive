---
title: "Evolution Mail - Error while Pinging IMAP"
date: 2008-03-10
forum: Networking &amp; Wireless
---

### Post by fk4rp6 on 2008-03-10
It seems that with the Evolution mail client everytime before automatically checking for mail it tries to ping the mail server.  This results in the error popping up stating

Error while Pinging IMAP
server mail.xxxxxxx.com
connection reset by peer

The mail client retrieves and sends mail just fine.  How do I fix it so this annoying and incorrect message so that it does not pop up anymore?

---

### Post by wchu on 2008-03-13
+1
I have the same question

---

### Post by convikt on 2008-04-24
This appears to be a time out error. Try resetting Evolution to get mail every 3 minutes or less, I collect every 1 minute. You need to click: Edit >> Preferences >> Select the email account & click edit >> Click receiving options tab.

I hope this helps.

---

### Post by mondalaci on 2008-04-24
Evolution kept popping up this annoyance so I mercilessly eradicated it using the following [Devil's Pie]("http://burtonini.com/blog/computers/devilspie") script:

```
(if (and (matches (window_name) "Evolution Error") (matches (application_name) "evolution"))
    (close)
)

```

You should save it as /home/yourhome/.devilspie/evolution-kill-ping-popup.ds and start up Devil's Pie.

---

### Post by fk4rp6 on 2008-04-30
Setting evolution to check for mail every 2 min. seemed to fix the problem.  If I have any more trouble I'll definitely try the script next.

---

