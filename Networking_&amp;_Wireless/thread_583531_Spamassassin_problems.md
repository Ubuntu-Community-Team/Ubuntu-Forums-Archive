---
title: "Spamassassin problems"
date: 2007-10-20
forum: Networking &amp; Wireless
---

### Post by zx80user on 2007-10-20
I have upgrade my mail server (for historical reasons running the desktop distro) to 7.10 and in doing so rejected the chance to change my customised spamassassin config files.

Now the basic daemon is running but it is not using Bayesian filtering:

Oct 20 18:35:49 newgolddream spamd[19503]: spamd: setuid to root succeeded 
Oct 20 18:35:49 newgolddream spamd[19503]: spamd: still running as root: user not specified with -u, not found, or set to root, falling back to nobody 
Oct 20 18:35:49 newgolddream spamd[19503]: bayes: cannot open bayes databases /root/.spamassassin/bayes_* R/O: tie failed: Permission denied 
Oct 20 18:35:49 newgolddream spamd[19503]: spamd: processing message (unknown) for root:65534 
Oct 20 18:35:49 newgolddream spamd[19503]: bayes: cannot open bayes databases /root/.spamassassin/bayes_* R/O: tie failed: Permission denied 
Oct 20 18:35:55 newgolddream spamd[19503]: pyzor: check failed: internal error 
Oct 20 18:36:10 newgolddream spamd[19503]: auto-whitelist: open of auto-whitelist file failed: locker: safe_lock: cannot create tmp lockfile /nonexistent/.spamassassin/auto-whitelist.lock.dragoneye.19503 for /nonexistent/.spamassassin/auto-whitelist.lock: No such file or directory 
Oct 20 18:36:10 newgolddream spamd[19503]: bayes: cannot open bayes databases /root/.spamassassin/bayes_* R/W: tie failed: Permission denied 

Any clues as to where to begin to fix this, or is there a way to reaccept the alterations being proposed?

---

### Post by zx80user on 2007-10-20
OK, did some more digging and fixed this myself...

altered the spamassassin file in /etc/init.d so that it ran with a -u <user> option, and copied the files (and chgrped etc) from /root/.spamassassin to /<user>/.spamassassin

The user you pick needs to be able to run a shell (though doesn't have to be able to login) - if you want to run sa-learn on the spams that got away.

---

