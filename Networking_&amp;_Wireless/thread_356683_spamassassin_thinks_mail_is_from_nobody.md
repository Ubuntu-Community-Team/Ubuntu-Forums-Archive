---
title: "spamassassin thinks mail is from nobody"
date: 2007-02-08
forum: Networking &amp; Wireless
---

### Post by Cowloon on 2007-02-08
I have spamassassin magicly being run by exim4. In mail.log I got a lot of messages like:

Feb  8 14:36:00 pokey spamd[4863]: spamd: connection from localhost [127.0.0.1] at port 49573
Feb  8 14:36:00 pokey spamd[4863]: spamd: setuid to nobody succeeded
Feb  8 14:36:00 pokey spamd[4863]: spamd: creating default_prefs: /nonexistent/.spamassassin/user_prefs
Feb  8 14:36:00 pokey spamd[4863]: mkdir /nonexistent: Permission denied at /usr/share/perl5/Mail/SpamAssassin.pm line 1491
Feb  8 14:36:01 pokey spamd[4863]: config: cannot write to /nonexistent/.spamassassin/user_prefs: No such file or directory
Feb  8 14:36:01 pokey spamd[4863]: spamd: failed to create readable default_prefs: /nonexistent/.spamassassin/user_prefs

The email I'm getting seems to be to me though, not to nobody. Do you have any idea what's going on?

---

### Post by Cowloon on 2007-02-09
This appears to be a solution:

[http://www.debianhelp.org/node/3765](http://www.debianhelp.org/node/3765)

I added -x -D and --virtual-config-dir so it doesn't try to look in ~nobody/.spamassassin.

---

