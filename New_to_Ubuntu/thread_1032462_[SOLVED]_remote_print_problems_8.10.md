---
title: "[SOLVED] remote print problems 8.10"
date: 2009-01-06
forum: New to Ubuntu
---

### Post by bhold on 2009-01-06
From Ubuntu Desktop 8.10, remote print to HP Officejet on XP system fails. Message in /var/log/cups/error_log says
E [06/Jan/2009:09:00:16 -0800] Print-Job: Unauthorized

From Ubuntu Desktop 8.04, the same remote print operation works fine. 

I noticed cups version went from 1.3.7 in 8.04 to 1.3.9 in 8.10 but I don't know that this is relevant. Any ideas?

-------------------

I found a workaround. In /etc/cups/printers.conf on the 8.10 system - commented out the AuthInfoRequired line, it now looks like:
# AuthInfoRequired username,password

On my 8.04 system, the printers.conf file does not contain this entry.

Not much of an in depth answer, but it works so I will close this as "solved".

---

