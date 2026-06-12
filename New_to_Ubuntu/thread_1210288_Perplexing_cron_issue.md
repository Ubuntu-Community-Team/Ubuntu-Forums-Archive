---
title: "Perplexing cron issue"
date: 2009-07-11
forum: New to Ubuntu
---

### Post by criticalbill on 2009-07-11
Hi all. I have the following script

=============================
/bin/cat <file> | /home/me/script.pl | /usr/bin/mail [email]me@me.com[/email] -s "My Report"
=============================

script.pl does some basic processing of <file>. Nothing fancy. All output is in text.

If I run the command above by hand I get an e-mail and the body contains my text data.

If I add the script to cron (crontab -e), it runs but my e-mail contains an empty body...no text data. I've been scratching my head for a couple of days.

Can anyone provide some troubleshooting guidance?

---

