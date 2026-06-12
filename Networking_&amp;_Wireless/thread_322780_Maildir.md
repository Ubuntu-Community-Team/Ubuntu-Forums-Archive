---
title: "Maildir"
date: 2006-12-21
forum: Networking &amp; Wireless
---

### Post by msh_man on 2006-12-21
I'm installing a new mail server using uBuntu 6.10.
I want sitewide Maildir support on this server, so I have edited exim.conf to read:
local_delivery:
driver = appendfile
group = mail
mode = 0660
mode_fail_narrower = false
envelope_to_add = true
return_path_add = true

directory=${home}/Maildir
maildir_format = true
prefix = ""

I'm expecting to find the mail message, from the cmd: mail -s "test message" username,
in the user's directory.

The problem I have is mail is landing in: /var/mail/username.

---

