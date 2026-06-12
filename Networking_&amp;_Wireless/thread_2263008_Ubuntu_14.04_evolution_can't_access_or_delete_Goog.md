---
title: "Ubuntu 14.04: evolution: can't access or delete Google Calendar"
date: 2015-01-28
forum: Networking &amp; Wireless
---

### Post by temmokan on 2015-01-28
Given: Ubuntu 14.04 upgraded from 12.04 (64-bit).

When I start Evolution, I see calndar for Google Apps email (hereinafter [email]user@example.com[/email]). There's no such account in Online Accounts; the following
- restarting Evolution
- removing Evolution config files from current user's home dirctories
- removing/reinstalling Evolution
- adding/removing online account [email]user@example.com[/email]
- adding/revoking online account [email]user@example.com[/email]'s access for Evolution

mixed in any combination do not result in anything useful. I still see the mentioned calendar in calendars list and see the following error message every time Evolution starts:

> Error loading calendar 'Calendar (user@example.com)'

Unable to connect to 'Calendar': Failed to obtain an access token for 'Calendar': GDBus.Error:org.gnome.OnlineAccounts.Error.NotAuthorized: No credentials found in the keyring

Also, the following seems appearing repeatedly in /var/log/syslog

signond: ../../../../src/signond/signondaemon.cpp 388 init Failed to SUID root. Secure storage will not be available.

I would appreciate any useful piece of advise on that. It's really annoying.

---

### Post by temmokan on 2015-01-29
Not a single idea, folks?

I did searching on this forum an on the Net, prior to asking. Nothing mentioned helps.

---

### Post by St.Lukas on 2015-08-21
This happened to me due to removing my credentials from gnome-keyring. Evolution is not able to access the calendar as it is bound to mail because it can't access credentials in keyring. Therefore, it is not manageable. Adding again, credentials to gnome-keyring will fix this issue. You can do this manually by the seahorse. Or in evolution by Edit->Preferences -> Mail Accounts and sign again to your mail account (calendar).

---

